```yaml
AWSTemplateFormatVersion: 2010-09-09
#
Parameters:

  KeyName:
    Type: String
    Description: Key used by WebServer.
    Default: lab-key-pair

  AmazonLinuxAMIID:
    Type: AWS::SSM::Parameter::Value<AWS::EC2::Image::Id>
    Default: /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2

Resources:

  VPC:
    Type: AWS::EC2::VPC
    Properties:
      CidrBlock: 10.0.0.0/16
      Tags:
        - Key: Name
          Value: Lab VPC

  InternetGateway:
    Type: AWS::EC2::InternetGateway

  AttachGateway:
    Type: AWS::EC2::VPCGatewayAttachment
    Properties:
      VpcId: !Ref VPC
      InternetGatewayId: !Ref InternetGateway

  PublicSubnet1:
    Type: AWS::EC2::Subnet
    Properties:
      VpcId: !Ref VPC
      CidrBlock: 10.0.0.0/24
      AvailabilityZone: !Select
        - '0'
        - !GetAZs ''
      Tags:
        - Key: Name
          Value: Public Subnet 1

  PublicSubnet2:
    Type: AWS::EC2::Subnet
    Properties:
      VpcId: !Ref VPC
      CidrBlock: 10.0.2.0/24
      AvailabilityZone: !Select
        - '1'
        - !GetAZs ''
      Tags:
        - Key: Name
          Value: Public Subnet 2

  PrivateSubnet1:
    Type: AWS::EC2::Subnet
    Properties:
      VpcId: !Ref VPC
      CidrBlock: 10.0.1.0/24
      AvailabilityZone: !Select
        - '0'
        - !GetAZs ''
      Tags:
        - Key: Name
          Value: Private Subnet 1

  PrivateSubnet2:
    Type: AWS::EC2::Subnet
    Properties:
      VpcId: !Ref VPC
      CidrBlock: 10.0.3.0/24
      AvailabilityZone: !Select
        - '1'
        - !GetAZs ''
      Tags:
        - Key: Name
          Value: Private Subnet 2

  PublicRouteTable:
    Type: AWS::EC2::RouteTable
    Properties:
      VpcId: !Ref VPC
      Tags:
        - Key: Name
          Value: Public Route Table

  PublicRoute:
    Type: AWS::EC2::Route
    Properties:
      RouteTableId: !Ref PublicRouteTable
      DestinationCidrBlock: 0.0.0.0/0
      GatewayId: !Ref InternetGateway

  PublicSubnet1RouteTableAssociation:
    Type: AWS::EC2::SubnetRouteTableAssociation
    Properties:
      SubnetId: !Ref PublicSubnet1
      RouteTableId: !Ref PublicRouteTable

  PublicSubnet2RouteTableAssociation:
    Type: AWS::EC2::SubnetRouteTableAssociation
    Properties:
      SubnetId: !Ref PublicSubnet2
      RouteTableId: !Ref PublicRouteTable

  PrivateRouteTable:
    Type: AWS::EC2::RouteTable
    Properties:
      VpcId: !Ref VPC
      Tags:
        - Key: Name
          Value: Private Route Table

  PrivateSubnet1RouteTableAssociation:
    Type: AWS::EC2::SubnetRouteTableAssociation
    Properties:
      SubnetId: !Ref PrivateSubnet1
      RouteTableId: !Ref PrivateRouteTable

  PrivateSubnet2RouteTableAssociation:
    Type: AWS::EC2::SubnetRouteTableAssociation
    Properties:
      SubnetId: !Ref PrivateSubnet2
      RouteTableId: !Ref PrivateRouteTable

  WebInstance:
    Type: AWS::EC2::Instance
    Properties:
      ImageId: !Ref AmazonLinuxAMIID
      KeyName: !Ref KeyName
      InstanceType: t3.micro
      NetworkInterfaces:
        - DeviceIndex: '0'
          AssociatePublicIpAddress: true
          SubnetId: !Ref PublicSubnet2
          GroupSet:
            - !Ref WebSecurityGroup
      SourceDestCheck: false
      Tags:
        - Key: Name
          Value: Web Server 1
      UserData: !Base64
        Fn::Sub: |
          #!/bin/bash -ex
          yum -y update
          yum -y install httpd php
          /usr/bin/systemctl enable httpd
          /usr/bin/systemctl start httpd
          cd /var/www/html
          #wget https://aws-tc-largeobjects.s3.amazonaws.com/ILT-TF-100-TUFOUN-1/6-lab-scale-loadbalance/loadtestapp.zip
          wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-RSJAWS-1-23732/174-lab-JAWS-scale-load-balance/s3/loadtestapp.zip
          unzip loadtestapp.zip -d /var/www/html/

  WebSecurityGroup:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: Enable HTTP access
      GroupName: Web Security Group
      VpcId: !Ref VPC
      Tags:
        - Key: Name
          Value: Web Security Group
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: 80
          ToPort: 80
          CidrIp: 0.0.0.0/0
        - IpProtocol: tcp
          FromPort: 22
          ToPort: 22
          CidrIp: 0.0.0.0/0

Outputs:
  WebServer:
    Value: !GetAtt WebInstance.PublicIp
    Description: Public IP address of Web Server
```

