```yml
AWSTemplateFormatVersion: 2010-09-09
Description: 'AWS TechU - Highly Available Web Applications: Scaling in AWS (Linux)'
Parameters:
  VPCCIDR:
    Description: CIDR Block for VPC
    Type: String
    Default: 10.0.0.0/16
    AllowedValues:
      - 10.0.0.0/16
  PublicSubnet1Param:
    Description: Public Subnet 1
    Type: String
    Default: 10.0.1.0/24
    AllowedValues:
      - 10.0.1.0/24
  PrivateSubnet1Param:
    Description: Private Subnet 1
    Type: String
    Default: 10.0.2.0/24
    AllowedValues:
      - 10.0.2.0/24
  PublicSubnet2Param:
    Description: Public Subnet 2
    Type: String
    Default: 10.0.3.0/24
    AllowedValues:
      - 10.0.3.0/24
  PrivateSubnet2Param:
    Description: Private Subnet 2
    Type: String
    Default: 10.0.4.0/24
    AllowedValues:
      - 10.0.4.0/24
  KeyName:
    Type: 'AWS::EC2::KeyPair::KeyName'
  #####
  LatestAMZN2AmiId:
    Type: 'AWS::SSM::Parameter::Value<AWS::EC2::Image::Id>'
    Default: '/aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2'

  RoleName:
    Description: Enter the service linked role name.
    Type: String
    Default: AWSServiceRoleForAutoScaling

  ServiceName:
    Description: Choose a service to create a service linked role.
    Type: String
    Default: autoscaling.amazonaws.com

  #####

Resources:
  VPC:
    Type: 'AWS::EC2::VPC'
    Properties:
      CidrBlock: !Ref VPCCIDR
      EnableDnsSupport: true
      EnableDnsHostnames: true
      Tags:
        - Key: Name
          Value: Lab VPC
  InternetGateway:
    Type: 'AWS::EC2::InternetGateway'
    DependsOn: VPC
  AttachGateway:
    Type: 'AWS::EC2::VPCGatewayAttachment'
    DependsOn:
      - VPC
      - InternetGateway
    Properties:
      VpcId: !Ref VPC
      InternetGatewayId: !Ref InternetGateway
  PublicSubnet1:
    Type: 'AWS::EC2::Subnet'
    DependsOn: AttachGateway
    Properties:
      VpcId: !Ref VPC
      CidrBlock: !Ref PublicSubnet1Param
      MapPublicIpOnLaunch: true
      AvailabilityZone: !Select
        - '0'
        - !GetAZs ''
      Tags:
        - Key: Name
          Value: Public Subnet 1
  PublicSubnet2:
    Type: 'AWS::EC2::Subnet'
    DependsOn: AttachGateway
    Properties:
      VpcId: !Ref VPC
      CidrBlock: !Ref PublicSubnet2Param
      MapPublicIpOnLaunch: true
      AvailabilityZone: !Select
        - '1'
        - !GetAZs ''
      Tags:
        - Key: Name
          Value: Public Subnet 2
  PrivateSubnet1:
    Type: 'AWS::EC2::Subnet'
    DependsOn: AttachGateway
    Properties:
      VpcId: !Ref VPC
      CidrBlock: !Ref PrivateSubnet1Param
      AvailabilityZone: !Select
        - '0'
        - !GetAZs ''
      Tags:
        - Key: Name
          Value: Private Subnet 1
  PrivateSubnet2:
    Type: 'AWS::EC2::Subnet'
    DependsOn: AttachGateway
    Properties:
      VpcId: !Ref VPC
      CidrBlock: !Ref PrivateSubnet2Param
      AvailabilityZone: !Select
        - '1'
        - !GetAZs ''
      Tags:
        - Key: Name
          Value: Private Subnet 2
  PublicRouteTable:
    Type: 'AWS::EC2::RouteTable'
    DependsOn:
      - VPC
      - AttachGateway
    Properties:
      VpcId: !Ref VPC
      Tags:
        - Key: Name
          Value: Public
  PublicRoute:
    Type: 'AWS::EC2::Route'
    DependsOn:
      - PublicRouteTable
      - AttachGateway
    Properties:
      RouteTableId: !Ref PublicRouteTable
      DestinationCidrBlock: 0.0.0.0/0
      GatewayId: !Ref InternetGateway
  PublicSubnet1RouteTableAssociation:
    Type: 'AWS::EC2::SubnetRouteTableAssociation'
    DependsOn:
      - PublicRouteTable
      - PublicSubnet1
      - AttachGateway
    Properties:
      SubnetId: !Ref PublicSubnet1
      RouteTableId: !Ref PublicRouteTable
  PublicSubnet2RouteTableAssociation:
    Type: 'AWS::EC2::SubnetRouteTableAssociation'
    DependsOn:
      - PublicRouteTable
      - PublicSubnet2
      - AttachGateway
    Properties:
      SubnetId: !Ref PublicSubnet2
      RouteTableId: !Ref PublicRouteTable
  PrivateRouteTable:
    Type: 'AWS::EC2::RouteTable'
    DependsOn: AttachGateway
    Properties:
      VpcId: !Ref VPC
      Tags:
        - Key: Name
          Value: Private
  PrivateSubnet1RouteTableAssociation:
    Type: 'AWS::EC2::SubnetRouteTableAssociation'
    DependsOn:
      - PublicRouteTable
      - PrivateSubnet1
      - AttachGateway
    Properties:
      SubnetId: !Ref PrivateSubnet1
      RouteTableId: !Ref PrivateRouteTable
  PrivateSubnet2RouteTableAssociation:
    Type: 'AWS::EC2::SubnetRouteTableAssociation'
    DependsOn:
      - PublicRouteTable
      - PrivateSubnet2
      - AttachGateway
    Properties:
      SubnetId: !Ref PrivateSubnet2
      RouteTableId: !Ref PrivateRouteTable
  PrivateNetworkAcl:
    Type: 'AWS::EC2::NetworkAcl'
    DependsOn: AttachGateway
    Properties:
      VpcId: !Ref VPC
      Tags:
        - Key: Network
          Value: Private


  LambdaSLRRole:
    Type: AWS::IAM::Role
    Properties:
      AssumeRolePolicyDocument:
        Version: '2012-10-17'
        Statement:
          - Effect: Allow
            Principal:
              Service: lambda.amazonaws.com
            Action: sts:AssumeRole
      Path: "/"
      Policies:
        - PolicyName: createservicerole
          PolicyDocument:
            Version: '2012-10-17'
            Statement:
              - Effect: Allow
                Action:
                - logs:CreateLogGroup
                - logs:CreateLogStream
                - logs:PutLogEvents
                Resource: arn:aws:logs:*:*:*
              - Effect: Allow
                Action:
                  - iam:CreateServiceLinkedRole
                  - iam:UpdateServiceLinkedRole
                  - iam:DeleteServiceLinkedRole
                  - iam:AttachRolePolicy
                  - iam:ListRoles
                  - events:PutRule
                  - events:DeleteRule
                  - events:PutTargets
                  - events:RemoveTargets
                  - lambda:AddPermission
                  - lambda:RemovePermission
                Resource: '*'

  CreateServiceLinkedRole:
    Type: AWS::Lambda::Function
    DependsOn:
    - LambdaSLRRole
    Properties:
      FunctionName: CreateServiceLinkedRole
      Description: Create a service linked role if absent.
      Handler: index.handler
      MemorySize: 128
      Role: !GetAtt LambdaSLRRole.Arn
      Runtime: "python3.11"
      Timeout: 50
      Code:
        ZipFile: |
          """
          This application creates a service
          linked role if it is missing.
          """
          import boto3
          import cfnresponse
          import json
          import logging
          import traceback

          # Define logging information
          logger = logging.getLogger(__name__)
          logger.setLevel(logging.INFO)

          def handler(event, context):
              logger.info(f"Event: {json.dumps(event)}")
              logger.info(f"Context: {str(dir(context))}")
              operation = event['RequestType']
              physical_id = None
              data = { }
              try:
                  role_check = event['ResourceProperties']['CheckRoleName']
                  aws_service_info = event['ResourceProperties']['AWSServiceInfo']
                  if operation == 'Create':
                      client = boto3.client('iam')
                      response = client.list_roles(PathPrefix='/aws-service-role/')
                      role_names = list()
                      for roles in response["Roles"]:
                          role_names.append(roles["RoleName"])
                      if role_check not in role_names:
                          logger.info(f"Creating service linked role {role_check}...")
                          create_role_response = client.create_service_linked_role(
                              AWSServiceName=aws_service_info,
                              Description='Custom service linked role created for the lab.',
                              #CustomSuffix='lab'
                          )
                          logger.info(f"Details for create service linked role: {create_role_response}")
                          data['ServiceLinkedRoleOutput'] = create_role_response['Role']['RoleName']
                      else:
                          logger.info(f"Service linked role {role_check} already present.")
                          data['ServiceLinkedRoleOutput'] = 'Service linked role already present.'

              except Exception as excep:
                  logger.error(f"CloudFormation custom resource {operation} failed. Exception: {traceback.format_exc()}")
                  data['ServiceLinkedRoleOutput'] = None
                  status = cfnresponse.FAILED
              else:
                  status = cfnresponse.SUCCESS
                  logger.info(f"CloudFormation custom resource {operation} succeeded. Result data {json.dumps(data)}.")
              cfnresponse.send(event, context, status, data, physical_id)

  ServiceLinkedRoleCustomResource:
    Type: Custom::ServiceLinkedRoleCustomResource
    DependsOn:
      - CreateServiceLinkedRole
    Properties:
      ServiceToken: !GetAtt CreateServiceLinkedRole.Arn
      CheckRoleName: !Ref RoleName
      AWSServiceInfo: !Ref ServiceName


  #####


  CommandHostSecurityGroup:
    Type: 'AWS::EC2::SecurityGroup'
    DependsOn: AttachGateway
    Properties:
      GroupDescription: Security Group for Command Host
      GroupName: CommandHostSecurityGroup
      VpcId: !Ref VPC
      Tags:
        - Key: Name
          Value: CommandHostSecurityGroup
      SecurityGroupEgress:
        - IpProtocol: tcp
          FromPort: 0
          ToPort: 65535
          CidrIp: 0.0.0.0/0
        - IpProtocol: udp
          FromPort: 0
          ToPort: 65535
          CidrIp: 0.0.0.0/0
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: 22
          ToPort: 22
          CidrIp: 0.0.0.0/0
        - IpProtocol: tcp
          FromPort: 80
          ToPort: 80
          CidrIp: 0.0.0.0/0
        - IpProtocol: tcp
          FromPort: 443
          ToPort: 443
          CidrIp: 0.0.0.0/0
  HTTPAccess:
    Type: 'AWS::EC2::SecurityGroup'
    Properties:
      GroupDescription: Allow HTTP access to client.
      GroupName: HTTPAccess
      VpcId: !Ref VPC
      Tags:
        - Key: Name
          Value: HTTPAccess
      SecurityGroupEgress:
        - IpProtocol: tcp
          FromPort: 0
          ToPort: 65535
          CidrIp: 0.0.0.0/0
        - IpProtocol: udp
          FromPort: 0
          ToPort: 65535
          CidrIp: 0.0.0.0/0
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: 80
          ToPort: 80
          CidrIp: 0.0.0.0/0
        - IpProtocol: tcp
          FromPort: 443
          ToPort: 443
          CidrIp: 0.0.0.0/0
  RootRole:
    Type: 'AWS::IAM::Role'
    Properties:
      RoleName: LabRootRole
      AssumeRolePolicyDocument:
        Version: 2012-10-17
        Statement:
          - Effect: Allow
            Principal:
              Service:
                - ec2.amazonaws.com
            Action:
              - 'sts:AssumeRole'
      Path: /
      ManagedPolicyArns:
        - 'arn:aws:iam::aws:policy/ReadOnlyAccess'
      Policies:
        - PolicyName: root
          PolicyDocument:
            Version: 2012-10-17
            Statement:
              - Sid: AllowAllActions
                Effect: Allow
                Action:
                  - 'autoscaling:AttachInstances'
                  - 'autoscaling:*AutoScalingGroup'
                  - 'autoscaling:Describe*'
                  - 'autoscaling:DetachInstances'
                  - 'autoscaling:*Tags'
                  - 'autoscaling:*Configuration'
                  - 'autoscaling:*Hook'
                  - 'autoscaling:*Lifecycle*'
                  - 'autoscaling:*LoadBalancer*'
                  - 'autoscaling:*Metrics*'
                  - 'autoscaling:*Policy'
                  - 'autoscaling:*Processes'
                  - 'autoscaling:*Standby'
                  - 'autoscaling:*Scheduled*'
                  - 'autoscaling:SetInstanceHealth'
                  - 'autoscaling:SetDesiredCapacity'
                  - 'autoscaling:SetInstanceProtection'
                  - 'cloudformation:List*'
                  - 'cloudformation:Describe*'
                  - 'cloudformation:Detect*'
                  - 'cloudformation:EstimateTemplateCost'
                  - 'cloudformation:Get*'
                  - 'cloudwatch:Describe*'
                  - 'cloudwatch:Get*'
                  - 'cloudwatch:List*'
                  - 'ec2:*Address*'
                  - 'ec2:Cancel*'
                  - 'ec2:Describe*'
                  - 'ec2:*Gateway'
                  - 'ec2:Get*'
                  - 'ec2:*Image*'
                  - 'ec2:*Network*'
                  - 'ec2:*Route*'
                  - 'ec2:*SecurityGroup*'
                  - 'ec2:*Snapshot*'
                  - 'ec2:*Subnet*'
                  - 'ec2:*Vpc*'
                  - 'ec2:*Vpn*'
                  - 'ec2:DeleteFleets'
                  - 'ec2:ResetEbsDefaultKmsKeyId'
                  - 'ec2:ReportInstanceStatus'
                  - 'ec2:ImportKeyPair'
                  - 'ec2:StopInstances'
                  - 'ec2:ProvisionByoipCidr'
                  - 'ec2:WithdrawByoipCidr'
                  - 'ec2:AssociateDhcpOptions'
                  - 'ec2:ConfirmProductInstance'
                  - 'ec2:ConfirmProductInstance'
                  - 'ec2:ModifyFpgaImageAttribute'
                  - 'ec2:EnableEbsEncryptionByDefault'
                  - 'ec2:SendDiagnosticInterrupt'
                  - 'ec2:AssociateIamInstanceProfile'
                  - 'ec2:ReplaceIamInstanceProfileAssociation'
                  - 'ec2:CreateDhcpOptions'
                  - 'ec2:DeleteDhcpOptions'
                  - 'ec2:CreateKeyPair'
                  - 'ec2:DeleteKeyPair'
                  - 'ec2:BundleInstance'
                  - 'ec2:CreateTags'
                  - 'ec2:DisassociateIamInstanceProfile'
                  - 'ec2:AttachVolume'
                  - 'ec2:CreateInstanceExportTask'
                  - 'ec2:MonitorInstances'
                  - 'ec2:UnmonitorInstances'
                  - 'ec2:DetachVolume'
                  - 'ec2:DeleteVolume'
                  - 'ec2:DeleteLaunchTemplate*'
                  - 'ec2:CreateFlowLogs'
                  - 'ec2:DeleteFlowLogs'
                  - 'ec2:ModifyIdentityIdFormat'
                  - 'ec2:ModifyIdFormat'
                  - 'ec2:AdvertiseByoipCidr'
                  - 'ec2:DeprovisionByoipCidr'
                  - 'ec2:DeleteTags'
                  - 'ec2:TerminateInstances'
                  - 'ec2:DisableEbsEncryptionByDefault'
                  - 'ec2:ModifyEbsDefaultKmsKeyId'
                  - 'elasticloadbalancing:AddListenerCertificates'
                  - 'elasticloadbalancing:Modify*'
                  - 'elasticloadbalancing:RegisterTargets'
                  - 'elasticloadbalancing:Set*'
                  - 'elasticloadbalancing:RemoveListenerCertificates'
                  - 'elasticloadbalancing:DeleteLoadBalancer'
                  - 'elasticloadbalancing:Describe*'
                  - 'elasticloadbalancing:CreateListener'
                  - 'elasticloadbalancing:CreateRule'
                  - 'elasticloadbalancing:DeleteRule'
                  - 'elasticloadbalancing:CreateLoadBalancer'
                  - 'elasticloadbalancing:*TargetGroup'
                  - 'elasticloadbalancing:DeregisterTargets'
                  - 'elasticloadbalancing:*Tags'
                  - 'elasticloadbalancing:DeleteListener'
                  - 'events:Describe*'
                  - 'events:List*'
                  - 'events:TestEventPattern'
                  - 'iam:List*'
                  - 'iam:Get*'
                  - 'logs:List*'
                  - 'logs:Describe*'
                  - 'logs:Get*'
                  - 'logs:StartQuery'
                  - 'logs:StopQuery'
                  - 'logs:TestMetricFilter'
                  - 'logs:FilterLogEvents'
                  - 'resource-groups:Get*'
                  - 'resource-groups:List*'
                  - 'resource-groups:SearchResources'
                  - 'ssm:List*'
                  - 'ssm:Describe*'
                  - 'ssm:Get*'
                  - 'ssm:PutInventory'
                  - 'ssm:PutComplianceItems'
                  - 'ssm:PutConfigurePackageResult'
                  - 'ssm:UpdateAssociationStatus'
                  - 'ssm:UpdateInstanceAssociationStatus'
                  - 'ssm:UpdateInstanceInformation'
                  - 'ssm:CancelCommand'
                  - 'ssm:SendCommand'
                  - 'ssm:StartAutomationExecution'
                  - 'ssm:StartSession'
                  - 'ssm:TerminateSession'
                  - 'ssm:ResumeSession'
                  - 'ssm:DescribeSessions'
                  - 'ssm:GetConnectionStatus'
                  - 'sns:TagResource'
                  - 'sns:Delete*'
                  - 'sns:List*'
                  - 'sns:Unsubscribe'
                  - 'sns:Set*'
                  - 'sns:UntagResource'
                  - 'sns:OptInPhoneNumber'
                  - 'sns:CheckIfPhoneNumberIsOptedOut'
                  - 'sns:Publish'
                  - 'sns:Subscribe'
                  - 'sns:ConfirmSubscription'
                  - 'sns:RemovePermission'
                  - 'sns:Get*'
                  - 'sns:Create*'
                  - 'sns:AddPermission'
                  - 'sts:DecodeAuthorizationMessage'
                  - 'tag:*'
                Resource: '*'
              - Sid: RestrictInstanceActions
                Effect: Allow
                Action:
                  - 'ec2:CreateVolume'
                  - 'ec2:ModifyVolume'
                  - 'ec2:ImportVolume'
                  - 'ec2:ModifyVolumeAttribute'
                  - 'ec2:ModifyFleet'
                  - 'ec2:ImportSnapshot'
                  - 'ec2:ResetInstanceAttribute'
                  - 'ec2:CreateFleet'
                  - 'ec2:CreateLaunchTemplateVersion'
                  - 'ec2:EnableVolumeIO'
                  - 'ec2:CreateLaunchTemplate'
                  - 'ec2:ImportInstance'
                  - 'ec2:ModifyInstanceCreditSpecification'
                  - 'ec2:ModifyLaunchTemplate'
                  - 'ec2:ModifyInstanceAttribute'
                  - 'ec2:RebootInstances'
                  - 'ec2:RunInstances'
                  - 'ec2:StartInstances'
                Resource: '*'
                Condition:
                  StringEqualsIfExists:
                    'ec2:Owner': amazon
                  'ForAllValues:StringLikeIfExists':
                    'ec2:InstanceType':
                      - '*.nano'
                      - '*.micro'
                      - '*.small'
                    'ec2:Tenancy': default
                  StringNotEqualsIfExists:
                    'ec2:PlacementGroupStrategy': cluster
                  StringNotEqualsIgnoreCaseIfExists:
                    'ec2:VolumeType':
                      - io1
                      - st1
                  NumericLessThanEqualsIfExists:
                    'ec2:VolumeSize': '51'
              - Sid: RestrictActions
                Effect: Deny
                Action:
                  - 'ec2:*Spot*'
                  - 'ec2:*ReservedInstances*'
                  - 'ec2:*Scheduled*'
                  - 'ec2:*Purchase*'
                  - 'ec2:EnableFastSnapshotRestores'
                Resource: '*'
              - Sid: RestrictASLCInstanceType
                Effect: Allow
                Action: 'autoscaling:CreateLaunchConfiguration'
                Resource: '*'
                Condition:
                  'ForAnyValue:StringNotLikeIfExists':
                    'autoscaling:InstanceType':
                      - '*.nano'
                      - '*.micro'
                      - '*.small'
              - Sid: RestrictASGInstanceTypeAndNo
                Effect: Allow
                Action:
                  - 'autoscaling:UpdateAutoScalingGroup'
                  - 'autoscaling:CreateAutoScalingGroup'
                Resource: '*'
                Condition:
                  NumericGreaterThanIfExists:
                    'autoscaling:MaxSize': '6'
                  'ForAnyValue:StringNotLikeIfExists':
                    'autoscaling:InstanceTypes':
                      - '*.nano'
                      - '*.micro'
                      - '*.small'

  RootInstanceProfile:
    Type: 'AWS::IAM::InstanceProfile'
    Properties:
      Path: /
      Roles:
        - !Ref RootRole
  WaitHandle01:
    Type: 'AWS::CloudFormation::WaitConditionHandle'
    Properties: {}
  WaitCondition01:
    Type: 'AWS::CloudFormation::WaitCondition'
    DependsOn: CommandHost
    Properties:
      Handle: !Ref WaitHandle01
      Timeout: '1800'
  CommandHost:
    Type: 'AWS::EC2::Instance'
    DependsOn:
      - RootInstanceProfile
      - PublicSubnet1
      - CommandHostSecurityGroup
      - AttachGateway
    Properties:
      KeyName: !Ref KeyName
      IamInstanceProfile: !Ref RootInstanceProfile
      ImageId: !Ref LatestAMZN2AmiId
      InstanceType: t3.medium
      NetworkInterfaces:
        - DeviceIndex: '0'
          AssociatePublicIpAddress: true
          SubnetId: !Ref PublicSubnet1
          GroupSet:
            - !Ref CommandHostSecurityGroup
      Tags:
        - Key: Name
          Value: Command Host
      UserData: !Base64
        'Fn::Join':
          - ''
          - - |
              #!/bin/bash -ex
            - |
              yum -y update
            - |
              mkdir /home/ec2-user/.aws
            - |
              cat > /home/ec2-user/.aws/config <<EOF
            - |
              [default]
            - 'region = '
            - !Ref 'AWS::Region'
            - |+

            - |
              EOF
            - |
              chown -R ec2-user:ec2-user /home/ec2-user/.aws
            - |
              cd /home/ec2-user
            - >
              wget
              https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-RSJAWS-1-23732/175-lab-JAWS-autoscaling-linux/s3/UserData.txt
            - /opt/aws/bin/cfn-signal -s true '
            - !Ref WaitHandle01
            - |
              '
Outputs:
  AMIID:
    Value: !Ref LatestAMZN2AmiId
  COMMANDHOSTIP:
    Value: !Sub ${CommandHost.PublicIp}
  KEYNAME:
    Value: !Ref KeyName
  HTTPACCESS:
    Value: !Ref HTTPAccess
  SUBNETID:
    Value: !Ref PublicSubnet2

```
# Uso de escalado automático en AWS (Linux)

