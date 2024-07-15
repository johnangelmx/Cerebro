- ¿Qué son los primitivos?
    
- Palabras reservadas
    
- Arreglos
    
- Objetos literales
    
- Funciones básicas
    
- Funciones de flecha
    
- Retorno de las funciones
    
- Ejercicios y ejemplos con cada tipo expuesto

---
# Tipos de datos primitivos

El tipado de dato que pueda tener una variable, cuando hablamos de JavaScript, es un lenguaje de tipado débil, es decir, no le decimos a JavaScript que es lo que va a contener una variable, ya sea un número, un string, un booleano, etc., esto porque la asignación del valor de la variable dependerá de como la expresemos:

En Java, un lenguaje fuertemente tipado, si queremos decir que una variable canasta tendrá un valor de manzana seria de la siguiente forma: 
```Java
    String canasta = "manzana";
    System.out.print(canasta);
```
Como resultado tendremos:
![[Pasted image 20240413143318.png]]

En cambio, en **JavaScript**:
```JavaScript
	let canasta = "Manzana";
	console.log(canasta)
```
Como en el ejemplo a JavaScript hay que decir como se va a comportar la variable (`let` o `const`) y especificar el valor únicamente asignándolo a la variable.

## Primitivos
Los primitivos en JavaScript son tipos de datos fundamentales que representan valores simples. Son "primitivos" en el sentido de que no son objetos, es decir, no tienen métodos o propiedades asociadas con ellos. Además, son inmutables, lo que significa que una vez que se crea un valor primitivo, no se puede cambiar.

Cuando digo que los primitivos son "inmutables", me refiero a que no pueden cambiar una vez que se han creado. Piensa en ellos como bloques sólidos de información que no pueden ser modificados.

¿Pero cuándo le asignamos un número a la variable no estamos cambiando el valor?

```JavaScript
let numero = 5;
numero = 10; //Intentamos cambiar el valor de "numero"
```
A primera vista, podría parecer que estamos cambiando el valor de "número" de 5 a 10. Pero en realidad, lo que estamos haciendo es crear un nuevo valor (10) y asignarlo a la variable "número". El valor original (5) sigue siendo el mismo, no se ha cambiado. Es como si hubieras sacado el número 5 de la caja y pusieras un 10 en su lugar.

Cuando dices que el número es 5, ese 5 es como un bloque sólido dentro de la caja. No importa cuánto lo muevas o intentes cambiarlo, seguirá siendo 5. No estamos hablando de la variable sino al tipo de dato, por eso se considera inmutable, porque no se está cambiando el valor 5, se crea un nuevo valor y se le asigna a la variable.

Hay 6 tipos de datos primitivos en JavaScript:
* **Boolean** - true/false :: Verdadero y Falso.
* **Null** - Sin valor en lo absoluto.
* **Undefined** - Una variable declarada que aún no se le asigna un valor.
* **Number** - integers, floats, etc.
* **String** - Una cadena de caracteres, ej.: Palabras, nombre de personas
* **Symbol** - Es un valor único que no es igual a ningún otro valor.

---
# Introducción general a los tipos primitivos
```JavaScript
let nombre = 'Peter Parker'; //String
console.log(nombre);

nombre = 'Ben Parker';
console.log(nombre);

nombre = "Tia May";
nombre = `Tia May`;
console.log(typeof nombre)

nombre = 123;
console.log(typeof nombre)


let esMarvel = false; //Boleano
console.log(esMarvel);

let edad = 33; //Number
console.log(typeof edad);

edad = 33.001;
console.log(typeof edad);


let superPoder; // Undefined
console.log(typeof superPoder); // ???


let soyNull = null; // Null
console.log(typeof soyNull);

let symbol1 = Symbol('a'); //Symbol
let symbol2 = Symbol('a');

console.log(typeof symbol1);
console.log(symbol1 === symbol2);
```

---
# Palabras reservadas
![[Pasted image 20240413152207.png]]

Ejemplo de nombres de variables: 
```JavaScript 
let _objetos$123 = 123;

let precio99_99 = 123;

let jugadorConPuntajeMasAlto = 'Angel';
```

---
# Arreglos

Son un objeto muy parecido a una lista de información, que contiene un grupo de elementos
> Usualmente, esa información dentro del arreglo es del mismo tipo de dato...

Los arreglos no son más que bloques de información apilados, es decir, tomando el ejemplo de un estante de libros, el estante es el arreglo y cada libro es un valor de tipo dato, el cual puedes acceder simplemente tomándolo, pero en JavaScript sería accediendo a él por medio de su **índice**.

