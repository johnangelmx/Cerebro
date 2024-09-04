# Balanceador de carga: agentes de escucha

- Proceso que define el puerto y el protocolo con el que escucha el balanceador de carga
- Cada balanceador de carga necesita al menos un agente de escucha para aceptar el tráfico.
- Puede haber hasta 50 agentes de escucha en un balanceador de carga.
- Las reglas de direccionamiento se definen en los agentes de escucha.

![[Pasted image 20240903131944.png]]

# Balanceador de carga de aplicaciones 

**Componentes**

![[Pasted image 20240903132239.png]]

# Balanceador de carga: grupos de destino

- Grupos de destino registrados que ofrecen soporte a:
	* Instancias de Amazon Elastic Compute Cloud (Amazon EC2)
	* Instancias de contenedores de Amazon Elastic Container Service (Amazon ECS)
- Un solo destino puede tener varios registros de grupos de destino 

![[Pasted image 20240903132648.png]]

## Ejemplo balanceador de carga de aplicaciones

![[Pasted image 20240903150813.png]]

# Crear un balanceador de carga de aplicaciones: AWS Command Line interface (AWS CLI)

```zsh
aws elbv2 create-load-balancer \--name my-load-balancer\--subnets subnet-12345678 subnet-23456789 \--security-groups sg-12345678
```

![[Pasted image 20240903150931.png]]

Resultado de comando:
```zsh
{"LoadBalancers": [{"LoadBalancerArn": "arn:aws:elasticloadbalancing:us-east-1:123456789012:loadbalancer/app/my-load-balancer/1234567890123456","DNSName": "my-load-balancer-1234567890123456.us-east-1.elb.amazonaws.com","CanonicalHostedZoneId": "Z35SXDOTRQ7X7K","CreatedTime": "2019-03-28T16:33:59.670Z","LoadBalancerName": "my-load-balancer", ...
```

![[Pasted image 20240903151453.png]]

#  Crear grupo de destino para el balanceador de carga
Utilice el comando `create-target-group` para crear un grupo de destino. Debe especificar la VPC en la que se ejecutan las instancias EC2.
```zsh
aws elbv2 create-target-group \
--name my-targets\
--protocol HTTP \
--port 80 \
--vpc-id vpc-12345678
```

![[Pasted image 20240903151530.png]]
![[Pasted image 20240903151836.png]]

# Registre las instancias EC2 en el grupo de destino
Utilice el comando `register-targets` para registrar las instancias con el grupo de destino
```zsh
aws elbv2 register-targets \
--target-group-arn targetgroup-arn\
--targets Id=i-12345678Id=i-23456789
```
![[Pasted image 20240903151954.png]]

# Crear un agente de escucha para el balanceador de carga
Utilice el comando `create-listener` para crear un agente de escucha para el balanceador de carga.
```zsh
aws elbv2 create-listener \
--load-balancer-arn loadbalancer-arn \
--protocol HTTP \
--port 80 \
--default-actions Type=forward,TargetGroupArn=targetgroup-arn
```

![[Pasted image 20240903152036.png]]
![[Pasted image 20240903152142.png]]

# Compruebe el estado de los destinos registrados
Opcionalmente, compruebe el estado de los destinos registrados para el grupo de destino usando el comando `describe-target-health`.

```zsh
aws elbv2 describe-target-health --target-group-arn targetgroup-arn
```
![[Pasted image 20240903152226.png]]

Comprobando estado:
![[Pasted image 20240903152302.png]]