## Información general del laboratorio

En este laboratorio usará la Interfaz de la línea de comandos de AWS (AWS CLI) para crear una instancia de Elastic Compute Cloud (EC2) a fin de alojar un servidor web y crear una Imagen de máquina de Amazon (AMI) a partir de dicha instancia. Luego utilizará esta AMI como base para iniciar un sistema que escale automáticamente según una carga variable, con Amazon EC2 Auto Scaling. También creará un Elastic Load Balancer para distribuir la carga entre las instancias de EC2 que se crearon en varias zonas de disponibilidad mediante la configuración de Auto Scaling.

Arquitectura inicial:

![[Pasted image 20240905130236.png]]

Arquitectura final:

![[Pasted image 20240905130246.png]]

## Objetivos

Después de completar este laboratorio, podrá hacer lo siguiente:

- Crear una instancia de EC2 mediante la utilización de un comando de la AWS CLI.
    
- Crear una AMI nueva mediante la utilización de la AWS CLI.
    
- Crear una plantilla de lanzamiento de Amazon EC2.
    
- Crear una configuración de lanzamiento de Amazon EC2 Auto Scaling.
    
- Configurar políticas de escalado y crear un grupo de Auto Scaling para reducir y escalar horizontalmente el número de servidores con base en la carga variable.
    

