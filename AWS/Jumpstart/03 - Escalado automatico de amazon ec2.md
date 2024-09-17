# Amazon EC2 Auto Scaling
Amazon EC2 Auto Scaling lo ayuda a garantizar que cuenta con la cantidad correcta de instancias de Amazon EC2 disponibles para gestionar la carga de su aplicación. Crea colecciones de instancias EC2, denominadas _grupos de Auto Scaling_. Puede especificar el número mínimo de instancias en cada grupo de escalado automático y Amazon EC2 Auto Scaling garantizará que el grupo nunca tenga menos de esas instancias. Puede especificar el número máximo de instancias en cada grupo de escalado automático y Amazon EC2 Auto Scaling garantizará que el grupo nunca tenga más de esas instancias.


- Lanzar o terminar las instancias de Amazon Elastic Compute Cloud (Amazon EC2) automáticamente, según:
	-  Comprobaciones de estado
	- Políticas predeterminadas por el usuario que están impulsadas por Amazon CloudWatch
	- Cronogramas
	- Otros criterios (por ejemplo, programación)
	- Utilizando manualmente la capacidad deseada
- Realizar un escalado horizontal para ajustarse a la demanda y una reducción horizontal, si quiere reducir costos.
![[Pasted image 20240904130525.png]]

## Auto Scaling en acción

### Plantilla de lanzamiento
Para crear una plantilla de lanzamiento, debe especificar:
- Amazon Machine Image (AMI)
- Tipo de instancia
- VPC
- Grupo de seguridad
- Almacenamiento
- Instancia de par de claves
- Roles de IAM
- Datos de Usuario
- Etiquetado
![[Pasted image 20240904130730.png]]

### Grupo de Amazon EC2 Auto Scaling
**Grupo lógico de instancias EC2**

Realizar escalado automático entre:
- Mínimo 
- Objetivo (Opcional)
- Máximo

Integración con Elastic Load Balacing (Opcional)
Comprobaciones de estado para mantener el tamaño del grupo
Distribuya y equilibre las instancias entre zonas de disponibilidad

### Política de Amazon EC2 Auto Scaling
**Política de Amazon EC2 Auto Scaling**

Parámetros para llevar a cabo una acción de Auto Scaling de Amazon EC2

¿Cómo activar políticas? 
- alarma Amazon CloudWatch
- Seguimiento de objetivos
- Programadas
- Manualmente

Realice un escalado o una reducción horizontal y define en que medida lo hace:
- ChangeInCapacity (+/-#)
- ExactCapacity (#)
- ChangeInPercent (+/-%)

## Amazon EC2 Auto Scaling y estado de la instancia

- Mantiene el estado de las instancias
- Termina las instancias con marcas del mal estado
- Utiliza las comprobaciones de estado de la instancia de EC2 de manera predeterminada
- Puede configurar estas comprobaciones si las instancias están detrás de un balanceador de carga:
	- Comprobaciones de instancias de balanceador de carga
	- Verificaciones de instancias EC2
- Puede activar el reciclado de instancias a través de scripts externos:
	- **Comando**
		- `aws autoscaling set-instance-health`


## Política de terminación de Amazon EC2 Auto Scaling

- Define que instancia se termina con el escalado descendente
- define el orden de terminación según estos factores
	- Zona de disponibilidad con el número más grande de instancias
	- Varias políticas (las políticas se ejecutaran en el orden de enumeración)
	  
![[Pasted image 20240904131754.png]]

## Políticas de terminación

| Politica de terminacion      | Descripcion                                                                            |
| ---------------------------- | -------------------------------------------------------------------------------------- |
| **OldestInstance**           | Selecciona las instancias ejecutadas por mas tiempo                                    |
| **NewestInstance**           | Selecciona las instancias ejecutadas por menos tiempo                                  |
| **OldestLaunchTemplate**     | Termina la instancia con la plantilaa de lanzamiento mas antigua<br>( Predeterminado ) |
| **ClosetToNextInstanceHour** | Termina la instancia mas cercana a la próxima hora facturable<br>( Predeterminado)     |

## Creación de un grupo de estado estable

**Grupo de estado estable:**
- Configurar un grupo de Amazon EC2 Auto Scaling con los mismos valores mínimos, máximos y deseados.
- La instancia se recrea automáticamente si se pone en mal estado o si falla la zona de disponibilidad
- Tiempo de inactividad posible mientras se recicla la instancia

**Caso de uso:**
Mantenga el servidor de Traducción de direcciones de red (NAT) en estado estable en cada zona de disponibilidad.


# Tipos de Escalado Programado: Ejemplo

![[Pasted image 20240904143309.png]]


## Escalado Dinámico![[Pasted image 20240904143333.png]]

## Escalado Predictivo

- Carga de previsión 
- Capacidad mínima de programación 

#### Caso de uso
- Escalado dinámico de seguimiento de destino
- Aplicaciones que tienen picos periódicos

![[Pasted image 20240904143455.png]]