# Escalado y balanceo de carga de su arquitectura

## Información general del laboratorio

En este laboratorio utilizará los servicios de Elastic Load Balancing (ELB) y Amazon EC2 Auto Scaling para balancear la carga y escalar la infraestructura de forma automática.

ELB distribuye automáticamente el tráfico entrante de las aplicaciones entre varias instancias de Amazon Elastic Compute Cloud (Amazon EC2). ELB proporciona la capacidad de balanceo de carga necesaria con el fin de enrutar el tráfico de la aplicación para ayudarle a lograr la tolerancia a errores en sus aplicaciones.

Auto Scaling le permite mantener la disponibilidad de las aplicaciones y le brinda la capacidad de escalar o reducir horizontalmente, de forma automática, la capacidad de Amazon EC2 según las condiciones que defina. Puede utilizar Auto Scaling para asegurarse de que ejecuta la cantidad que desea de instancias de EC2. Auto Scaling también puede aumentar de forma automática la cantidad de instancias de EC2 durante los picos de demanda, para mantener el rendimiento y reducir la capacidad durante los períodos de baja demanda con el objetivo de minimizar los costos. Auto Scaling es adecuado para aplicaciones con patrones de demanda estables o para aquellas cuyo uso varía cada hora, día o semana.

A continuación, se muestra la arquitectura inicial:

![[Pasted image 20240905125700.png]]

A continuación, se muestra la arquitectura final:

![[Pasted image 20240905125809.png]]
## Objetivos

Después de completar este laboratorio, debería poder realizar lo siguiente:

- Crear una AMI a partir de una instancia de EC2.
    
- Crear un equilibrador de carga.
    
- Crear una plantilla de lanzamiento y un grupo de Auto Scaling.
    
- Configurar un grupo de Auto Scaling para escalar instancias nuevas dentro de subredes privadas.
    
- Utilizar alarmas de Amazon CloudWatch para supervisar el rendimiento de la infraestructura.
    

## Duración

El tiempo estimado para completar este laboratorio es de **45 minutos**.

## Acceso a la Consola de administración de AWS

1. En la parte superior de estas instrucciones, elija **Start Lab** (Comenzar laboratorio) para iniciar el laboratorio.
    
    **Sugerencia**: Si necesita más tiempo para completar el laboratorio, vuelva a seleccionar **Start Lab** (Comenzar el laboratorio) para reiniciar el temporizador del entorno.
    
2. Los recursos del laboratorio se mostrarán en la esquina superior izquierda:
    
    - **AWS** indica que los recursos del laboratorio de AWS se están creando actualmente.
        
    - **AWS** indica que los recursos del laboratorio de AWS se encuentran listos.
        
    
    Espere a que el laboratorio se encuentre listo antes de continuar.
    
3. En la parte superior de estas instrucciones, seleccione **AWS** .
    
    La Consola de administración de AWS se abrirá en una pestaña nueva del navegador. El sistema iniciará la sesión de forma automática.
    
    **Sugerencia:** Si no se abre una pestaña nueva del navegador, suele aparecer un anuncio o un ícono en la parte superior de este con un mensaje que indica que el navegador impide que el sitio web abra ventanas emergentes. Seleccione el anuncio o ícono y elija **Permitir ventanas emergentes**.
    
