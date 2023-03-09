## ¿Que es Internet? 

Internet es una red de computadoras interconectadas que permite la comunicación y el intercambio de información a nivel mundial. Su funcionamiento se basa en la comunicación entre diferentes dispositivos a través de un protocolo de comunicación estándar, conocido como TCP/IP.

El internet funciona mediante la transmisión de datos entre los dispositivos conectados a la red, a través de cables físicos, ondas de radio y satélites. Estos dispositivos pueden ser computadoras, teléfonos inteligentes, tabletas, televisores inteligentes y otros dispositivos que estén conectados a la red.

La información se transmite a través de paquetes de datos, que se dividen en pequeñas unidades antes de ser enviados a través de la red. Estos paquetes son enviados a través de múltiples nodos en la red, y cada nodo los envía al siguiente hasta que llegan a su destino final.

Para acceder a la información en internet, los usuarios utilizan un navegador web, que se conecta a un servidor remoto y descarga los archivos necesarios para mostrar una página web. Los servidores web son dispositivos conectados a la red que almacenan y sirven contenido en internet.

En resumen, el internet funciona como una red global de dispositivos interconectados que transmiten información a través de paquetes de datos y protocolos estándar, permitiendo la comunicación y el intercambio de información a nivel mundial.

---
## La arquitectura cliente-servidor

La arquitectura cliente-servidor es un modelo de comunicación entre sistemas informáticos. Los sistemas se dividen en dos partes principales: el cliente (que se ejecuta en la computadora del usuario) y el servidor (que se ejecuta en una computadora remota). El cliente envía solicitudes al servidor y espera una respuesta, mientras que el servidor recibe solicitudes, procesa los datos o servicios solicitados y envía una respuesta al cliente. Esta arquitectura ofrece ventajas en términos de escalabilidad, centralización, seguridad y eficiencia.

![[Pasted image 20230224101632.png]]

--- 
## TCP/IP

TCP/IP es un conjunto de protocolos de red que permite que las computadoras se comuniquen entre sí. El protocolo de Internet (IP) se encarga de enrutar los paquetes de datos a través de la red, mientras que el protocolo de Control de Transmisión (TCP) garantiza que los datos se transmitan de manera confiable. TCP/IP también incluye otros protocolos para diferentes propósitos, como ICMP, ARP, DHCP y DNS.

>Enrutar: Enrutar es el proceso de enviar paquetes de datos a través de una red de computadoras desde el origen hasta el destino correcto. El enrutamiento se realiza utilizando una variedad de técnicas y protocolos de red, como el Protocolo de Internet (IP).

![[Pasted image 20230224101918.png]]

---
## Puertos, Servidores, Estándares

![[Pasted image 20230224102317.png]]

**Puertos**: Los puertos son canales de comunicación utilizados para enviar y recibir información en una red de computadoras. Cada dispositivo en una red tiene un número de puerto asignado, que se utiliza para identificar los procesos en ejecución en ese dispositivo. Los puertos se dividen en dos categorías: puertos bien conocidos (que van del 0 al 1023) y puertos registrados (que van del 1024 al 49151). Cada protocolo de red utiliza puertos específicos para enviar y recibir información, por lo que los puertos son importantes para garantizar que la información llegue al proceso correcto en el dispositivo de destino.

**Servidores**: Un servidor es un software o hardware que proporciona servicios o recursos a otros dispositivos en una red. Los servidores pueden proporcionar una amplia gama de servicios, como correo electrónico, almacenamiento de archivos, alojamiento de sitios web, bases de datos y mucho más. Los dispositivos que solicitan servicios o recursos de un servidor se denominan clientes. Los servidores y clientes utilizan diferentes protocolos de red (como TCP/IP) para comunicarse entre sí.

**Request for Comments (RFC)**: Los Estándares de Internet, también conocidos como Request for Comments (RFC), son documentos que describen cómo deben funcionar los diferentes protocolos de red en Internet. Los RFC son escritos por expertos en la materia y son revisados por la comunidad de Internet antes de ser adoptados como estándares. Los RFC se utilizan para garantizar que los diferentes dispositivos en una red puedan comunicarse entre sí utilizando los mismos protocolos y estándares.

--- 
## HTTP (Protocolo de Transferencia de Hipertexto)
 
Es el protocolo de red utilizado para transmitir y recibir información en la World Wide Web (WWW). Es el protocolo que permite que las páginas web se comuniquen con los navegadores web (como Chrome, Firefox, Safari, etc.) y los servidores web (como Apache, Nginx, IIS, etc.).