## Inicializando arreglos 

### Estricta
Existe una forma que cotidianamente en lenguajes de programación de tipado fuerte se utiliza para inicializar un arreglo, que también existe en JavaScript:
```JavaScript
const arr = new Array(10);
```
Como resultado, al imprimir en consola tendremos:
![[Pasted image 20240414113235.png]]
Lo que aquí podemos ver es que la representación de un arreglo son las `[ ]` esto siempre será así, cada vez que veamos las llaves `[ ]` significa que es un arreglo.

Aunque esto es válido, no es usual verlo, pero no lo descartes porque podría haber empresas que inicializar asi sus arreglos sea un estándar para ellos.

### Estándar 
Pero habitualmente se inicializa asi: 
```JavaScript
const arr = [];
```
Al imprimirlo en la consola se verá asi: 
![[Pasted image 20240414113935.png]]
Esto a diferencia de `new Array` se conoce como un arreglo dinámico, a lo que el arreglo puede tener un tamaño de elementos indefinido, que al ingresar información crecerá sin problemas, esto a que JavaScript es débilmente tipado.

## Uso de arreglos
```JavaScript
let videoJuegos = ['Mario 3', 'Megaman', 'Chrono Trigger'];
console.log({ videoJuegos });
```
Como resultado de la impresión: 
![[Pasted image 20240414114423.png]]
>Recordemos que "envolver" la variable que queremos imprimir con llaves `{ }` nos permite verlo como en la imagen.

El uso que se dio en el ejemplo anterior es que tenemos una "repisa" de videojuegos, que en realidad sería un arreglo de valores de cadena de textos (`String`).

## Acceder a un elemento de un arreglo
Pero, ¿Cómo podremos imprimir un elemento en específico? 

Como explicamos anteriormente existe el índice en los arreglos, como nosotros leeríamos de izquierda a derecha podríamos decir que **Mario 3** tiene la posición 1, **Megaman** tiene la posición 2, etcétera, pero con los arreglos sería más bien, **Mario 3** tiene la posición 0, **Megaman** tiene la posición 1 y asi sucesivamente

Ejemplo, si del arreglo `videoJuegos` necesito el primer elemento, entonces escribiríamos: 
```JavaScript
console.log(videoJuegos[0]); //Del arreglo de videojuegos me interesa la primera posicion
```
Como resultado: 
![[Pasted image 20240414115241.png]]

Recordemos que esto no solo sirve para imprimir, si queremos manipular el elemento en el arreglo lo podríamos hacer como si fuera un variable.

```JavaScript
videoJuegos[0] = "Luigi";
console.log(videoJuegos[0]);
```
Como resultado: 
![[Pasted image 20240414115520.png]]

## Dinamismo en los Arreglos de JavaScript

En otros lenguajes de programación que son de tipado fuerte, los arreglos solo pueden ser de un tipo de dato, es decir, un arreglo de cadena de caracteres (`Strings`) no puede tener un número en él, pero en JavaScript es diferente, sus arreglos son dinámicos.

Podemos llegar a realizar este tipo de arreglos:
```JavaScript
let arregloCosas = [
    true,
    123,
    'Fernando'
    , 1 + 2,
    function () { },
    () => { },
    { a: 1 },
    ['X', 'Megaman', 'Zero', 'Dr.Light', [
        'Dr.Willy'
        , 'Woodman']]
];
```

Expliquemos un poco lo que estamos viendo

Posición: 
- 0 - Es un booleano, con valor `true`
- 1 - Es un número con valor `123`
- 2 - Es una cadena de caracteres (`String`)con valor `Fernando`
- 3 - Es una operación aritmética con valor `1+2`
- 4 - Es una función
- 5 - Es una función flecha
- 6 - Es un objeto literal 
- 7 - Es un arreglo 
	- 0 - Es una cadena de caracteres (`String`) con valor `X`
	- 1 - Es una cadena de caracteres (`String`) con valor `Megaman`
	- 2 - Es una cadena de caracteres (`String`) con valor `Zero`
	- 3 - Es una cadena de caracteres (`String`) con valor `Dr.Light`
	- 4 - Es un arreglo 
		-  0 - Es una cadena de caracteres (`String`) con valor `Dr.Willy`
		-  1 - Es una cadena de caracteres (`String`) con valor `Woodman`

La lista anterior es una representación del los elementos que tenemos en el arreglo y el cómo podemos acceder en ellos, recordemos que el índice siempre empieza en 0, y por ello tendremos que tener en mente al manipular arreglos.

El tema principal es ver el dinamismo que tiene los arreglos que no están atados o estrictamente obligados a usar solo un tipo de dato. 