4. Ubique la pestaña de la Consola de administración de AWS de modo que aparezca al lado de estas instrucciones. Lo ideal es que pueda ver las dos pestañas del navegador a la vez para seguir los pasos del laboratorio.
    
    No cambie la región del laboratorio a menos que se le indique específicamente.
    

## Tarea 1: crear una AMI para Auto Scaling

En esta tarea, creará una AMI para el web server 1 existente. Esta acción hace que se guarde el contenido del disco de arranque, de modo que se puedan iniciar instancias nuevas con contenido idéntico.

5. En la **Consola de administración de AWS**, en la barra de **búsqueda**, ingrese y seleccione `EC2` para abrir la **Consola de administración de Amazon EC2**.
    
6. En el panel de navegación izquierdo, ubique la sección **Instancias** y seleccione **Instancias**.
    
    La instancia **Web Server 1** estará en la lista. Ahora, creará una AMI con base en esta instancia.
    
7. Elija la instancia **Web Server 1**, que debería aparecer en estado En ejecución.
    
8. En la lista desplegable Acciones , elija **Imagen y plantillas** > **Crear imagen** y, luego, configure las siguientes opciones:
    
    - En **Nombre de la imagen**, ingrese `Web Server AMI`.
        
    - En **Descripción de la imagen: _opcional_**, ingrese `Lab AMI for Web Server`
        
9. Seleccione Crear imagen.
    
    En la pantalla de confirmación, se muestra el ID de la AMI de la nueva AMI. Utilizará esta AMI cuando inicie el grupo de Auto Scaling, más adelante en el laboratorio.
    

## Tarea 2: crear un equilibrador de carga

En esta tarea, creará un equilibrador de carga para equilibrar el tráfico entre varias instancias de EC2 y zonas de disponibilidad.

10. En el panel de navegación izquierdo, localice la sección **Balance de carga** y elija **Balanceadores de carga**.
    
11. Elija Crear balanceador de carga.
    
12. En la sección **Tipos de equilibradores de carga**, en **Balanceador de carga de aplicaciones**, elija **Crear**.
    
13. En la página **Crear balanceador de carga de aplicaciones**, en la sección **Configuración básica**, configure la siguiente opción:
    
    - En **Nombre del balanceador de carga**, ingrese `LabELB`.
        
14. En la sección **Mapeo de red**, configure las siguientes opciones:
    
    - En **VPC**, elija **Lab VPC** (VPC de laboratorio).
        
    - En **Mapeos**, seleccione ambas zonas de disponibilidad mencionadas.
        
    - Para la primera zona de disponibilidad seleccione **Subred pública 1**.
        
    - Para la segunda zona de disponibilidad seleccione **Subred pública 2**.
        
    
    Estas opciones configuran el equilibrador de carga para que funcione en varias zonas de disponibilidad.
    
15. En la sección **Grupos de seguridad**, seleccione la **X** para eliminar el grupo de seguridad **predeterminado**.
    
16. En la lista desplegable **Grupos de seguridad**, seleccione **Web Security Group** (Grupo de seguridad web).
    
    Ya se creó el **Web Security Group** (Grupo de seguridad web) que le permite acceder mediante HTTP.
    
17. En la sección **Agentes de escucha y direccionamiento**, seleccione el enlace **Crear un grupo de destino**.
    
    **Nota:** Este enlace hace que se abra una pestaña del navegador nueva con las opciones de configuración de **Crear un grupo de destino**.
    
18. En la nueva pestaña del navegador **Grupos de destino**, en el campo **Basic configuration** (Configuración básica), establezca lo siguiente:
    
    - En **Elegir un tipo de destino**, seleccione **Instancias**.
        
    - En **Nombre del grupo de destino**, ingrese `lab-target-group`.
        
19. Al final de la página, elija **Siguiente**.
    