HTTP se basa en un modelo cliente-servidor, donde el cliente (como un navegador web) envía una solicitud de recursos al servidor web (como una página web) a través de una conexión de red. El servidor web recibe la solicitud, procesa la solicitud y envía una respuesta al cliente a través de la misma conexión de red.

HTTP utiliza métodos de solicitud (como GET, POST, PUT, DELETE, etc.) para especificar la acción que se debe realizar en el servidor y códigos de estado de respuesta (como 200 OK, 404 Not Found, 500 Internal Server Error, etc.) para indicar si la solicitud se ha procesado correctamente o no.

![[Pasted image 20230224102601.png]]
![[Pasted image 20230224102702.png]]


---
## HTTPS / Secure Socket Layer

HTTPS (Protocolo de Transferencia de Hipertexto Seguro) es una versión segura del protocolo HTTP que utiliza SSL/TLS (Secure Sockets Layer / Transport Layer Security) para cifrar la comunicación entre un cliente y un servidor.

![[Pasted image 20230224103017.png]]

En otras palabras, HTTPS es similar a HTTP en términos de cómo funciona, pero utiliza una capa adicional de seguridad para proteger la información transmitida entre un navegador web y un servidor web. HTTPS se utiliza principalmente para proteger la privacidad y la integridad de la información confidencial, como las contraseñas, la información de pago y otros datos sensibles que se transmiten a través de la web.

La forma en que funciona HTTPS es que el navegador web y el servidor web establecen una conexión segura mediante SSL/TLS, que utiliza cifrado para proteger los datos transmitidos entre ellos. Esto significa que los datos enviados y recibidos a través de HTTPS están encriptados y protegidos contra el acceso no autorizado.

## Métodos HTTP

Los métodos HTTP son comandos que un cliente (como un navegador web) envía a un servidor web para indicar la acción que se debe realizar en el servidor. En otras palabras, los métodos HTTP se utilizan para especificar qué se debe hacer con un recurso (como una página web) en el servidor.

![[Pasted image 20230224103159.png]]

Los métodos HTTP más comunes son:

- **POST:** se utiliza para enviar datos del cliente al servidor. Cuando un cliente envía una solicitud POST a un servidor, el servidor procesa los datos enviados y puede enviar una respuesta.
- **GET:** se utiliza para recuperar recursos del servidor. Cuando un cliente envía una solicitud GET a un servidor, el servidor responde con el recurso solicitado, como una página web o un archivo.  
- **PUT:** se utiliza para actualizar un recurso existente en el servidor. Cuando un cliente envía una solicitud PUT a un servidor, el servidor actualiza el recurso especificado con los datos proporcionados.
- **DELETE:** se utiliza para eliminar un recurso existente en el servidor. Cuando un cliente envía una solicitud DELETE a un servidor, el servidor elimina el recurso especificado.
- **HEAD:** se utiliza para obtener solo los encabezados de respuesta sin recuperar el recurso completo. Esto puede ser útil para verificar la existencia de un recurso sin descargar todo el contenido.
- **OPTIONS:** se utiliza para obtener información sobre las opciones y características disponibles en el servidor para un recurso determinado.

### GET

GET es uno de los métodos HTTP más comunes que se utilizan para recuperar recursos del servidor. Cuando un cliente envía una solicitud GET a un servidor, el servidor responde con el recurso solicitado, como una página web o un archivo.

En otras palabras, GET se utiliza para solicitar una representación del recurso especificado en la solicitud. Por ejemplo, si un usuario escribe la URL de una página web en el navegador web y presiona Enter, el navegador enviará una solicitud GET al servidor web correspondiente para recuperar la página web solicitada. El servidor web responderá con el código HTML que representa la página web solicitada, y el navegador web lo mostrará en la ventana del navegador.

![[Pasted image 20230224104059.png]]

GET se basa en el modelo de solicitud-respuesta cliente-servidor de HTTP. Cuando un cliente envía una solicitud GET a un servidor, la solicitud incluye información como la URL del recurso solicitado, los parámetros de consulta (si los hay) y los encabezados de solicitud. El servidor procesa la solicitud y envía una respuesta al cliente, que incluye información como el código de estado de la respuesta, los encabezados de respuesta y el cuerpo de la respuesta, que contiene el recurso solicitado.

### POST

POST es uno de los métodos HTTP más comunes que se utilizan para enviar datos del cliente al servidor. Cuando un cliente envía una solicitud POST a un servidor, el servidor procesa los datos enviados y puede enviar una respuesta.