```JavaScript
console.log({ arregloCosas });
// Imprimir el valor de true que viene del arreglo arregloCosas
console.log(arregloCosas[0]);
// Imprimir el valor de 'Fernando'
console.log(arregloCosas[2]);
// Imprimir el valor de 'Dr.Light'
console.log(arregloCosas[7][3]);
//  Imprimir el valor Woodman
console.log(arregloCosas[7][4][1]);
```
En la vida real es muy difícil ver una búsqueda de arreglos como al imprimir el valor `woodman`

## Métodos de los arreglos

Los arreglos en JavaScript proporcionan una serie de métodos integrados que permiten realizar diversas operaciones en los elementos del arreglo. Estos métodos están disponibles para cualquier arreglo que crees en JavaScript.

Por ejemplo, cuando veas una palabra seguida de un punto después de un arreglo en JavaScript, es probable que estés accediendo a alguno de sus métodos. Estos métodos pueden incluir:

- `push()`: Agrega uno o más elementos al final del arreglo.
- `pop()`: Elimina el último elemento del arreglo y lo devuelve.
- `shift()`: Elimina el primer elemento del arreglo y lo devuelve.
- `unshift()`: Agrega uno o más elementos al principio del arreglo.
- `slice()`: Devuelve una copia superficial de una porción del arreglo en un nuevo arreglo.
- `splice()`: Cambia el contenido de un arreglo eliminando elementos existentes y/o agregando nuevos elementos.
- `forEach()`: Ejecuta una función dada una vez por cada elemento del arreglo.
- `map()`: Crea un nuevo arreglo con los resultados de llamar a una función dada en cada elemento del arreglo.
- `filter()`: Crea un nuevo arreglo con todos los elementos que pasan la prueba implementada por la función proporcionada.
- `reduce()`: Aplica una función a un acumulador y a cada valor de un arreglo (de izquierda a derecha) para reducirlo a un único valor.

Pero hagamos unos ejemplos: 
### Tamaño del arreglo `.length`
```JavaScript
let juegos = ['Zelda', 'Mario', 'Metroid', 'Chrono'];
console.log('Largo: ', juegos.length);
```
El método `.length` permite saber el tamaño total del arreglo, como resultado:
![[Pasted image 20240414165137.png]]

### Operaciones aritméticas en el índice
Dentro de las llaves `[ ]` podemos realizar operaciones aritméticas para calcular el índice deseado, por ejemplo:

¿Cómo podemos acceder al primer elemento de un arreglo con operaciones aritméticas? 
```JavaScript
let primero = juegos[2 - 2];
console.log('Primero: ', primero);
```

También dado que ya conocemos como calcular el tamaño total de un arreglo
¿Cómo podemos acceder al último elemento de un arreglo sabiendo que los arreglos empiezan en 0? 
```JavaScript
let ultimo = juegos[juegos.length - 1];
console.log('ultimo: ' + ultimo);
```

### Recorrer un arreglo, elemento por elemento `.forEach()`

En JavaScript, `forEach()` es un método que se utiliza para iterar sobre cada elemento de un arreglo y ejecutar una función proporcionada una vez por cada elemento. Esto significa que puedes realizar alguna operación específica en cada elemento del arreglo sin necesidad de utilizar un bucle `for` tradicional.

Tomemos el siguiente ejemplo:
```JavaScript
juegos.forEach((elemento, indice, arr) => {
    console.log(elemento, indice, arr);
});
```

- **Arreglo (Array)**: En este caso, `juegos` es el arreglo sobre el cual se está iterando. Cada elemento del arreglo será pasado a la función proporcionada uno por uno.
    
- **Función de devolución de llamada (Callback Function)**: La función que se pasa como argumento a `forEach()` se ejecutará una vez por cada elemento del arreglo. En tu código, `(elemento, indice, arr) => { ... }` es la función de devolución de llamada. Esta función toma tres parámetros:
    - `elemento`: Representa el valor del elemento actual del arreglo en cada iteración.
    - `indice`: Representa el índice del elemento actual en el arreglo.
    - `arr`: Es una referencia al arreglo sobre el cual se está iterando (en este caso, `juegos`).
    
- **Cuerpo de la función**: Es el bloque de código dentro de `{}` que se ejecutará en cada iteración. En tu caso, el código `console.log(elemento, indice, arr);` imprimirá en la consola el valor del elemento actual (`elemento`), su índice (`indice`) y el arreglo completo (`arr`).