20. En la página **Registrar destinos**, seleccione **Crear un grupo de destino**.
    
    Cuando el grupo de destino se cree correctamente, puede cerrar la pestaña del navegador **Grupos de destino**.
    
21. Regrese a la pestaña **Balanceadores de carga** en el navegador. En la sección **Agentes de escucha y direccionamiento**, seleccione **Actualizar** a la derecha de la lista desplegable **Reenviar a** de **Acción predeterminada**.
    
22. Desde la lista desplegable **Reenviar a**, seleccione **lab-target-group**.
    
23. Al final de la página, elija **Crear balanceador de carga**.
    

Debería recibir un mensaje similar al que se muestra a continuación:

Se creó correctamente el balanceador de carga: LabELB

24. Para visualizar el equilibrador de carga **LabELB** que creó, elija **Ver el balanceador de carga**.
    
25. Para copiar el **Nombre de DNS** del equilibrador de carga, utilice la opción de copia y pegue el nombre de DNS en un editor de texto.
    
    Necesitará esta información más adelante en el laboratorio.
    

## Tarea 3: crear una plantilla de lanzamiento

En esta tarea, creará una _plantilla de lanzamiento_ para el grupo de Auto Scaling. Una plantilla de lanzamiento es una plantilla que utiliza un grupo de Auto Scaling para iniciar instancias de EC2. Cuando crea una plantilla de lanzamiento, se especifica la información para las instancias, tales como la AMI, tipo de instancia, par de claves, grupo de seguridad y discos.

26. En la parte superior de la Consola de administración de AWS, en la barra de búsqueda, ingrese y seleccione `EC2`
    
27. En el panel de navegación izquierdo, ubique la sección **Instancias** y elija **Plantillas de lanzamiento**.
    
28. Elija **Crear plantilla de lanzamiento**.
    
29. En la sección **Nombre y descripción de la plantilla de lanzamiento** de la página **Crear plantilla de lanzamiento**, configure las siguientes opciones:
    
    - En **Nombre de la plantilla de lanzamiento: _obligatorio_**, ingrese `lab-app-launch-template`
        
    - En **Descripción de la versión de la plantilla**, ingrese `A web server for the load test app`
        
    - En **Orientación sobre Auto Scaling**, elija **Provide guidance to help me set up a template that I can use with EC2 Auto Scaling** (Proporcionar orientación para ayudarme a configurar una plantilla que pueda utilizar con EC2 Auto Scaling).
        
30. En la sección **Application and OS Images (Amazon machine Image) - required** (Imágenes de aplicaciones y sistemas operativos [Amazon Machine Image]: obligatorio), seleccione la pestaña **Mis AMI**. Observe que **Web Server AMI** (AMI de servidor web) ya está elegido.
    
31. En la sección **Tipo de instancia**, elija la lista desplegable **Tipo de instancia** y seleccione **t3.micro**.
    
32. En la sección **Par de claves (inicio de sesión)**, confirme que la lista desplegable **Nombre del par de claves** esté establecida en **No incluir en la plantilla de lanzamiento**.
    
    Amazon EC2 utiliza criptografía de clave pública para cifrar y descifrar la información de inicio de sesión. Para iniciar sesión en una instancia, deberá crear un par de claves. Al iniciar la instancia, deberá especificar el nombre del par de claves y, cada vez que se conecte a dicha instancia, tendrá que proporcionar la clave privada.
    
    **Nota:** En este laboratorio, no necesitará conectarse a la instancia.
    
33. En la sección **Configuraciones de red**, elija la lista desplegable **Grupos de seguridad** y elija **Web Security Group** (Grupo de seguridad web).
    
    Cuando inicia una instancia, puede traspasar los datos de usuario a la instancia. Los datos se pueden utilizar para ejecutar tareas y scripts de configuración.
     
34. Elija **Crear plantilla de lanzamiento**.
    

Debería recibir un mensaje similar al que se muestra a continuación:

Successfully created lab-app-launch-template (Se creó correctamente lab-app-launch-template).

35. Seleccione **Ver plantillas de lanzamiento**.
    

## Tarea 4: crear un grupo de Auto Scaling

En esta tarea, utilizará la plantilla de lanzamiento para crear un grupo de Auto Scaling.