En otras palabras, POST se utiliza para enviar información del cliente al servidor y solicitar que el servidor la procese. Por ejemplo, un formulario web puede utilizar POST para enviar datos ingresados por el usuario al servidor, como el nombre y la dirección de correo electrónico del usuario. El servidor procesa los datos y puede enviar una respuesta, como una página de confirmación o un mensaje de error.

![[Pasted image 20230224104137.png]]

POST es uno de los métodos HTTP más comunes que se utilizan para enviar datos del cliente al servidor. Cuando un cliente envía una solicitud POST a un servidor, el servidor procesa los datos enviados y puede enviar una respuesta.

En otras palabras, POST se utiliza para enviar información del cliente al servidor y solicitar que el servidor la procese. Por ejemplo, un formulario web puede utilizar POST para enviar datos ingresados por el usuario al servidor, como el nombre y la dirección de correo electrónico del usuario. El servidor procesa los datos y puede enviar una respuesta, como una página de confirmación o un mensaje de error.

---
## HTTP Status Code

Los códigos de estado HTTP, también conocidos como códigos de respuesta HTTP, son un conjunto de números que indican el estado de una solicitud realizada por un cliente a un servidor HTTP. Los códigos de estado HTTP se utilizan para comunicar el resultado de una solicitud HTTP al cliente que la ha realizado.

![[Pasted image 20230224104441.png]]

Hay cinco clases de códigos de estado HTTP:

- **Códigos de estado informativos (100-199)** - Estos códigos indican que la solicitud del cliente ha sido recibida y está siendo procesada por el servidor.
- **Códigos de estado de éxito (200-299)** - Estos códigos indican que la solicitud del cliente ha sido procesada correctamente por el servidor.
- **Códigos de estado de redirección (300-399)** - Estos códigos indican que el servidor está redirigiendo al cliente a otra ubicación para completar la solicitud.
- **Códigos de estado de error del cliente (400-499)** - Estos códigos indican que la solicitud del cliente contiene un error y no se puede procesar correctamente.
- **Códigos de estado de error del servidor (500-599)** - Estos códigos indican que el servidor ha encontrado un error al procesar la solicitud del cliente.

Algunos de los códigos de estado HTTP más comunes son:

-   **200 OK:** la solicitud del cliente ha sido procesada correctamente y el servidor ha devuelto la información solicitada.
- **404 Not Found:** el recurso solicitado no se ha encontrado en el servidor.
- **500 Internal Server Error:** se ha producido un error interno en el servidor al procesar la solicitud del cliente.
- **302 Found:** el servidor ha redirigido al cliente a otra ubicación para completar la solicitud.

---
## Herramientas Para Desarrolladores

Las DevTools de Chrome, también conocidas como "Herramientas para desarrolladores", son un conjunto de herramientas que están integradas en el navegador web Google Chrome. Estas herramientas están diseñadas para ayudar a los desarrolladores a depurar, optimizar y mejorar sitios web y aplicaciones web.

![[Pasted image 20230224104750.png]]

Las DevTools de Chrome permiten a los desarrolladores examinar el código fuente, editar el HTML, CSS y JavaScript en vivo, analizar la carga de la página, controlar la red, simular diferentes dispositivos móviles y mucho más. Las herramientas también incluyen un depurador de JavaScript, que permite a los desarrolladores detectar y corregir errores en el código.

Además, las DevTools de Chrome también incluyen una función de auditoría de página, que permite a los desarrolladores evaluar la accesibilidad, el rendimiento y las mejores prácticas de su sitio web o aplicación. La auditoría proporciona una puntuación global para la página y sugerencias específicas para mejorar la accesibilidad, la velocidad de carga y la calidad del código.

---
## Web Stie vs Web Application

La diferencia principal entre un sitio web y una aplicación web es su propósito y funcionalidad.

![[Pasted image 20230224105129.png]]

Un sitio web es una colección de páginas web relacionadas entre sí, que se pueden acceder a través de una dirección URL única y que se utilizan para proporcionar información o contenido en línea. Los sitios web son generalmente estáticos y están diseñados para ser vistos en un navegador web. A menudo, los sitios web se utilizan para proporcionar información de manera unilateral, sin interacción con el usuario.

Por otro lado, una aplicación web es un software interactivo que se ejecuta en un servidor web y se puede acceder a través de un navegador web. Las aplicaciones web pueden ser más dinámicas que los sitios web y se utilizan para proporcionar una experiencia interactiva al usuario, permitiendo que los usuarios realicen tareas y operaciones en línea. Las aplicaciones web suelen estar diseñadas para ser más interactivas, ofreciendo una funcionalidad que puede variar desde el procesamiento de formularios hasta la gestión de bases de datos.