Como resultado:
![[Pasted image 20240414171008.png]]
### Ingresar un elemento al final del arreglo `.push`
El `.push` ingresa un elemento al final de arreglo, y retorna el nuevo tamaño total del arreglo
```JavaScript
// Colocar al final del arreglo
let nuevaLongitud = juegos.push('F-Zero');
console.log({ nuevaLongitud, juegos });
```
Como resultado: 
![[Pasted image 20240414171632.png]]

### Ingresar un elemento al inicio del arreglo `.unshift`
El `.unshift` ingresa un elemento al inicio del arreglo y retorna el nuevo tamaño total del arreglo
```JavaScript
nuevaLongitud = juegos.unshift('Fire Emblem');
console.log({ nuevaLongitud, juegos });
```
Como resultado: 
![[Pasted image 20240414171904.png]]

### Borrar el último elemento de un arreglo `.pop`
El `.pop` borra el último elemento de un arreglo, y retornara `undefined` si el arreglo esta vacio de lo contrario retornara el elemento borrado
```JavaScript
// Borrar el ulitmo elemento
let juegoBorrado = juegos.pop()
console.log(juegoBorrado);
```
Como resultado:
![[Pasted image 20240414172205.png]]

### Borrar un elemento en una posición especifico `.splice`
Remueve elementos de un arreglo, pero para ello tiene que ingresar 2 datos, el primero sería el índice, es decir, en la posición donde empezara removiendo elementos, y el segundo dato es el número de elementos a remover, el retorno del método es un nuevo arreglo de los elementos eliminados.

El arreglo actual es: 
```JavaScript
let juegos = ['Fire Emblem', 'Zelda', 'Mario', 'Metroid', 'Chrono'];
```
Eliminaremos dos elementos que serán Zelda y Mario:
```JavaScript
let pos = 1;
let juegosBorrados = juegos.splice(pos, 2);
console.log({ juegosBorrados, juegos });
```
Como resultado, en la variable `juegosBorrados` tenemos:![[Pasted image 20240414173619.png]]
Y en el arreglo juegos tenemos: 
![[Pasted image 20240414173641.png]]

---

# Objetos literales
Los objetos literales son una extensión o forma de llamar a los objetos que no son creados a partir de una clase, esto conlleva que en JavaScript los objetos literales se refiere a la creación de los mismos de manera manual.

>**Recuerda** Si no es un primitivo, es un objeto.

Cuando nos adentramos en el mundo de la programación orientada a objetos, es esencial entender el concepto de objetos. Este paradigma nos permite codificar de una manera que refleje la estructura y comportamiento de entidades del mundo real. Por ejemplo, si necesitamos manejar datos personales de usuarios, en lugar de crear una variable para cada dato, podemos crear un objeto que represente a una persona. Este objeto contendrá propiedades como nombre, código, estado vital, edad, entre otros. Esta forma de organizar el código nos permite una gestión más eficiente y coherente de la información, facilitando el mantenimiento y la comprensión del sistema en su conjunto.

**Sintaxis básica de un objeto literal**
```JavaScript
let personaje = {};
```
En JavaScript, las llaves `{ }` se utilizan para denotar tanto objetos como bloques de código. Cuando se utilizan para definir una estructura de datos, como en `{ clave: valor }`, representan un objeto. Sin embargo, cuando se utilizan para delimitar un bloque de código, como en un condicional `if` o un bucle `for`, indican el inicio y el final de dicho bloque. Es importante tener en cuenta el contexto en el que se utilizan las llaves para interpretar correctamente su significado en el código.

Veámoslo con un ejemplo de persona, pero para hacerlo interesante será un superhéroe: 
```JavaScript
const personaje = {
    nombre: 'Tony Stark',
    codeName: 'Ironman',
    vivo: false,
    edad: 40,
    coords: {
        lat: 34.034,
        lng: -118.70
    },
    trajes: ['Mark I', 'Mark V', 'Hulkbuster'],
    direccion: {
        zip: '108080, 90265',
        ubicacion: 'Malibu, California'
    },
    'ultima pelicula': 'Infinity War'
};
```
La estructura de un objeto literal se compone de pares `propiedad: valor`. Esto se asemeja mucho a la idea de atributos o características de un objeto. 

Por ejemplo, si consideramos un superhéroe como objeto, sus propiedades podrían ser características como nombre, alias, poderes, y el valor de cada una de estas propiedades sería el dato específico asociado a esa característica para ese superhéroe en particular. Esta estructura facilita la organización y manipulación de datos en forma de objetos, lo que es fundamental para el desarrollo de aplicaciones en JavaScript.