## Duración

El tiempo estimado para completar este laboratorio es de **45 minutos**.

## Acceso a la Consola de administración de AWS

1. En la parte superior de estas instrucciones, elija Start Lab (Comenzar laboratorio) para iniciar el laboratorio.
    
    Se abrirá el panel **Start Lab** (Comenzar laboratorio), donde se muestra el estado del laboratorio.
    
2. Espere hasta que aparezca el mensaje “Lab status: ready” (Estado de la sesión de laboratorio: listo) y, a continuación, elija la **X** para cerrar el panel **Start Lab** (Comenzar laboratorio).
    
3. En la parte superior de estas instrucciones, seleccione AWS para abrir la Consola de administración de AWS en una pestaña nueva del navegador. El sistema iniciará la sesión de forma automática.
    
    **Sugerencia** Si no se abre una pestaña nueva del navegador, suele aparecer un anuncio o un ícono en la parte superior de este con un mensaje que indica que el navegador impide que el sitio web abra ventanas emergentes. Seleccione el anuncio o ícono y elija **Permitir ventanas emergentes**.
    
4. Ubique la pestaña de la Consola de administración de AWS de modo que aparezca al lado de estas instrucciones. Lo ideal sería que pudiera ver ambas pestañas del navegador al mismo tiempo para seguir los pasos del laboratorio.
    
    **Importante:** No cambie la región del laboratorio a menos que se le indique específicamente.
    

