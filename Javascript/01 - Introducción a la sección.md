# Base Teórica & Práctica

- Historia de JavaScript
    
- Uso de JavaScript en la industria actual
    
- Hola Mundo en JavaScript
    
- Creación de variables y constantes
    
- Introducción a la consola de JavaScript
    
- Problemas con la declaración de variables con **var**
    
- Prompts, alerts, confirms.

---
# Historia de JavaScript

Como todos los lenguajes de programación, o en su mayoría, son creados para resolver un problema en especial, el caso de JavaScript no es la excepción, dado que la idea de su creación fue para satisfacer su necesidad de ejecutar código del lado del cliente.

Lado del cliente y del servidor, cuando hablamos de lados nos referimos en este caso a la interacción en una página web, es decir, que el proceso de un usuario interactuando o "cliqueando" con una página web tiene dos lados, uno sería **lado del cliente** que es la computadora o el dispositivo que el usuario interactúa y el **lado del servidor** el cual es en el que la lógica de la página web se desarrolla. Pero esto no todo el tiempo fue así, antes de la existencia de JavaScript la interacción de ambos lados era tosco, burdo, carecía de información para completar tareas fácilmente como hoy en día es posible.

Ejemplo:
![[Pasted image 20240405093429.png]]
Algo tan simple como completar un formulario tal cual la página quería que fuera completado, era bastante difícil en ese tiempo, dado que si el formulario estaba incompleto o incorrecto tenías que esperar la respuesta del servidor, cosa que hoy en día ya no es necesario, porque gracias a JavaScript la corrección y verificación de campos dentro del formulario se hace del **Lado del cliente**

El creador de JavaScript es Brendan Eich:
![[Pasted image 20240405093745.png|200]]

---
# Uso de JavaScript en la industria actual

Hoy en día, el usar JS es un estándar del 99% en navegadores web, podría decirse que es un monopolio, él ha podido salir del navegador y ejecutarse en varios ecosistemas tecnológicos.

**Monopolio más allá del navegador:** Si bien JavaScript comenzó como un lenguaje para agregar interactividad a las páginas web, ha trascendido los límites del navegador para convertirse en un lenguaje versátil con un alcance mucho más amplio. Gracias a la aparición de Node.js, JavaScript ahora se utiliza para desarrollar aplicaciones del lado del servidor de alto rendimiento, como Netflix y PayPal. Esto ha llevado a que JavaScript se convierta en un lenguaje de programación omnidireccional, capaz de abarcar tanto el desarrollo web front-end como back-end.

**Un lenguaje para múltiples plataformas:** La ubicuidad de JavaScript se extiende más allá del desarrollo web y del lado del servidor. Frameworks como React Native y Flutter permiten a los desarrolladores crear aplicaciones móviles nativas utilizando JavaScript, lo que reduce la necesidad de aprender lenguajes específicos de la plataforma como Swift o Java. Además, JavaScript se está utilizando cada vez más en el desarrollo de juegos, la automatización y el Internet de las Cosas (IoT), lo que demuestra su adaptabilidad a una amplia gama de dominios.

**Evolución continua:** El ecosistema de JavaScript está en constante evolución, con nuevas bibliotecas, marcos y herramientas que se lanzan regularmente. Esta innovación constante mantiene a JavaScript a la vanguardia del desarrollo web y garantiza que siga siendo una herramienta valiosa para los desarrolladores de todo el mundo. Entre las tendencias más recientes se encuentran la creciente popularidad de TypeScript, un lenguaje superconjunto de JavaScript que ofrece mayor seguridad y escalabilidad, y el auge de la programación funcional, que promueve un estilo de codificación más declarativo y modular.

---
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

---
# Introducción a variables y comentarios

## Comentarios
Los comentarios son líneas de código que el intérprete de JavaScript ignorara a la hora de ejecutarlo

```JavaScript
// console.log(console.log('Hola Mundo'));
```

## Variables
Es un contenedor de información que apunta a un lugar en memoria.
Dicha información puede cambiar en el futuro.