En el ejemplo también puedes ver que puedes anidar arreglos y objetos, esto por la facilidad del tipado de JavaScript

```JavaScript
console.log("personaje");
```
Como resultado: 
![[Pasted image 20240415182336.png]]
La forma en la cual se ordena por defecto es de manera alfabética.
## Accediendo a los datos del objeto
Para manipular los datos de un objeto en JavaScript, es necesario entender cómo acceder a sus propiedades y métodos. Una forma común de hacerlo es mediante el uso del punto `(.)`. 

Por ejemplo, si tenemos un objeto `persona` con una propiedad `nombre`, podemos acceder a ese valor utilizando `persona.nombre`. Esto nos permite tanto obtener como modificar el valor de esa propiedad. Es importante tener en cuenta esta sintaxis para trabajar de manera efectiva con objetos en JavaScript.

Ejemplo: 
```JavaScript
console.log("Nombre", personaje.nombre);

console.log("Nombre", personaje['nombre']);

console.log("Edad", personaje.edad);
```
Como resultado: 
![[Pasted image 20240415182605.png]]
Como podrás ver en el código, hay una impresión que se hizo como si fuera un arreglo. 

En JavaScript, además de acceder a las propiedades de un objeto utilizando el operador de punto `(.)`, también podemos hacerlo utilizando la sintaxis de corchetes `[ ]`. Esto es útil cuando el nombre de la propiedad está almacenado en una variable o cuando queremos acceder dinámicamente a una propiedad.
Ejemplo: 
```JavaScript
const x = 'vivo';
console.log('Vivo', personaje[x]);
```
Como resultado:  
![[Pasted image 20240415183005.png]]

## Accediendo a objetos dentro del objeto
```JavaScript
console.log("Coors", personaje.coords);
console.log("Coors", personaje.coords.lat);
```
Como resultado:
![[Pasted image 20240415183119.png]]


## Accediendo a arreglos dentro del objeto
```JavaScript
console.log('No. Trajes', personaje.trajes.length);
console.log('Ultimo Trajes', personaje.trajes[personaje.trajes.length - 1]);
```
Como resultado: 
![[Pasted image 20240415183226.png]]

## Propiedad con nombres con espacio
En el ejemplo del objeto literal, si queremos utilizar nombres de propiedad largos, lo podemos hacer con camelCase o como la siguiente forma:
`'ultima pelicula': 'Infinity War'`

Y para acceder a él tendremos que escribirlo de la siguiente forma:
```JavaScript
console.log("Ultima Pelicula", personaje['ultima pelicula']);
```
Como resultado:
![[Pasted image 20240415183508.png]]

## Borrar Propiedad
```JavaScript
// Borrar Propiedad
delete personaje.edad;
console.log(personaje);
```
## Trabajar el objeto como si fuera arreglos

```JavaScript
const entriesPares = Object.entries(personaje);
console.log(entriesPares);
```
## Crear una nueva propiedad en el objeto
```JavaScript
personaje.casado = true
console.log(personaje);
```
## Bloquear cambios en el objeto incluido clave:valor

Necesito que pueda cambiar objetos, cambiarlo a `const` no bloquea la creación de nuevas propiedades, Si lo hace, pero no es como nosotros lo pensamos, lo que bloquea es que no puedas cambiar el tipo de dato, en este caso un objeto

Tendremos que hacer:
```JavaScript
Object.freeze(personaje);
```
Está haciendo "congela" el objeto tal cual está antes de la instrucción.

```JavaScript
personaje.dinero = 100000000000000000000;// No crea la propiedad

personaje.casado = false; // No cambia por la instruccion Objet.freeze

personaje.direccion.ubicacion = 'Mexico, City'; // Si cambia porque, cambia el objeto hijo(direccion) y no el objeto padre (personaje)

console.log(personaje); // No veremos la nueva propiedad dinero
```
## Listado de propiedades y valores (convertir en arreglos)
```JavaScript
// Necesito unlistado de propiedades del objeto
const propiedades = Object.getOwnPropertyNames(personaje);
// Necesito unlistado de valores del objeto
const valores = Object.values(personaje);
console.log([valores]);
console.log({ propiedades });
```
Como resultado: 
![[Pasted image 20240415184119.png]]

---

# Funciones

Las funciones son bloques de código reutilizables que pueden ser llamados para ejecutar una tarea específica.

## Función General
Ejemplo saludar:
```Javascript
function saludar(){
	console.log('Hola Mundo');
}
```

Para ejecutarla o también llamada "invocarla" se utiliza: 
```JavaScript
saludar();
```

> **Buenas Prácticas** : la forma en la que debemos escribir el código es primero la función y después la ejecución


