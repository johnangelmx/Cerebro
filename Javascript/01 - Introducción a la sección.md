# Base Teórica & Práctica

- Historia de JavaScript
    
- Uso de JavaScript en la industria actual
    
- Hola Mundo en JavaScript
    
- Creación de variables y constantes
    
- Introducción a la consola de JavaScript
    
- Depuración y breakpoints
    
- Problemas con la declaración de variables con **var**
    
- Prompts, alerts, confirms.


# Historia de JavaScript

Como todos los lenguajes de programación, o en su mayoría, son creados para resolver un problema en especial, el caso de JavaScript no es la excepción, dado que la idea de su creación fue para satisfacer su necesidad de ejecutar código del lado del cliente.

Lado del cliente y del servidor, cuando hablamos de lados nos referimos en este caso a la interacción en una página web, es decir, que el proceso de un usuario interactuando o "cliqueando" con una página web tiene dos lados, uno sería **lado del cliente** que es la computadora o el dispositivo que el usuario interactúa y el **lado del servidor** el cual es en el que la lógica de la página web se desarrolla. Pero esto no todo el tiempo fue así, antes de la existencia de JavaScript la interacción de ambos lados era tosco, burdo, carecía de información para completar tareas fácilmente como hoy en día es posible.

Ejemplo:
![[Pasted image 20240405093429.png]]
Algo tan simple como completar un formulario tal cual la página quería que fuera completado, era bastante difícil en ese tiempo, dado que si el formulario estaba incompleto o incorrecto tenías que esperar la respuesta del servidor, cosa que hoy en día ya no es necesario, porque gracias a JavaScript la corrección y verificación de campos dentro del formulario se hace del **Lado del cliente**

El creador de JavaScript es Brendan Eich:
![[Pasted image 20240405093745.png|200]]


# Uso de JavaScript en la industria actual

Hoy en día, el usar JS es un estándar del 99% en navegadores web, podría decirse que es un monopolio, él ha podido salir del navegador y ejecutarse en varios ecosistemas tecnológicos.

**Monopolio más allá del navegador:** Si bien JavaScript comenzó como un lenguaje para agregar interactividad a las páginas web, ha trascendido los límites del navegador para convertirse en un lenguaje versátil con un alcance mucho más amplio. Gracias a la aparición de Node.js, JavaScript ahora se utiliza para desarrollar aplicaciones del lado del servidor de alto rendimiento, como Netflix y PayPal. Esto ha llevado a que JavaScript se convierta en un lenguaje de programación omnidireccional, capaz de abarcar tanto el desarrollo web front-end como back-end.

**Un lenguaje para múltiples plataformas:** La ubicuidad de JavaScript se extiende más allá del desarrollo web y del lado del servidor. Frameworks como React Native y Flutter permiten a los desarrolladores crear aplicaciones móviles nativas utilizando JavaScript, lo que reduce la necesidad de aprender lenguajes específicos de la plataforma como Swift o Java. Además, JavaScript se está utilizando cada vez más en el desarrollo de juegos, la automatización y el Internet de las Cosas (IoT), lo que demuestra su adaptabilidad a una amplia gama de dominios.

**Evolución continua:** El ecosistema de JavaScript está en constante evolución, con nuevas bibliotecas, marcos y herramientas que se lanzan regularmente. Esta innovación constante mantiene a JavaScript a la vanguardia del desarrollo web y garantiza que siga siendo una herramienta valiosa para los desarrolladores de todo el mundo. Entre las tendencias más recientes se encuentran la creciente popularidad de TypeScript, un lenguaje superconjunto de JavaScript que ofrece mayor seguridad y escalabilidad, y el auge de la programación funcional, que promueve un estilo de codificación más declarativo y modular.

# Hola mundo en JavaScript
En este apartado vamos a elaborar de forma más práctica las instrucciones y menos teórica.

## Navegadores
La forma en la cual vamos a crear un "Hola Mundo", es imprimiendo en consola, asi que para ello abriremos nuestro navegador y abriremos la herramienta de desarrollo.
![[Pasted image 20240405103755.png]]