### Anatomía de una variable

![[Pasted image 20240411121009.png|500]]

### Tipos de variables en JavaScript

```JavaScript
let a = 10;
var b = 20;
const c = 30;
d = 40;
```

En JavaScript tenemos 4 formas de declarar una variable y cada una de ellas dependiendo de la palabra reservada que tengamos tendrá un comportamiento propio.

### Palabras reservadas 

1. **`let`**: Esta palabra reservada permite cambiar el valor de la variable en cualquier momento. Se considera una buena práctica utilizar `let` cuando se espera que el valor de la variable cambie durante la ejecución del programa.

2. **`var`**: Aunque aún es compatible, el uso de `var` está en desuso y se considera una mala práctica. Funciona de manera similar a `let`, permitiendo el cambio del valor de la variable en cualquier momento. Sin embargo, su alcance puede ser confuso y propenso a errores, especialmente en programas grandes.

3. **`const`**: Utilizar `const` declara una variable cuyo valor no puede cambiar una vez asignado. Es una buena práctica utilizar `const` para valores que no cambiarán durante la ejecución del programa. Intentar asignar un nuevo valor a una variable declarada con `const` generará un error.

4. **Sin palabra reservada (`d = 40`)**: En JavaScript, es posible declarar una variable sin utilizar ninguna palabra reservada, como en el ejemplo `d = 40;`. En JavaScript, cuando se declara una variable sin utilizar ninguna palabra reservada, como en el ejemplo `d = 40;`, esta se comporta de manera diferente a como lo haría una variable declarada con `var`. En realidad, la variable `d` se convierte en una variable global si se encuentra en el ámbito global o en el ámbito de la función si se declara dentro de una función.

Es importante utilizar las palabras reservadas adecuadas al declarar variables en JavaScript para garantizar un código claro, mantenible y libre de errores.

### `Var` Palabra reservada
Como palabra reservada `var` tiene un alcance global y esto no es porque sea una característica agregada recientemente, sino que hay que entender que JavaScript ha evolucionado con los años , anteriormente `var` era una buena práctica y estándar, a su vez como **Sin palabra reservada (`d = 40`)**. Pero JavaScript tienes más de una versión: 

- 1996: LiveScript a JavaScript (estándar)
- 1997: ES1 (ECMAScript 1)
- 2009: ES5 (ECMAScript 5) Con muchas características nuevas.
- 2015: ES6/ES2015 (ECMAScript 2015) que fue la actualización más grande de JavaScript hasta el momento.
- 2015: Se estableció el año de nuevos lanzamientos de JavaScript. 
- 2016/2017/2018/2019/2020...

¿Qué versión debo de usar?

- ES5:
	- Soportada en todos los navegadores web.
- ES6/ES2015, ES7/ES2016, ES8/ES2017:
	- Soportados por la mayoría de navegadores modernos
	- Pero no por todos los navegadores web
	- Muchas características puedes ser implementadas con polyfills
## Polyfill
Es un código que provee el funcionamiento de una nueva característica de JavaScript (ES6), en versiones viejas como ES5.

---
# Introducción a la consola
En este punto vamos a explorar la consola del navegador, recordemos que esta documentación está enfocada para el lado del navegador. 

En la consola de los navegadores hay diferentes comportamientos, esto es por la compatibilidad que cada uno de ellos ofrezca a los usuarios, hoy en día el líder por excelencia es Chrome, que mantiene actualizaciones constantes, por ello los ejemplos serán con la consola de Chrome.

En JavaScript podemos imprimir una variable con `console.log()` entre otras opciones, pero no es la única forma en que podemos imprimir en consola:

```JavaScript
let a = 10,
    b = 20,
    c = 30,
    d = 40,
    x = a + b;
// Imprimir mensajes en consola nos permte saber en que punto esta nuestra variable

console.log(a);
console.warn(b);
console.error(c);
console.info(d);
```

Como resultado tendremos: 
![[Pasted image 20240411125938.png]]