36. Seleccione **lab-app-launch-template** y, luego, en la lista desplegable Acciones , elija **Crear grupo de Auto Scaling**.
    
37. En la página **Elija la plantilla de lanzamiento o la configuración**, en la sección **Nombre**, ingrese `Lab Auto Scaling Group` como **Nombre del grupo de Auto Scaling**.
    
38. Elija **Siguiente**.
    
39. En la página **Elegir las opciones de lanzamiento de instancias** de la sección **Red**, configure las siguientes opciones:
    
    - En la lista desplegable **VPC**, elija **Lab VPC** (VPC de laboratorio).
        
    - En la lista desplegable **Zonas de disponibilidad y subredes** seleccione **Subred privada 1 (10.0.1.0/24)** y **Subred privada 2 (10.0.3.0/24)**.
        
40. Elija **Siguiente**.
    
41. En la página **Configurar las opciones avanzadas – _opcional_**, configure las siguientes opciones:
    
    - En la sección **Balance de carga – _opcional_**, elija **Asociar a un balanceador de carga existente**.
        
    - En la sección **Asociar a un balanceador de carga existente**, configure las siguientes opciones:
        
        - Seleccione **Elegir entre los grupos de destino del balanceador de carga**.
            
        - En la lista desplegable de **Grupos de destino del balanceador de carga existentes**, elija **lab-target-group | HTTP**.
            
    - En la sección **Comprobaciones de estado – _opcional_**, para **Tipo de comprobación de estado**, seleccione **ELB**.
        
42. Elija **Siguiente**.
    
43. En la página **Configurar políticas de escalado y tamaño de grupo – _opcional_**, configure las siguientes opciones:
    
    - En la sección **Tamaño del grupo – _opcional_**, ingrese los siguientes valores:
        
        - **Capacidad deseada**:`2`
            
        - **Capacidad mínima**: `2`
            
        - **Capacidad máxima**: `4`
            
    - En la sección **Políticas de escalado – _opcional_**, configure las siguientes opciones:
        
        - Seleccione **Política de escalado de seguimiento de destino**.
            
        - En **Tipo de métrica**, seleccione **Utilización de CPU promedio**.
            
        - Cambie **Valor de destino** a `50`.
            
        
        Este cambio le indica a Auto Scaling que mantenga una utilización de CPU promedio del 50 % en todas las instancias. Auto Scaling aumenta o elimina la capacidad de forma automática, según sea necesario, para mantener la métrica en el valor de destino especificado o en un valor próximo. Se ajusta a las fluctuaciones de la métrica debido a un patrón de carga fluctuante.
        
44. Elija **Siguiente**.
    
45. En la página **Añadir notificación – _opcional_**, elija **Siguiente**.
    
46. En la página **Añadir etiquetas – _opcional_**, elija **Añadir etiquetas** y configure las siguientes opciones:
    
    - **Clave:** ingrese `Name`
        
    - **Valor: opcional** ingrese `Lab Instance`
        
47. Elija **Siguiente**.
    
48. Elija **Crear grupo de Auto Scaling**.
    
    Estas opciones harán que se inicien las instancias de EC2 en subredes privadas en ambas zonas de disponibilidad.
    
    En el grupo de Auto Scaling aparecerá, inicialmente, un recuento de **instancias** igual a cero, pero se iniciarán instancias nuevas para alcanzar el recuento deseado de dos instancias.
    
    **Nota**: Si experimenta un error relacionado con que el tipo de instancia t3.micro no se encuentra disponible, vuelva a ejecutar esta tarea y seleccione en su lugar el tipo de instancia t2.micro.
    

## Tarea 5: comprobar el funcionamiento del balanceo de carga

En esta tarea, verificará si el balanceo de carga está funcionando correctamente.

49. En el panel de navegación izquierdo, ubique la sección **Instancias** y seleccione **Instancias**.
    
    Verá dos instancias nuevas llamadas **Lab Instance** (Instancia de laboratorio). Auto Scaling inició estas instancias. Si no se visualizan las instancias o sus nombres, espere 30 segundos y seleccione Actualizar .
    
    En primer lugar, asegúrese de que las instancias nuevas aprobaron la comprobación de estado.
    