Una vez con esta visto, nos dirigiremos a la pestaña `console`, del panel de herramientas de desarrollo y escribiremos:

```JavaScript
console.log('Hola Mundo');
```
Como resultado: 
![[Pasted image 20240405104024.png]]
- Lo que indica el `console.log` es que imprima en consola lo que tenga dentro de los paréntesis.
- El Hola Mundo este envuelto en comillas simples (**''**) le indica que lo que va a imprimir es texto o cadena de caracteres.
- El resultado de la instrucción es la segunda línea de la imagen, una simple cadena de caracteres diciendo Hola Mundo.
- El `undefined` se explicará más adelante, pero lo que se tiene que saber es que en JavaScript todas las funciones siempre tiene un `return`.
- El `.log` indica que es un "método" dentro de un "objeto" esto lo veremos más adelante.

Por ahora es entendible que no comprendas del todo lo que sucede, pero no es para alarmarte, lo importante, aquí es que entiendas que la instrucción `console.log('hola mundo');` sirve para imprimir en consola.

Como lo platicamos con anterioridad, el lenguaje de JavaScript se creó para poder tener interactividad del lado del cliente, es decir, del lado del navegador, entonces ¿cómo hacemos un hola mundo con el navegador que no solo se quede en la consola?

En nuestra consola escribiremos:
```JavaScript
document.write('Hola Mundo');
```
Y como resultado:   
![[Pasted image 20240405105518.png]]
- El método `document.write` es una función integrada en los navegadores web que posibilita la manipulación directa del contenido de una página, sitio o aplicación web. Este método es esencial, ya que permite que lo que visualizamos en el navegador sea considerado como un documento, y mediante su uso podemos "escribir" directamente en dicho documento.
- La parte `'Hola Mundo'` le indica al método que lo que queremos ingresar en el "documento" es una cadena de texto.
- Esto no tiene estilos ni cambios grades, solo es demostrativo para él "hola mundo."

## Node.js