>Cuando ustedes vean paréntesis en JavaScript significa que es una función o es un método, (un método no es más que una función que se encuentra en un objeto)

## `console.log(concatenar)`
También podemos concatenar (es decir, podemos crear unión de números con otros números, o letras con letras)
```JavaScript
console.log("a", a);
console.log("b", b);
console.log("c", c);
console.log("d", d);
```
Como resultado: 
![[Pasted image 20240411130242.png]]

## `console.log({convertir en objeto})`
Existe otra forma de visualizar la variable con el valor, el uso de impresión por objeto:
```JavaScript
console.log({ a });
console.log({ b });
console.log({ c });
console.log({ d });
```
Como resultado:
![[Pasted image 20240411130415.png]]

## `console.log & CSS`
Impresión con estilos CSS:
```JavaScript
console.log('%c Mis Variables', 'color:pink; font-weight: bold;');
```
Como resultado: 
![[Pasted image 20240411130533.png]]

## `console.table`
Existe otra forma de organizar de mejor manera la información y eso es con `console.table`
```JavaScript
let a = 10,
    b = 20,
    c = 'Hola ',
    d = 'Spiderman',
    x = a + b;

console.table({ a, b, c, d, x });
```
Como resultado: 
![[Pasted image 20240411131249.png]]
## Importancia del `const`
```JavaScript
let a = 10,
    b = 20,
    c = 'Hola ',
    d = 'Spiderman',
    x = a + b;
    
const saludo = c+d;
```
La palabra reservada `const` en muchos lenguajes el nombre de la variable tiene que ser en mayúsculas, pero en JavaScript se utiliza de dos modos, es decir: 
- SALUDO: si la variable en todo el proyecto va a tener el mismo valor en todas los archivos.js
- saludo: si la variable solo existirá en una archivo.js

Y para imprimirlo esta vez solo lo invocaremos en nuestra consola: 
![[Pasted image 20240411131818.png]]

# Promt, Confirm y Alert

En los navegadores existen alertas que permiten una interacción con el usuario, este tipo de alertas solo funcionan en navegadores o en donde se ejecute el objeto `window` que en su mayoría son solo navegadores.

Que estas alertas solo se ejecuten en el objeto global `window` hacen que su comportamiento sea el detener procesos y esperar una respuesta, lo cual esto no es una buena práctica.

Pero el uso de ellos en la etapa de desarrollo puede ser de utilidad.

Existen 3 tipos de formas de ingreso de información del usuario por parte del navegador.

## `alert`
```JavaScript
alert('Hola Mundo');
```
Como resultado al abrir un navegador: 
![[Pasted image 20240413140252.png]]
## `promt`
```JavaScript
prompt('Cual es tu nombre?');
```
Como resultado veremos la siguiente ventana:
![[Pasted image 20240413140456.png]]

La ventana `promt` es una función la cual retornara siempre un resultado y este mismo lo puedes guardar en una variable.

La función `promt` puede enviar un segundo argumento, esto para que en el `input` de la ventana aparezca un dato que puede tomarlo de ejemplo o cambiarlo si lo desea:
```JavaScript
let nombre = prompt('Cual es tu nombre?', 'Sin Nombre');
console.log(nombre);
```
Como resultado: 
![[Pasted image 20240413140916.png]]
![[Pasted image 20240413140935.png]]

## `confirm`
```JavaScript
const seleccion = confirm('Esta seguro de borrar esto?');
console.log(seleccion);
```
Como resultado: 
![[Pasted image 20240413141130.png]]
Y en la consola al darle aceptar:
![[Pasted image 20240413141200.png]]

La función de `confirm` es un booleano, es decir true o false, la función siempre retornará un resultado.

## `window` (JavaScript) & `global` (Node)
Recordemos que las alertas que acabamos de ver son métodos que vienen dentro del objeto `window`, pero estos solo sirve en programas en donde se ejecute y tengan el objeto `window` principalmente navegador.

Esto en Node es totalmente diferente, porque no existe `window` existe un método parecido llamado `global`
![[Pasted image 20240413141856.png]]