## Función anónima
Ejemplo saludar:
```JavaScript
const saludar = function(){
	console.log('Hola Mundo');
}
```
Para ejecutarla o también llamada "invocarla" se utiliza: 
```JavaScript
saludar();
```
## Función Flecha
Ejemplo saludar: 
```JavaScript
const saludar = () => {
	console.log('Hola Mundo');
}
```

Para ejecutarla o también llamada "invocarla" se utiliza: 
```JavaScript
saludar();
```

## Argumentos
Como hemos visto hasta ahora, las funciones nos permite reutilizar fragmentos de código.

Pero las funciones tiene más utilidades o herramienta como los argumentos, son una herramienta esencial en JavaScript que nos permiten pasar información a las funciones para que puedan realizar tareas específicas con esos datos. 

Cuando definimos una función, podemos especificar parámetros entre los paréntesis que actúan como contenedores para los argumentos que se pasarán a la función cuando se llame.

Imagina que a la función saludar quieres que salude a alguien por su nombre, entonces la forma en que puedes hacer esto dinámicamente es que al invocar la función le agregues el nombre de la persona: 

```JavaScript
function saludar(nombre){
	console.log('Hola '+ nombre)
}
```

Al invocarla le pondrás el nombre al cual saludar:
```JavaScript
saludar('Juan');
saludar('Angel');
```
Como resultado de ambas ejecuciones o invocaciones es: 
![[Pasted image 20240415202503.png]]

¿Y puedes enviar más de un argumento? 
Si, y tal cual el orden que "vienen", tendrás que tomarlos en cuenta, es decir, como si de un arreglo enviaras la posición en la que se encuentran es importante, por ejemplo: 

Si a la función:
```JavaScript
function saludar(nombre){
	console.log('Hola '+ nombre)
}
```

Le enviamos más de un argumento: 
```JavaScript
saludar('Fernando', 40, true, 'Costa Rica');
```
El resultado sería: 
![[Pasted image 20240415202907.png]]

¿Por qué no afecto el tener más de un argumento?, porque dichos argumentos extras no los definimos en la función, lo cual para JavaScript no significo un error o diferencia, simplemente lo entiende como que es información que no vas a utilizar