Como indicamos en [[01 - Introducción a la sección#Uso de JavaScript en la industria actual|Uso de JavaScript en la industria actual]], JavaScript es un lenguaje multiplataforma, el cual permite ahora ejecutarse fuera del navegador, y con ello tenemos la herramienta de node.js.

Node.js no es un lenguaje de programación. Más bien, es un entorno de ejecución que se utiliza para ejecutar JavaScript fuera del navegador. Pero ¿Es Node.js Front-end o Back-end?, la respuesta rápida es ambos, pero es mayormente utilizado en back-end, esto gracias a las herramientas que se han ido desarrollando para este entorno de desarrollo llamado "frameworks".

### Verificando si tenemos instalado node y su versión
En cualquier terminal ingresaremos (En mi caso PowerShell): 
```Powershell
node --version
```

Como resultado:
![[Pasted image 20240407044750.png]]

Como habíamos dicho, node.js es un entorno de desarrollo, a lo que se refiere es que es un lugar donde puedes ejecutar código de JavaScript, el cual no está atado a un navegador. 

Entonces para entrar a este entorno tendremos que ingresar en la terminal: 
```PowerShell
node
```
Y se nos abrirá el entorno:    
![[Pasted image 20240407045930.png]]
En él, tal cual lo hicimos en la terminal del navegador, podemos ingresar: 
```Node
console.log('Hola Mundo');
```
Y como resultado: 
![[Pasted image 20240407050139.png]]

## VS Code (Visual Studio Code)
En VS Code existe muchas maneras en las cuales podremos ejecutar JavaScript, pero no son diferente a los anteriores, sino que, aprenderemos a utilizar de manera optimizada nuestro VS Code, que recordemos que es un editor de texto.

### Node.js & VS Code
Para ello tendremos que crear un archivo `app.js` el cual tendrá escrito el `console.log('Hello World');` que hemos practicado hasta ahora.

En nuestro VS Code lo tendremos de la siguiente manera: 
![[Pasted image 20240407131944.png]]
Y abrimos nuestra terminal:
![[Pasted image 20240407132017.png]]
En él mandaremos a llamar a node y que ejecute el archivo `app.js` el cual, el entorno de ejecución puede ejecutarlo siento un archivo .js 

Como resultado: 
![[Pasted image 20240407132155.png]]
Si te preguntas el porqué no tenemos el `undefined` como en navegador o escrito directamente en node, es porque node al ejecutar un archivo actúa de manera diferente al del navegador, consulta [[01 - Introducción a la sección#Diferencias entre ejecuciones Navegadores Web & Node.js|Diferencias de ejecucion Web & Node]]


```Node
console.log(console.log('Hola Mundo'));
```
Como resultado: 
![[Pasted image 20240407132543.png]]
En este caso, la función `console.log()` se está utilizando dos veces. La primera invocación imprime "Hola Mundo" en la consola como se espera. Pero dentro de la llamada a `console.log()`, se está pasando otra llamada a `console.log('Hola Mundo')`. Esta segunda llamada devolverá `undefined`, ya que la función `console.log()` no devuelve ningún valor específico.

#### Diferencias entre ejecuciones Navegadores Web & Node.js
En el navegador, cuando utilizas la consola y ejecutas `console.log('Hola Mundo');`, el navegador interpreta esta instrucción como una expresión que debe ser evaluada. En este caso, la función `console.log()` es llamada y muestra "Hola Mundo" en la consola del navegador. Sin embargo, como `console.log()` no devuelve explícitamente ningún valor, JavaScript devuelve automáticamente `undefined` después de ejecutar la instrucción, lo cual se muestra como la siguiente línea en la consola.
![[Pasted image 20240407140245.png]]

En Node.js, si escribes `console.log('Hola Mundo');` en un archivo y lo ejecutas con `node ./app.js`, el entorno de Node.js interpreta el archivo de manera diferente. En lugar de evaluarlo como una expresión interactiva, Node.js ejecuta el archivo secuencialmente línea por línea. Por lo tanto, cuando se encuentra `console.log('Hola Mundo');`, Node.js simplemente ejecuta esta instrucción y muestra "Hola Mundo" en la consola, sin añadir automáticamente `undefined` después, ya que no se está evaluando como una expresión interactiva sino como una parte de un archivo de código.
![[Pasted image 20240407140309.png]]

Es importante entender que en este contexto, al escribir directamente en el entorno de Node.js en la terminal, estás interactuando con Node.js de manera similar a como interactúas con la consola del navegador. Node.js interpreta las expresiones que escribes y muestra los resultados según corresponda. Por lo tanto, el comportamiento de mostrar `undefined` después de una llamada a `console.log()` es consistente tanto en la consola del navegador como en el entorno de Node.js en la terminal.
![[Pasted image 20240407140350.png]]

### HTML & VS Code
En HTML podemos ejecutar JavaScript de dos formas, la primera es directamente en HTML y para ello tendremos el ejemplo del "Hola mundo":

```HTML
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Hola Mundo</title>
</head>
<body>
    <script>
        console.log('Hola Mundo');
    </script>
</body>
</html>
```
Como resultado:
![[Pasted image 20240407141518.png]]

Pero el tener código JavaScript en el HTML es mala práctica, por ello tenemos que crear un archivo `.js` para ingresar el código y mandarlo a llamar desde el HTML así: 

```HTML
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Hola Mundo</title>
</head>
<body>


	<script src="./app.js"></script>
</body>
</html>
```
Como resultado: 
![[Pasted image 20240407141840.png]]

Las buenas prácticas dictan que este tipo de llamadas a un archivo JavaScript siempre tiene que ser antes del que la etiqueta `</body>` cierre

Y si te vuelves a preguntar el porqué aparece el `undefined` y en el HTML no, es porque HTML es secuencial.

# Introducción a variables y comentarios

## Comentarios
Los comentarios son líneas de código que el intérprete de JavaScript ignorara a la hora de ejecutarlo

```JavaScript
// console.log(console.log('Hola Mundo'));
```

## Variables
Es un contenedor de información que apunta a un lugar en memoria.

Dicha información puede cambiar en el futuro.
