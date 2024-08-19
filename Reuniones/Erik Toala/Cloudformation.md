## Crear par de claves

```bash
aws ec2 create-key-pair --key-name my-key-pair --query 'KeyMaterial' --output text > my-key-pair.pem
```

## Plantilla 
```YAML
AWSTemplateFormatVersion: "2010-09-09"  
Description: |  
  Creacion de pila para entorno de ejecucion de un servidor  
  
Parameters:  
  AmiIdParameter:  
    Type: "AWS::SSM::Parameter::Value<AWS::EC2::Image::Id>"  
    Default: "/aws/service/canonical/ubuntu/server/jammy/stable/current/amd64/hvm/ebs-gp2/ami-id"  
  InstanceTypeParameter:  
    Type: String  
    Default: t3.micro  
    AllowedValues:  
      - t2.micro  
      - t3.micro  
      - t3.small  
      - m5.large  
    Description: Seleccione el tipo de instancia que desea crear.  
  KeyPairParameter:  
    Type: String  
    Default: "my-key-pair"  
  
Resources:  
  PruebaVPC:  
    Type: AWS::EC2::VPC  
    Properties:  
      CidrBlock: "10.0.0.0/16"  
      EnableDnsHostnames: true  
      EnableDnsSupport: true  
      Tags:  
        - Key: "Name"  
          Value: "PruebaVPC"  
  
  InternetGateway:  
    Type: AWS::EC2::InternetGateway  
    Properties:  
      Tags:  
        - Key: "Name"  
          Value: "Internet Gateway"  
  
  IGWattachVPC:  
    Type: AWS::EC2::VPCGatewayAttachment  
    Properties:  
      VpcId: !Ref PruebaVPC  
      InternetGatewayId: !Ref InternetGateway  
  
  RouteTable:  
    Type: AWS::EC2::RouteTable  
    Properties:  
      VpcId: !Ref PruebaVPC  
      Tags:  
        - Key: "Name"  
          Value: "Tabla de ruteo"  
  
  PublicRouteTable:  
    Type: AWS::EC2::Route  
    Properties:  
      DestinationCidrBlock: "0.0.0.0/0"  
      GatewayId: !Ref InternetGateway  
      RouteTableId: !Ref RouteTable  
  
  PublicSubnet1:  
    Type: AWS::EC2::Subnet  
    Properties:  
      VpcId: !Ref PruebaVPC  
      MapPublicIpOnLaunch: true  
      CidrBlock: "10.0.1.0/24"  
      AvailabilityZone: !Select [ 0, !GetAZs "" ]  
      Tags:  
        - Key: "Name"  
          Value: "Public Subnet 1"  
  
  PSattachRT1:  
    Type: AWS::EC2::SubnetRouteTableAssociation  
    Properties:  
      RouteTableId: !Ref RouteTable  
      SubnetId: !Ref PublicSubnet1  
  
  PublicSubnet2:  
    Type: AWS::EC2::Subnet  
    Properties:  
      VpcId: !Ref PruebaVPC  
      MapPublicIpOnLaunch: true  
      CidrBlock: "10.0.2.0/24"  
      AvailabilityZone: !Select [ 1, !GetAZs "" ]  
      Tags:  
        - Key: "Name"  
          Value: "Public Subnet 2"  
  
  PSattachRT2:  
    Type: AWS::EC2::SubnetRouteTableAssociation  
    Properties:  
      RouteTableId: !Ref RouteTable  
      SubnetId: !Ref PublicSubnet2  
  
  SecurityGroup:  
    Type: AWS::EC2::SecurityGroup  
    Properties:  
      GroupName: "SecurityGroup"  
      GroupDescription: "Habilitado para ssh"  
      VpcId: !Ref PruebaVPC  
      SecurityGroupIngress:  
        - IpProtocol: tcp  
          FromPort: 22  
          ToPort: 22  
          CidrIp: 0.0.0.0/0  
      SecurityGroupEgress:  
        - IpProtocol: -1  
          FromPort: -1  
          ToPort: -1  
          CidrIp: 0.0.0.0/0  
      Tags:  
        - Key: "Name"  
          Value: "Grupo de seguridad para ssh"  
  
  IAMRoleForEC2:  
    Type: AWS::IAM::Role  
    Properties:  
      AssumeRolePolicyDocument:  
        Version: "2012-10-17"  
        Statement:  
          - Effect: Allow  
            Principal:  
              Service: ec2.amazonaws.com  
            Action: sts:AssumeRole  
      Path: "/"  
      Policies:  
        - PolicyName: "S3AccessPolicy"  
          PolicyDocument:  
            Version: "2012-10-17"  
            Statement:  
              - Effect: Allow  
                Action:  
                  - s3:ListBucket  
                  - s3:GetObject  
                  - s3:PutObject  
                  - s3:DeleteObject  
                Resource:  
                  - "arn:aws:s3:::cero-papel-repository"  
                  - "arn:aws:s3:::cero-papel-repository/*"  
  
  IAMInstanceProfile:  
    Type: AWS::IAM::InstanceProfile  
    Properties:  
      Path: "/"  
      Roles:  
        - !Ref IAMRoleForEC2  
  
  BackendInstance:  
    Type: AWS::EC2::Instance  
    Properties:  
      ImageId: !Ref AmiIdParameter  
      KeyName: !Ref KeyPairParameter  
      InstanceType: !Ref InstanceTypeParameter  
      SecurityGroupIds:  
        - !Ref SecurityGroup  
      SubnetId: !Ref PublicSubnet1  
      IamInstanceProfile: !Ref IAMInstanceProfile  
      Tags:  
        - Key: "Name"  
          Value: "Servidor Backend"  
  
  S3Bucket:  
    Type: AWS::S3::Bucket  
    Properties:  
      BucketName: "cero-papel-repository"  
      Tags:  
        - Key: "Name"  
          Value: "Cero Papel Repository"  
  
  S3BucketPolicy:  
    Type: AWS::S3::BucketPolicy  
    Properties:  
      Bucket: !Ref S3Bucket  
      PolicyDocument:  
        Version: "2012-10-17"  
        Statement:  
          - Effect: Allow  
            Principal: "*"  
            Action: "s3:*"  
            Resource: !Sub "arn:aws:s3:::${S3Bucket}/*"  
            Condition:  
              StringEquals:  
                "aws:PrincipalArn": !GetAtt IAMRoleForEC2.Arn  
  
Outputs:  
  PublicIp:  
    Description: Server Public IP  
    Value: !GetAtt BackendInstance.PublicIp  
    Export:  
      Name: !Sub "${AWS::StackName}-PublicIp"
```