## Tarea 1: crear una AMI nueva para Amazon EC2 Auto Scaling

En esta tarea, iniciará una instancia de EC2 nueva y luego creará una AMI nueva con base en esa instancia en ejecución. Utilizará la AWS CLI en la instancia de EC2 Command Host para realizar todas estas operaciones.

### Tarea 1.1: conectarse a la instancia Command Host

En esta tarea, usará EC2 Instance Connect para conectarse a la instancia de EC2 Command Host que se creó cuando se aprovisionó el laboratorio. Utilizará esta instancia para ejecutar comandos de la AWS CLI.

5. En la **Consola de administración de AWS**, en la barra de **búsqueda**, ingrese y seleccione `EC2` para abrir la **Consola de administración de Elastic Compute Cloud**.
    
6. En el panel de navegación, seleccione **Instancias**.
    
7. En la lista de instancias, seleccione la instancia **Command Host**.
    
8. Elija **Conectar**.
    
9. En la pestaña **EC2 Instance Connect**, seleccione **Conectar**.
    
    **Nota:** Si prefiere usar un cliente SSH para conectarse a la instancia de EC2, consulte la guía para [Conectarse a su instancia de Linux](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstances.html).
    

Ahora que ya se conectó a la instancia Command Host, puede configurar y usar la AWS CLI para llamar a los servicios de AWS.

