
# ¿Qué es un balanceador de carga? 
Distribuye automáticamente el tráfico de aplicaciones entrantes a través de varios destinos, tales como las instancias de Amazon Elastic Compute Cloud (Amazon EC2), los contenedores y las direcciones del protocolo de internet (IP).

![[Pasted image 20240903101017.png]]

## Características

![[Pasted image 20240903101112.png]]

## Tipos de balanceadores de carga ELB
![[Pasted image 20240903115059.png]]

## Casos de uso

![[Pasted image 20240903122124.png]]

# Balanceador de carga clásica

**Casos de uso**
- Acceder a servidores mediante un único punto 
- Desacoplar el entorno de aplicaciones 
- Proporcionar alta disponibilidad y tole rancia a errores
- Aumentar la elasticidad y escalabilidad

![[Pasted image 20240903122254.png]]

# Balanceador de carga de aplicaciones

**Características**
- Direccionamiento basado en rutas y host 
- Compatibilidad IPv6 nativa
- Puerto dinámicos
- Protocolos de solicitud adicionales admitidos
- Protección contra la eliminación y el seguimiento de solicitudes
- Métricas y registros de acceso mejorados
- Comprobaciones de estado segmentados
  
![[Pasted image 20240903130410.png]]

**Caso de uso**

![[Pasted image 20240903131206.png]]

# Balanceadores de carga de red

**Características**
- Patrones de tráfico repentino y volátiles
- Única dirección IP estática por zona de disponibilidad
- Funciona bien para aplicaciones que requieren rendimiento extremo

![[Pasted image 20240903131332.png]]

**Caso de uso**
![[Pasted image 20240903131400.png]]
	-ELB es un servicio de equilibrio de carga.
	-Los balanceadores de carga distribuyen automáticamente la carga de tráfico entrante. 
	-ELB ofrece tres balanceadores de carga:
	–Balanceador de carga de aplicaciones–Balanceador de carga de red–Balanceador de carga clásico
	-ELB ofrece varias herramientas de monitorización