50. En el panel de navegación izquierdo, en la sección **Balance de carga**, elija **Grupos de destino**.
    
51. Elija **lab-target-group**.
    
    En la sección **Destinos registrados** deberían aparecer dos destinos **Lab Instance** (Instancia de laboratorio) para este grupo de destino.
    
52. Espere hasta que el valor de **Estado** de ambas instancias cambie a _En buen estado_. Elija Actualizar para revisar las actualizaciones.
    
    _En buen estado_ significa que la instancia aprobó la comprobación de estado del equilibrador de carga. Esto significa que el equilibrador de carga enviará tráfico a la instancia.
    
    Ahora, puede acceder a las instancias que se iniciaron en el grupo de Auto Scaling mediante el equilibrador de carga.
    
53. Abra una pestaña nueva en el navegador web, pegue el nombre de DNS que copió anteriormente y presione Intro.
    
    La aplicación **Load Test** (Prueba de carga) debería aparecer en el navegador, lo que significa que el equilibrador de carga recibió la solicitud, la envió a una de las instancias de EC2 y luego arrojó el resultado.
    

## Tarea 6: realizar pruebas de Auto Scaling

Creó un grupo de Auto Scaling con un mínimo de dos instancias y un máximo de cuatro. En este momento, hay dos instancias en ejecución, porque dos es el tamaño mínimo y el grupo no está sujeto a ninguna carga actualmente. Ahora, aumentará la carga para que Auto Scaling agregue instancias adicionales.

56. Regrese a la Consola de administración de AWS, pero mantenga abierta la pestaña de la aplicación **Load Test** (Prueba de carga). Volverá a esta pestaña pronto.
    
57. En la Consola de administración de AWS, en la barra de búsqueda, ingrese `CloudWatch` y selecciónelo.
    
58. En el panel de navegación izquierdo, en la sección **Alarmas**, elija **Todas las alarmas**.
    
    Aparecerán dos alarmas. El grupo de Auto Scaling creó estas dos alarmas de forma automática. Estas alarmas mantendrán automáticamente la carga de CPU promedio cerca del 50 por ciento y, al mismo tiempo, respetarán la limitación de tener entre 2 y 4 instancias.
    
59. Elija la alarma que incluye **AlarmHigh** en el nombre, la cual debería estar es un **Estado** de _Correcto_.
    
    Si el **Estado** de la alarma no se muestra como _Correcto_, espere un minuto y luego elija Actualizar hasta que el **Estado** cambie.
    
    El estado _Correcto_ indica que la alarma no se ha iniciado. Es la alarma de **Utilización de la CPU > 50**, la cual agrega instancias cuando el uso de CPU promedio es alto. En este momento, el gráfico debería mostrar niveles muy bajos de utilización de CPU.
    
    Ahora, le indicará a la aplicación que realice cálculos que deberían aumentar el nivel de utilización de CPU.
    
60. Regrese a la pestaña del navegador con la aplicación **Load Test** (Prueba de carga).
    
61. Elija **Load Test** (Prueba de carga) junto al logotipo de AWS.
    
    Este paso hará que la aplicación genere cargas elevadas. La página del navegador se actualizará de forma automática, para que todas las instancias del grupo de Auto Scaling generen cargas. No cierre esta pestaña.
    
62. Regrese a la pestaña del navegador donde se encuentra la **Consola de administración de CloudWatch**.
    
    En menos de 5 minutos, el estado de la alarma **AlarmLow** debería cambiar a _Correcto_ y el estado de la alarma **AlarmHigh** debería cambiar a _En modo alarma_.
    
    Seleccione Actualizar cada 60 segundos para actualizar la pantalla.
    
    Debería ver en el gráfico **AlarmHigh** un porcentaje en aumento del uso de CPU. Cuando cruza la línea del 50 por ciento por más de 3 minutos, inicia Auto Scaling para agregar instancias adicionales.
    
63. Espere hasta que la alarma **AlarmHigh** entre en estado _En modo alarma_.
    
    Ahora puede visualizar la instancia o instancias adicionales que se iniciaron.
    