### Tarea 1.2: configurar la AWS CLI

La AWS CLI esta configurada previamente en la instancia Command Host.

10. Ejecute el siguiente comando para confirmar que la región en la cual se ejecuta la instancia Command Host es la misma que la del laboratorio (la región us-west-2).
    
    `curl http://169.254.169.254/latest/dynamic/instance-identity/document | grep region`
    
    Utilizará esta información sobre la región en los siguientes pasos.
    
11. Ejecute el siguiente comando para actualizar el software de la AWS CLI con las credenciales correctas:
    
    `aws configure`
    
12. Cuando se le solicite, ingrese la siguiente información:
    
    - **AWS Access Key ID** (ID de clave de acceso de AWS): presione Intro.
        
    - **AWS Secret Access Key** (Clave de acceso secreta de AWS): presione Intro.
        
    - **Default region name** (Nombre predeterminado de la región): ingrese el nombre de la región según los pasos anteriores de esta tarea (por ejemplo, `us-west-2`). Si la región ya aparece, presione Intro.
        
    - **Default output format (Formato de resultado predeterminado)**: ingrese `json`.
        

Ahora ya puede acceder y ejecutar los scripts detallados en los siguientes pasos.

13. Para acceder a estos scripts, ingrese el siguiente comando para navegar al directorio correspondiente:
    
    `cd /home/ec2-user/`
    

### Tarea 1.3: crear una instancia de EC2 nueva

En esta tarea, utilizará la AWS CLI para crear una instancia nueva que alojará un servidor web.

14. Ejecute el siguiente comando para inspeccionar el script UserData.txt que se instaló para usted como parte de la creación de Command Host:
    
    `more UserData.txt`
    
    Este script realiza una serie de tareas de inicialización, incluida la actualización de todo el software instalado en el procesador y la instalación de una pequeña aplicación web PHP que puede utilizar para simular una alta carga de CPU en la instancia. Las siguientes líneas aparecen cerca del final del script:
    
    `find -wholename /root/.*history -wholename /home/*/.*history -exec rm -f {} \;`
    
    `find / -name 'authorized_keys' -exec rm -f {} \;`
    
    `rm -rf /var/lib/cloud/data/scripts/*`
    
    Estas líneas borran cualquier historial o información de seguridad que podría haberse dejado de forma accidental en la instancia cuando se tomó la imagen.
    
15. En la parte de arriba de esta pantalla, seleccione **Details** (Detalles) y seleccione **Show** (Mostrar).
    
16. Copie los valores de **KEYNAME**, **AMIID**, **HTTPACCESS** y **SUBNETID** en un documento de un editor de texto y luego haga clic en la **X** para cerrar el panel **Credentials** (Credenciales).
    