## Script para comprobación
```python
import boto3
import os

# Crear una sesión de boto3
session = boto3.Session()

# Crear un cliente S3
s3 = session.client('s3')

# Subir un archivo al bucket S3
def upload_file(file_name, bucket, object_name=None):
    if object_name is None:
        object_name = os.path.basename(file_name)
    try:
        s3.upload_file(file_name, bucket, object_name)
        print(f'Successfully uploaded {file_name} to {bucket}/{object_name}')
    except Exception as e:
        print(f'Failed to upload {file_name} to {bucket}/{object_name}: {e}')

# Descargar un archivo del bucket S3
def download_file(bucket, object_name, file_name=None):
    if file_name is None:
        file_name = os.path.basename(object_name)
    try:
        s3.download_file(bucket, object_name, file_name)
        print(f'Successfully downloaded {object_name} from {bucket} to {file_name}')
    except Exception as e:
        print(f'Failed to download {object_name} from {bucket} to {file_name}: {e}')

# Ejemplo de uso
upload_file('local_file.txt', 'cero-papel-repository', 'remote_file.txt')
download_file('cero-papel-repository', 'remote_file.txt', 'downloaded_file.txt')

```

## Comprobación 

```zsh
echo "Este es un archivo de prueba" > local_file.txt
```

```zsh
python3 your_script.py
```