64. En la Consola de administración de AWS, en la barra de búsqueda, ingrese `EC2` y selecciónelo.
    
65. En el panel de navegación izquierdo, ubique la sección **Instancias** y seleccione **Instancias**.
    
    Debería haber más de dos instancias llamadas **Lab Instance** (Instancia de laboratorio) en ejecución. Auto Scaling creó las instancias nuevas como respuesta a la alarma.
    

## Tarea 7: terminar la instancia web server 1

En esta tarea, terminará la instancia **Web Server 1**. Esta instancia se utilizó para crear la AMI que usó el grupo de Auto Scaling, pero esta ya no es necesaria.

66. Seleccione **Web Server 1** y asegúrese de que sea la única instancia que seleccionó.
    
67. En el menú desplegable Estado de la instancia , seleccione **Terminar instancia**.
    
68. Seleccione Terminar.
    

## Desafío opcional: crear una AMI mediante la utilización de la AWS CLI

Este desafío es opcional y se ofrece en caso de que le quede tiempo en el laboratorio.

En este desafío, debe crear una AMI mediante la utilización de comandos de la Interfaz de la línea de comandos de AWS (AWS CLI).

69. Sus tareas son las siguientes:
    
    - Utilice Amazon EC2 Instance Connect para conectarse a una de las instancias de EC2 que creó anteriormente.
        
    - En la parte superior de la página, seleccione **AWS Details** (Detalles de AWS). Para **AWS CLI**, elija **Mostrar**. Configure las credenciales de AWS con base en la información que se proporciona.
        
        - Para obtener más información sobre cómo configurar las credenciales de AWS, consulte [Configuration and Credential File Settings](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html) (Configuración del archivo de ajustes y credenciales).
            
    - Después de configurar las credenciales, cree una AMI mediante la AWS CLI.
        
        - Para obtener más información sobre cómo crear una AMI mediante la utilización de la AWS CLI, consulte [AWS CLI Command Reference Examples](https://docs.aws.amazon.com/cli/latest/reference/ec2/create-image.html#examples) (Ejemplos de referencia de comandos de la AWS CLI).
            
        
        **Sugerencia:** Debe proporcionar el nombre de la AMI y el ID de la instancia de EC2 para la cual necesita la imagen.
        

## Conclusión

¡Felicitaciones! Realizó correctamente lo siguiente:

- Creó una AMI a partir de una instancia de EC2.
    
- Creó un equilibrador de carga.
    
- Creó una plantilla de lanzamiento y un grupo de Auto Scaling.
    
- Configuró un grupo de Auto Scaling para escalar instancias nuevas dentro de subredes privadas.
    
- Utilizó alarmas de Amazon CloudWatch para supervisar el rendimiento de la infraestructura.
    

## Laboratorio completado

¡Felicitaciones! Completó el laboratorio.

70. En la parte superior de esta página, seleccione **End Lab** (Finalizar laboratorio) y, a continuación, elija Yes (Sí) para confirmar que desea finalizarlo.
    
    Aparece brevemente el mensaje “Ended AWS Lab Successfully” (Finalizó el laboratorio de AWS correctamente), el cual indica que finalizó el laboratorio.
    

## Recursos adicionales

- [Introducción a Amazon EC2 Auto Scaling](https://aws.amazon.com/ec2/autoscaling/getting-started/)
    
- [Introducción a Elastic Load Balancing](https://aws.amazon.com/elasticloadbalancing/getting-started)
    

Para obtener más información sobre AWS Training and Certification, consulte [AWS Training and Certification](http://aws.amazon.com/training/).

_Sus comentarios son bienvenidos y valorados._

Si desea compartir alguna sugerencia o corrección, ingrese los detalles en nuestro [Formulario de contacto de AWS Training and Certification](https://support.aws.amazon.com/#/contacts/aws-training).

_© 2023, Amazon Web Services, Inc. o sus filiales. Todos los derechos reservados. Este contenido no puede reproducirse ni redistribuirse, total ni parcialmente, sin el permiso previo por escrito de Amazon Web Services, Inc. Queda prohibida la copia, el préstamo o la venta de carácter comercial._