17. En el siguiente script, reemplace el texto correspondiente por los valores del paso anterior.
    
    `aws ec2 run-instances --key-name KEYNAME --instance-type t3.micro --image-id AMIID --user-data file:///home/ec2-user/UserData.txt --security-group-ids HTTPACCESS --subnet-id SUBNETID --associate-public-ip-address --tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=WebServer}]' --output text --query 'Instances[*].InstanceId'`
    
18. Ingrese el script modificado en la ventana del terminal y ejecute el script.
    
    El resultado de este comando proporciona un valor **InstanceId**. Los pasos posteriores de este laboratorio se referirán a este valor como **NEW-INSTANCE-ID**. Reemplace este valor según sea necesario durante este laboratorio.
    
19. Copie y pegue el valor **InstanceId** en un editor de texto para usarlo después.
    
20. Para utilizar el comando aws ec2 wait instance-running para supervisar el estado de esta instancia, reemplace _NEW-INSTANCE-ID_, en el siguiente comando, por el valor de **InstanceID** que copió en el paso anterior. Ejecute el comando modificado.
    
    `aws ec2 wait instance-running --instance-ids NEW-INSTANCE-ID`
    
    Espere a que el comando regrese al símbolo del sistema antes de continuar.
    
    La instancia iniciará un servidor web nuevo. Para probar si el servidor web se instaló de manera correcta, debe obtener el nombre de DNS público.
    
21. Para obtener el nombre de DNS público, en el siguiente comando, reemplace _NEW-INSTANCE-ID_ por el valor que copió anteriormente y ejecute el comando modificado:
    
    `aws ec2 describe-instances --instance-id NEW-INSTANCE-ID --query 'Reservations[0].Instances[0].NetworkInterfaces[0].Association.PublicDnsName'`
    
22. Copie el resultado de este comando sin las comillas.
    
    El valor de esta salida se denomina **PUBLIC-DNS-ADDRESS** en los siguientes pasos.
    
23. Ingrese la salida que copió del paso anterior en una pestaña del navegador nueva.
    
    La instalación del servidor web puede tardar unos minutos. Espere 5 minutos antes de continuar con los siguientes pasos.
    
    No seleccione **Start Stress** (Comenzar estrés) en esta etapa.
    
24. En el siguiente comando, reemplace _PUBLIC-DNS-ADDRESS_ por el valor que copió en los pasos anteriores y luego ejecute el comando modificado.
    
    `http://PUBLIC-DNS-ADDRESS/index.php`
    
    Si su servidor web parece no funcionar, consulte con su instructor.
    

### Tarea 1.4: crear una AMI personalizada

En esta tarea, creará una AMI nueva con base en la instancia que acaba de crear.

25. Para crear una AMI nueva con base en esta instancia, reemplace _NEW-INSTANCE-ID_ en el comando aws ec2 create-image por el valor que copió anteriormente y ejecute el comando ajustado:
    
    `aws ec2 create-image --name WebServerAMI --instance-id NEW-INSTANCE-ID`
    

El comando aws ec2 create-image reinicia de forma predeterminada la instancia actual antes de crear la AMI, para garantizar la integridad de la imagen en el sistema de archivos. Mientras se crea la AMI, continúe con la siguiente tarea.

## Tarea 2: crear un entorno de Auto Scaling

En esta sección, creará un equilibrador de carga que agrupe un conjunto de instancias de EC2 bajo una sola dirección del sistema de nombres de dominio (DNS). Utilizará Auto Scaling para crear un grupo de instancias de EC2 dinámicamente escalable y con base en la imagen que creó en la tarea anterior. Por último, creará un conjunto de alarmas que reducirán o escalarán horizontalmente el número de instancias de su grupo de equilibradores de carga cada vez que el rendimiento de la CPU de cualquier máquina dentro del grupo exceda o caiga por debajo de un conjunto de umbrales especificados.

Puede realizar la siguiente tarea con la AWS CLI o la Consola de administración de AWS. Para este laboratorio, usará la Consola de administración de AWS.

### Tarea 2.1: crear un equilibrador de carga de aplicación

En esta tarea, creará un equilibrador de carga para equilibrar el tráfico entre varias instancias de EC2 y zonas de disponibilidad.

26. En el panel de navegación izquierdo de la Consola de administración de Elastic Compute Cloud, localice la sección **Balance de carga** y elija **Balanceadores de carga**.
    
27. Elija Crear balanceador de carga.
    
28. En la sección **Tipos de equilibradores de carga**, en **Balanceador de carga de aplicaciones**, elija **Crear**.
    
29. En la página **Crear balanceador de carga de aplicaciones**, en la sección **Configuración básica**, configure la siguiente opción:
    
    - En **Nombre del balanceador de carga**, ingrese `WebServerELB`.
        
30. En la sección **Mapeo de red**, configure las siguientes opciones:
    
    - En **VPC**, elija **Lab VPC** (VPC de laboratorio).
        
    - En **Mapeos**, seleccione ambas zonas de disponibilidad mencionadas.
        
        - Para la primera zona de disponibilidad seleccione **Subred pública 1**.
            
        - Para la segunda zona de disponibilidad seleccione **Subred pública 2**.
            
        
        Estas opciones configuran el equilibrador de carga para que funcione en varias zonas de disponibilidad.
        
31. En la sección **Grupos de seguridad**, seleccione la **X** para eliminar el grupo de seguridad **predeterminado**.
    
32. En la lista desplegable **Grupos de seguridad**, seleccione **HTTPAccess**.
    
    Ya se creó un grupo de seguridad **HTTPAccess** para usted, el cual permite el acceso mediante HTTP.
    
33. En la sección **Agentes de escucha y direccionamiento**, seleccione el enlace **Crear un grupo de destino**.
    
    **Nota:** Este enlace hace que se abra una pestaña del navegador nueva con las opciones de configuración de **Crear un grupo de destino**.
    
34. En la página **Especificar los detalles del grupo**, en la sección **Basic configuration** (Configuración básica), configure las siguientes opciones:
    
    - En **Elegir un tipo de destino**, seleccione **Instancias**.
        
    - En **Nombre del grupo de destino**, ingrese `webserver-app`.
        
35. En la sección **Comprobaciones de estado**, para **Ruta de comprobación de estado**, ingrese `/index.php`.
    
36. Al final de la página, elija **Siguiente**.
    