¿Pero qué paso con dichos argumentos?, los argumento aún existen, la [[#Función General]] y la [[#Función General]] tiene una variable local llamada `arguments` la cual almacena los argumento que envía una invocación de función.

```JavaScript
function saludar(nombre){
	console.log(arguments) // Argumentos enviados a la funcion
	console.log('Hola '+ nombre)
}
saludar('Fernando', 40, true, 'Costa Rica');
```
Como resultado: 
![[Pasted image 20240415212938.png]]

¿Te acuerdas de que era importante el orden?, bueno, la importancia es que los argumentos son tomados tal cual es un arreglo, el nombre que les des y la posición que los pongas en los corchetes  `( )` de la función, es el orden tal cual fueron enviados al invocar la función.

> **Nota** la función flecha no cuenta con la variable local `arguments`
## Retorno (`return`)
En JavaScript, `return` es una declaración que se utiliza dentro de una función para devolver un valor.

En términos simples permite regresar algo de una función, recuerdas como en los métodos de los [[#Objetos literales]] regresaban valores, si queríamos borrar un elemento nos regresaba el elemento borrado, pues asi funciona el retorno (`return`) en las [[#Funciones]].

Ejemplo tenemos la función anterior de saludar: 
```JavaScript
function saludar(nombre) {
	console.log('Hola '+nombre);
	return 1;
}
saludar('Juan');
```
El resultado ya lo conocemos: 
![[Pasted image 20240415220105.png]]
Ahora el retorno de la función se aloja en la invocación `saludar()`, entonces lo guardamos en una variable e imprimimos esa variable:
```JavaScript
const retornoDeSaludar = saludar('Juan');
console.log({retornoDeSaludar});
```
Como resultado
![[Pasted image 20240415220347.png]]

>**Nota** Cuando una función alcanza una instrucción `return`, la ejecución de la función se detiene inmediatamente y se devuelve el valor especificado.

Puedes retornar lo que sea como arreglos: 
```JavaScript
function saludar(nombre) {
    return [1, 2];
    // Esto nunca se va a ejecutar
    console.log('Soy un codigo que esta despues del return');
}
```

Puedes retornar objetos:
```JavaScript
function saludar(nombre) {
    return {nombre: 'Tony Stark'};
}
```

Puedes retornar operaciones aritméticas:
```JavaScript
function sumar(a, b) {
    return a + b;
}
```
Aplica lo mismo en funciones flecha:
```JavaScript
const sumar2 = (a, b) => {
	return a + b;
}
```

## Retornando funciones con una única operación
Cuando una función solo tiene una operación y la operación se encuentra en el `return`, se puede resumir de la siguiente manera:

```JavaScript
const sumar2 = (a, b) => a + b;
```

Esto de manera genérica puede ser utilizado para obtener el siguiente ejemplo:
```JavaScript
// Funcion flecha
const getAleatorio = () => Math.random();
```
# Pro Tips Funciones

En este apartado vamos a ver tips/ consejos al codificar 

## Retorno de objetos - Property Shorthand
En JavaScript podemos retornar objetos de la siguiente forma: 
```JavaScript
function crearPersona(nombre, apellido) {
 return {
    nombre: nombre,
    apellido: apellido
}
```
Estamos creando un objeto a partir de los datos que nos envíe la "invocación" de la función:
```JS
const persona = crearPersona('John', 'Smith');
```
Como resultado: 
![[Pasted image 20240416163231.png]]

Pero podemos ahorrarnos código de la siguiente manera:
```JavaScript
function crearPersona(nombre, apellido) {
 return {nombre,apellido}}
```
El resultado es el mismo: 
![[Pasted image 20240416163231.png]]

JavaScript nos permite asignar el nombre argumento como propiedad del objeto, y el valor del argumento como valor del objeto.

Esta característica se llama "**property shorthand**" y es una forma abreviada de escribir propiedades de objeto en JavaScript cuando el nombre de la propiedad es igual al nombre de la variable que contiene su valor. Esto hace que el código sea más conciso y legible.

### Función flecha
¿Cómo podríamos utilizar él [[#Retorno de objetos - Property Shorthand|Property Shorthand]] como lo hicimos con [[#Retornando funciones con una única operación]]?

```JS
const crearPersona = (nombre, apellido) => ({ nombre, apellido })
```
Cuando retornemos un objeto en una función flecha de una única operación, hay que poner los paréntesis `( )` esto porque de no hacerlo, la función flecha tomaría esto como el cuerpo de la función y no como el retorno de la operación.

## Argumentos en Funciones Flecha
Como sabemos, las funciones flecha no tienen acceso a la variable local `arguments`, que almacena los argumentos que se le envían a una función. Sin embargo, existe una forma alternativa de acceder a los argumentos utilizando parámetros y el operador `rest`.

El parámetro `rest` en JavaScript se refiere a una característica que permite a una función aceptar un número variable de argumentos como un `array`. Esto se logra mediante la sintaxis de tres puntos (`...`) seguido por el nombre del parámetro

```JS
const imprimeArgumentos = (...args) => {
    console.log(args );
}
const argumentos = imprimeArgumentos(10, true, false, 'Fernando', 'Hola')
```
Como resultado:
![[Pasted image 20240416165820.png]]

Los tres puntos `(...)` antes del nombre del parámetro `args` indican un parámetro `rest`. Esto significa que todos los argumentos pasados a la función flecha se recopilan en un `array`, con cada argumento como un elemento individual del `array`

### Consideraciones
- Después del parámetro `Rest` (...) no puede haber más argumentos
- Para utilizar el primer parámetro recibido en la función (por ejemplo, "edad" en este caso) como un valor independiente y los demás argumentos como un arreglo, se debe seguir la siguiente sintaxis:
```JS
const imprimeArgumentos = (edad, ...args) => {
    console.log({ edad, args });
}
const argumentos = imprimeArgumentos(10, true, false, 'Fernando', 'Hola')
```
Como resultado: 
![[Pasted image 20240416170714.png]]

## Desestructuración de Arreglos (`arrays`)
Pongamos el ejemplo anterior:
Tenemos una función: 
```JS
const imprimeArgumentos = (edad, ...args) => {
    console.log({ edad, args });
}
```
Tenemos la invocación:
```JS
imprimeArgumentos(10, true, false, 'Fernando', 'Hola')
```
Como resultado: 
![[Pasted image 20240416170714.png]]

Recordemos que en este punto hemos decidido tomar el primer valor `10` y asignarlo como `edad` en nuestra función. 

¿Qué pasaría si yo quiero retornar los argumento y reutilizarlos en mi código individualmente?
Tendríamos que hacer algo asi:
```JS
//funcion
const imprimeArgumentos = (edad, ...args) => {
    console.log({ edad, args });
    return args;
}
// asignamos a una varible el retorno de la invocacion
const argumentos = imprimeArgumentos(10, true, false, 'Fernando', 'Hola')
//Asignado variables
const casado = argumentos[0];
const vivo = argumentos[1];
const nombre = argumentos[2];
const saludo = argumentos[3];
```

Lo cual podemos ahorrarnos con la **Desestructuración de arreglos**:
```JS
const [casado, vivo, nombre, saludo] = imprimeArgumentos2(10, true, false, 'Fernando', 'Hola')
```

En JavaScript, la desestructuración es una técnica poderosa que nos permite extraer valores de arreglos o propiedades de objetos de forma rápida y sencilla. Cuando sabemos que una función u objeto devolverá un arreglo, podemos utilizar la desestructuración para asignar variables a cada uno de sus elementos de manera eficiente. Esto nos ahorra tiempo y hace que nuestro código sea más legible y conciso, ya que evita la necesidad de realizar asignaciones individuales para cada elemento.

Así que ahora esas variables existen en nuestro código y vamos a imprimirlas:
```JS
console.log({ casado, vivo, nombre, saludo });
```
Como resultado:
![[Pasted image 20240416172319.png]]

## Desestructuración de Objetos 
Trabajemos con el ejemplo anterior:
```JS
const crearPersona = (nombre, apellido) => ({ nombre, apellido })
```
Invoquemos, guardemos en una variable e imprimamos el resultado:
```JS
const persona = crearPersona('Fernando', 'Herrera');
console.log(persona);
```
Como resultado:
![[Pasted image 20240416172730.png]]

En JavaScript, la desestructuración de objetos es una técnica que nos permite extraer valores de un objeto y asignarlos a variables de manera rápida y directa. Cuando conocemos la estructura de un objeto y queremos acceder a sus propiedades de una manera más eficiente, la desestructuración es la herramienta adecuada. 

En lugar de acceder a cada propiedad del objeto de forma independiente, podemos declarar las variables que deseamos directamente, utilizando los nombres de las propiedades del objeto. Esto hace que nuestro código sea más claro y conciso, facilitando la lectura y comprensión del mismo.

Es decir, si nosotros queremos que del retorno de la función se cree variables únicas, tendremos que hacer una desestructuración , por ejemplo, si solo queremos hacer una variable única de apellido, solo tendremos que hacer: 
```JS
const { apellido } = crearPersona('Fernando', 'Herrera');

console.log({ apellido });
```
Como resultado:
![[Pasted image 20240416173108.png]]
Claramente antes de hacer la desestructuración tienes que saber que nombres de propiedades va a retornar

¿Qué pasaría si no quiero que se llame justamente como la propiedad que retorna? 
Bueno, puedes hacer: 
```JS
const { apellido: nuevoApellido } = crearPersona('Fernando', 'Herrera');
console.log({ nuevoApellido });
```
Como resultado: 
![[Pasted image 20240416173253.png]]

## Desestructuración de argumentos
En JavaScript, la desestructuración de argumentos es una técnica que nos permite extraer valores de un objeto o arreglo que se pasa como argumento a una función de una manera más concisa y legible.

Por ejemplo tenemos el siguiente objeto literal:
```JS
const tony = {
    nombre: 'Tony Stark',
    codeName: 'Ironman',
    vivo: false,
    edad: 40,
    trajes: ['Mark I', 'Mark V', 'Hulkbuster'],
};
```

Y crearemos una función la cual me permite imprimir valores de propiedades de un objeto: 
```JS
const imprimePropiedades = (personaje) => {
    console.log('nombre: ' + personaje.nombre);
    console.log('codeName: ' + personaje.codeName);
    console.log('vivo: ' + personaje.vivo);
    console.log('edad: ' + personaje.edad);
    console.log('trajes: ' + personaje.trajes);
}
imprimePropiedades(tony);
```
Esto nos crea demasiado código el cual podemos ahorrar y reutilizar de mejor manera la desestructuración de argumentos, de la siguiente forma: 

```JS
const imprimePropiedades = ({ nombre, codeName, vivo, edad = 15, trajes }) => {
    console.log({ nombre })
    console.log({ codeName })
    console.log({ vivo })
    console.log({ edad })
    console.log({ trajes })
}
```
Esto nos permite recibir el objeto, y asignar de mejor manera el cómo vamos a utilizar cada propiedad.

Incluso nos permite poner funcionalidad, como la de;

¿Qué pasaría si la propiedad edad viene vacía o indefinida?
Al poner en los argumentos `edad=15` hace dicha verificación de que, si viene vacía o indefinida entonces tendrá el valor de 15, de lo contrario si viene definida tomará el valor que venga en el objeto.