37. En la página **Registrar destinos**, seleccione **Crear un grupo de destino**.
    
    Cuando el grupo de destino se cree correctamente, puede cerrar la pestaña del navegador **Grupos de destino**.
    
38. Vuelva a la pestaña del navegador **Balanceadores de carga** y ubique la sección **Agentes de escucha y direccionamiento**. En **Acción predeterminada**, seleccione **Actualizar** a la derecha de la lista desplegable **Reenviar a**.
    
39. Desde la lista desplegable **Reenviar a**, seleccione **webserver-app**.
    
40. Al final de la página, elija **Crear balanceador de carga**.
    

Debería recibir un mensaje similar al que se muestra a continuación:

Se creó correctamente el balanceador de carga: WebServerELB

41. Para visualizar el equilibrador de carga **WebServerELB** que creó, elija **Ver el balanceador de carga**.
    
42. Para copiar el **Nombre de DNS** del equilibrador de carga, utilice la opción de copia y pegue el nombre de DNS en un editor de texto.
    

Necesitará esta información más adelante en el laboratorio.

## Tarea 2.2: crear una plantilla de lanzamiento

En esta tarea, creará una plantilla de lanzamiento para el grupo de Auto Scaling. Una plantilla de lanzamiento es una plantilla que utiliza un grupo de Auto Scaling para iniciar instancias de EC2. Cuando crea una plantilla de lanzamiento, se especifica la información para las instancias, tales como la AMI, tipo de instancia, par de claves, grupo de seguridad y discos.

43. En la Consola de administración de Elastic Compute Cloud del panel de navegación izquierdo, ubique la sección **Instancias** y elija **Plantillas de lanzamiento**.
    
44. Elija **Crear plantilla de lanzamiento**.
    
45. En la sección **Nombre y descripción de la plantilla de lanzamiento** de la página **Crear plantilla de lanzamiento**, configure las siguientes opciones:
    
    - En **Nombre de la plantilla de lanzamiento: _obligatorio_**, ingrese `web-app-launch-template`
        
    - En **Descripción de la versión de la plantilla**, ingrese `A web server for the load test app`
        
    - En **Orientación sobre Auto Scaling**, seleccione **Provide guidance to help me set up a template that I can use with EC2 Auto Scaling** (Proporcionar orientación para ayudarme a configurar una plantilla que pueda utilizar con EC2 Auto Scaling).
        
46. En la sección **Application and OS Images (Amazon machine Image) - required** (Imágenes de aplicaciones y sistemas operativos [Amazon Machine Image]: obligatorio), seleccione la pestaña **Mis AMI**.
    
    Observe que **WebServerAMI** ya está elegido.
    
47. En la sección **Tipo de instancia**, elija la lista desplegable **Tipo de instancia** y seleccione **t3.micro**.
    
48. En la sección **Par de claves (inicio de sesión)**, confirme que la lista desplegable **Nombre del par de claves** esté establecida en **No incluir en la plantilla de lanzamiento**.
    
    Amazon EC2 utiliza criptografía de clave pública para cifrar y descifrar la información de inicio de sesión. Para iniciar sesión en una instancia, deberá crear un par de claves. Al iniciar la instancia, deberá especificar el nombre del par de claves y, cada vez que se conecte a dicha instancia, tendrá que proporcionar la clave privada.
    

**Nota:** En este laboratorio, no necesitará conectarse a la instancia.

49. En la sección **Configuraciones de red**, elija la lista desplegable **Grupos de seguridad** y elija **HTTPAccess**.
    
    Cuando inicia una instancia, puede traspasar los datos de usuario a la instancia. Los datos se pueden utilizar para ejecutar tareas y scripts de configuración.
    
50. Elija **Crear plantilla de lanzamiento**.
    
    Debería recibir un mensaje similar al que se muestra a continuación:
    

Successfully created web-app-launch-template (Se creó correctamente web-app-launch-template).

51. Seleccione **Ver plantillas de lanzamiento**.
    

## Tarea 2.3: crear un grupo de Auto Scaling

En esta tarea, utilizará la plantilla de lanzamiento para crear un grupo de Auto Scaling.

52. Seleccione **web-app-launch-template** y, luego, en la lista desplegable Acciones , elija **Crear grupo de Auto Scaling**.
    
53. En la página **Elija la plantilla de lanzamiento o la configuración**, en la sección **Nombre**, ingrese `Web App Auto Scaling Group` como **Nombre del grupo de Auto Scaling**.
    
54. Elija **Siguiente**.
    
55. En la página **Elegir las opciones de lanzamiento de instancias** de la sección **Red**, configure las siguientes opciones:
    
    - En la lista desplegable **VPC**, elija **Lab VPC** (VPC de laboratorio).
        
    - En la lista desplegable **Zonas de disponibilidad y subredes** seleccione **Subred privada 1 (10.0.2.0/24)** y **Subred privada 2 (10.0.4.0/24)**.
        
56. Elija **Siguiente**.
    
57. En la página **Configurar las opciones avanzadas – _opcional_**, configure las siguientes opciones:
    
    - En la sección **Balance de carga – _opcional_**, elija **Asociar a un balanceador de carga existente**.
        
    - En la sección **Asociar a un balanceador de carga existente**, configure las siguientes opciones:
        
        - Seleccione **Elegir entre los grupos de destino del balanceador de carga**.
            
        - En la lista desplegable de **Grupos de destino del balanceador de carga existentes**, elija **webserver-app | HTTP**.
            
    - En la sección **Comprobaciones de estado**, bajo **Tipos de comprobaciones de estado adicionales**, seleccione **Activar las comprobaciones de estado de Elastic Load Balancing**.
        
58. Elija **Siguiente**.
    
59. En la página **Configurar políticas de escalado y tamaño de grupo – _opcional_**, configure las siguientes opciones:
    
    - En la sección **Tamaño del grupo – _opcional_**, ingrese los siguientes valores:
        
        - **Capacidad deseada**:`2`
            
        - **Capacidad mínima**: `2`
            
        - **Capacidad máxima**: `4`
            
    - En la sección **Políticas de escalado – _opcional_**, configure las siguientes opciones:
        
        - Seleccione **Política de escalado de seguimiento de destino**.
            
        - En **Tipo de métrica**, seleccione **Utilización de CPU promedio**.
            
        - En **Valor de destino**, ingrese `50`.
            
        
        Este cambio le indica a Auto Scaling que mantenga una utilización de CPU promedio del 50 % en todas las instancias. Auto Scaling aumenta o elimina la capacidad de forma automática, según sea necesario, para mantener la métrica en el valor de destino especificado o en un valor próximo. Se ajusta a las fluctuaciones de la métrica debido a un patrón de carga fluctuante.
        
60. Elija **Siguiente**.
    
61. En la página **Añadir notificación – _opcional_**, elija **Siguiente**.
    
62. En la página **Añadir etiquetas – _opcional_**, elija **Añadir etiquetas** y configure las siguientes opciones:
    
    - En **Clave**, ingrese `Name`.
        
    - En **Valor: opcional**, ingrese `WebApp`.
        
63. Elija **Siguiente**.
    
64. En la página **Revisar**, elija **Crear grupo de Auto Scaling**.
    
    Estas opciones harán que se inicien las instancias de EC2 en subredes privadas en ambas zonas de disponibilidad.
    
    En el grupo de Auto Scaling aparecerá, inicialmente, un recuento de **instancias** igual a cero, pero se iniciarán instancias nuevas para alcanzar el recuento deseado de dos instancias.
    
    **Nota**: Si experimenta un error relacionado con que el tipo de instancia t3.micro no se encuentra disponible, vuelva a ejecutar esta tarea y seleccione en su lugar el tipo de instancia t2.micro.
    

### Tarea 3: verificar la configuración de Auto Scaling

En esta tarea, verificará que tanto la configuración de Auto Scaling como el balanceador de carga se encuentren en ejecución al acceder a un script preinstalado en uno de sus servidores que consumirá ciclos de CPU, lo que invocará la alarma de escalado horizontal.

65. En el panel de navegación izquierdo, elija **Instancias**.
    
    Se crean dos instancias nuevas con el nombre **WebApp** como parte de su grupo de Auto Scaling. Mientras se crean estas instancias, se está _Inicializando_ la **Comprobación de estado** de estas dos instancias.
    
    Observe el campo de **Comprobación de estado** de las instancias hasta que el estado sea _2/2 checks passed_ (2/2 comprobaciones aprobadas). Espere a que las dos instancias nuevas completen la inicialización antes de continuar con el siguiente paso.
    
    Es posible que tenga que seleccionar **Actualizar** para ver el estado actualizado.
    
66. Cuando las instancias finalicen la inicialización, seleccione **Grupos de destino** en la sección **Balance de carga** del panel de navegación izquierdo y luego seleccione su grupo de destino, **webserver-app**.
    
67. En la pestaña **Destinos**, compruebe que se están creando dos instancias. Actualice esta lista hasta que el valor de **Estado** de estas instancias cambie a _En buen estado_.
    

Ahora puede probar la aplicación web al acceder a ella a través del equilibrador de carga.

### Tarea 4: verificar la configuración de Auto Scaling

68. Abra una nueva pestaña del navegador web y pegue el **Nombre de DNS** del equilibrador de carga que copió anteriormente en la barra de direcciones. Luego presione Intro.
    
69. En la página web, seleccione **Start Stress** (Comenzar estrés).
    
    Este paso llama al **estrés** de la aplicación en segundo plano, lo que provoca que la utilización de CPU en la instancia que atendió esta solicitud aumente al 100 por ciento.
    
70. En la sección **Auto Scaling** de la Consola de administración de Elastic Compute Cloud del panel de navegación izquierdo, seleccione **Grupos de Auto Scaling**.
    
71. Seleccione **Web App Auto Scaling Group** (Grupo de Auto Scaling de aplicación web).
    
72. Seleccione la pestaña **Actividad**.
    
    Después de unos minutos, debería ver que su grupo de Auto Scaling agrega una instancia nueva. Esto se debe a que Amazon CloudWatch detectó que la utilización de CPU promedio de su grupo de Auto Scaling superó el 50 por ciento y, en respuesta, se invocó su política de escalado vertical.
    
    También puede revisar las instancias nuevas que se inician en el panel de EC2.
    

## Conclusión

¡Felicitaciones! Realizó correctamente lo siguiente:

- Creó una instancia de EC2 mediante la utilización de un comando de la AWS CLI
    
- Creó una AMI nueva mediante la utilización de la AWS CLI
    
- Creó una plantilla de lanzamiento de Amazon EC2
    
- Creó una configuración de lanzamiento de Amazon EC2 Auto Scaling
    
- Configuró políticas de escalado y creó un grupo de Auto Scaling para reducir y escalar horizontalmente el número de servidores con base en carga variable
    

## Laboratorio completado

¡Felicitaciones! Completó la actividad.

73. En la parte superior de la página, haga clic en End Lab (Finalizar laboratorio) y, a continuación, elija Yes (Sí) para confirmar que desea finalizar la actividad.
    

Aparecerá un panel que indica “You may close this message box now. Lab resources are terminating.” (Ya puede cerrar este cuadro de mensaje. Los recursos del laboratorio se están cerrando).

74. Para cerrar el panel **End lab** (Finalizar laboratorio), seleccione la **X** en la esquina superior derecha.
    

## Recursos adicionales

- [Introducción a Amazon EC2 Auto Scaling](https://aws.amazon.com/ec2/autoscaling/getting-started/)
    
- [Introducción a Elastic Load Balancing](https://aws.amazon.com/elasticloadbalancing/getting-started)
    

Para obtener más información sobre AWS Training and Certification, consulte [AWS Training and Certification](http://aws.amazon.com/training/).

_Sus comentarios son bienvenidos y valorados._

Si desea compartir alguna sugerencia o corrección, ingrese los detalles en nuestro [Formulario de contacto de AWS Training and Certification](https://support.aws.amazon.com/#/contacts/aws-training).

_© 2023, Amazon Web Services, Inc. o sus filiales. Todos los derechos reservados. Este contenido no puede reproducirse ni redistribuirse, total ni parcialmente, sin el permiso previo por escrito de Amazon Web Services, Inc. Queda prohibida la copia, el préstamo o la venta de carácter comercial._