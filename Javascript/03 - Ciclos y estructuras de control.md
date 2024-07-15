# Valor, referencia y romper la referencia
Tomemos el siguiente ejemplo: 
```JavaScript
let a = 10;
let b = a;
a = 30;

console.log({ a, b });
```
Como resultado:
![[Pasted image 20240416193449.png]]
Es el resultado esperado.

Cuando trabajamos con primitivos cualquier tipo de asignación como `a = 30`, o cuando lo mandamos a una función como un argumento lo estamos mandando por valor, es decir, no importa si transformamos la variable o le asignamos otra cosa, no estamos afectando el mismo lugar en memoria, estamos pasando únicamente el valor.

Es un resultado obvio, no?, ¿entonces para que enseñarlo?
```JS
let juan = {
    nombre: 'Juan',
}
let ana = juan ; 
ana.nombre = 'Ana'
console.log({ juan, ana });
```
¿Qué pasa si ejecutamos este código? ⬆️

Tenemos el siguiente resultado:![[Pasted image 20240416193817.png]]
Aquí paso algo muy raro, ¿por qué si estoy cambiando únicamente `ana.nombre = 'Ana'` el objeto `juan` también cambio su nombre? 
#### ¿Cómo funciona JavaScript?
En JavaScript todos los objetos son pasados por referencia, es decir, todo el tiempo apuntan al mismo lugar en memoria, cuando hacemos `let ana = juan` y cambiamos la propiedad nombre `ana.nombre = 'Ana'` no estamos haciendo referencia a un nuevo objeto llamado `ana`, sino que estamos apuntando al objeto `juan`.

**¿Por qué pasa esto?** 
En JavaScript todos los primitivos son pasados por valor, y todos los objetos son pasados por referencia.

**Recordemos**
En JavaScript todo en un objeto exceptuando los primitivos

## ¿Cómo rompemos la referencia en JavaScript?
El "`spread`" en JavaScript es un operador que se utiliza para copiar los elementos de un iterable (como un `array` o un objeto similar a un `array`) en otro lugar. Se representa con tres puntos consecutivos: `...`.

Su función principal es expandir un iterable en lugares donde se esperan múltiples argumentos o elementos. Por ejemplo, en la creación de un nuevo `array` o al llamar a una función con múltiples argumentos.

Tomando el ejemplo anterior que estamos manipulando un objeto literal:
```JS
let juan = {
    nombre: 'Juan',
}
let ana = {...juan}; //Spread - Separa los elementos y por ende rompe la referencia
ana.nombre = 'Ana'
console.log({ juan, ana });
```
Como resultado: 
![[Pasted image 20240416194740.png]]

Pongamos otro ejemplo:
```JS
const cambiarNombre = (persona) => {
    persona.nombre = 'Tony';
    return persona;
}

let peter = { nombre: 'Peter', };
let tony = cambiarNombre(peter);

console.log({ peter, tony });
```
¿Cuál crees que es el resultado código? 
En este código no estamos utilizando el método `spread`, entonces el resultado es: 
![[Pasted image 20240416195153.png]]

Entonces, ¿Dónde pondrías el método `spread`?
```JS
const cambiarNombre = (persona) => {
    persona.nombre = 'Tony';
    return persona;
}

let peter = { nombre: 'Peter', };
// ----------------------------------
let tony = cambiarNombre({...peter}); // SPREAD
// ----------------------------------
console.log({ peter, tony });
```
Tomando en cuenta el ejemplo anterior, la respuesta sería cuando enviamos el objeto a la función. 

Esto está bien, es correcto, pero 
- ¿Qué pasaría si tienes más objetos que van a pasar por esa función?
- ¿A todos los objetos tendrás que ponerle el `spread`?

Por ello la respuesta ideal sería: 
```JS
const cambiarNombre = ({...persona}) => { //SPREAD en los argumentos de la funcion
    persona.nombre = 'Tony';
    return persona;
}

let peter = { nombre: 'Peter', };
let tony = cambiarNombre(peter);
console.log({ peter, tony });
```
El operador `spread` en el argumento de la función
## Romper la referencia en arreglos
**Antes del `spread`:**
```JS
const frutas = ['Manzana', 'Pera', 'Pina'];

const otrasFrutas = [frutas];

otrasFrutas.push('Mango');
console.table({ frutas, otrasFrutas });
```
Como resultado: 
![[Pasted image 20240416200551.png]]

**Con `spread`:**
```JS
const frutas = ['Manzana', 'Pera', 'Pina'];

const otrasFrutas = [...frutas];

otrasFrutas.push('Mango');
console.table({ frutas, otrasFrutas });
```
Como resultado:
![[Pasted image 20240416200352.png]]
### Diferencias entre operado `rest(...)=>{ }` y `spread(...)`

El operador `rest` y el operador `spread` son ambos representados por tres puntos consecutivos (`...`) en JavaScript, pero tienen propósitos diferentes.

- **Spread (`...`)**: Se utiliza para descomponer un iterable (como un `array`) en elementos individuales. Por ejemplo, puedes usarlo para expandir los elementos de un `array` cuando pasas argumentos a una función o cuando creas un nuevo `array` combinando múltiples arrays.

- **Rest (`...`)**: Se utiliza en la definición de una función para recoger todos los argumentos restantes en un `array`. Esto permite manejar una cantidad variable de argumentos en una función sin necesidad de especificar cada uno de ellos individualmente.

---

# `If` y `Else`
Estructura de control, hasta este momento hemos visto que el código ya no es del todo secuencial, pero en cuestión de control como "Quiero que esto se ejecute sí…" 

La estructura básica de if-else en JavaScript se utiliza para tomar decisiones basadas en condiciones.

```JavaScript
// "if" es una declaración condicional que ejecuta un bloque de código si una condición especificada es verdadera. 
if (condición) { 
	// Este bloque de código se ejecuta si la condición es verdadera. 
} else { 
	// Este bloque de código se ejecuta si la condición es falsa. 
}
```

La **condición** de que si entra al "scoop" es si es verdadero, de lo contrario saltaría al `else`

Ejemplo
```JavaScript
let a = 5;
if (a > 10) {// undefinded , null , una asignacion
    console.log('A es mayor a 10');
} else {
    console.log('A es menor que 10');
}
```
El resultado esperado es "A es menor que 10", porque claramente 5 no es mayor que 10

Pero si a `let a = 15` entonces el resultado es: 
![[Pasted image 20240418134755.png]]

Pero, ¿Que pasa si ponemos 10?
![[Pasted image 20240418134925.png]]
Esto porque recordemos que en la **condición** solo recibirá `true` o `false`
¿Entonces 10 es mayor que 10 no es una condición verdadera?
No, 10 no es mayor que 10 es igual, por ende es falsa.
Solución: `if( a>= 10)` "5 es mayor o igual a 10"

Existe algo también que se llama anidamiento de `if(){}else if(){}`
```JS
const hoy = new Date();
let dia = hoy.getDay(); // 0: Domingo, 1:Lunes, 2: martes ...
console.log(hoy);
console.log({ dia });
```
Expliquemos un poco lo que estamos viendo antes de entrar el anidamiento.
-  `new Date()` Es un objeto lo cual al llamarlo retorna un objeto, entonces lo asignamos a una constante llamada `hoy`:                                     ![[Pasted image 20240418135902.png]]
- `hoy.getDay()` Es un objeto lo cual al llamarlo retorna un número, entonces lo asigna a una variable llamada `dia`

Estos objetos como `Date()` y `getDay()` vienen del lenguaje JavaScript, esto puede variar en otros lenguajes

`.getDay( )` retorna números, los cuales representa los días de la semana, se leen de la siguiente manera:
0: Domingo, 1: Lunes, 2: Martes, 3: Miércoles, 4: Jueves, 5: Viernes, 6: Sábado

Entonces, ¿como podríamos imprimir por medio del número de la variable `dia` el nombre del día de la semana? 
```JS
if (dia === 0) {
    console.log('Domingo');
} else if (dia === 1) {
    console.log('Lunes');
}
else if (dia === 2) {
    console.log('Martes');
}
```

Pero a esta solución existe maneras más fáciles de resolverlo:
```JS
// Sin usar If Else, o Switch, unicamnete objetos y arreglos
// Imprimir el dia de la semana:
dia = 3;// 0: Domingo, 1:Lunes, 2: martes ...

// Arreglos
let diaSemana = ['Domingo', 'Lunes', 'Martes', 'Miercoles', 'Jueves ', 'Viernes', 'Sabado']
console.log(diaSemana[dia]);

// Objetos
let diasDeLaSemana = {
    0: 'Domingo',
    1: 'Lunes',
    2: 'Martes',
    3: 'Miercoles',
    4: 'Jueves ',
    5: 'Viernes',
    6: 'Sabado'
}
console.log(diasDeLaSemana[dia] || 'No Valido');
```
Como resultado: 
![[Pasted image 20240418140934.png]]

---
# Lógica Booleana

La lógica booleana de forma sencilla es el uso de los operadores lógicos dentro de condicionales o asignaciones en la programación, no todos los lenguajes de programación se pueden utilizar, pero en el caso de JavaScript es un uso muy común y puede resumir código de manera eficiente, pero lo importante aquí es que tienes que saberlo leer.

![[Pasted image 20240418184649.png]]

La tabla anterior explica los operados lógicos que no son aritméticos, estos tienen un uso lógico cuando estamos programando.

Lógica booleana, una manera de trabajar con valores booleanos.

### Negación Not `!`
```JS
console.warn(" Not o la negacion")
console.log(true); // true
console.log(!true); // false
console.log(!false); // true
console.log(!regresaFalse());
```
### And `&&`
```JS
console.warn("And") // true si todos los valores son verdaderos
console.log(true && true); // true
console.log(true && false); // false
console.log('===============');
console.log(regresaFalse() && regresaTrue());// false
console.log(regresaTrue() && regresaFalse());// false
console.log('========&&=======');
regresaFalse() && regresaTrue()
```
### OR `||`
```JS
console.warn('OR');// true,por lo menos si una codicion es true
console.log(true || false) //true
console.log(false || false) // true
console.log('======== || =======');
console.log(regresaTrue() || regresaFalse());
console.log(regresaFalse() || regresaTrue());// true
```

### Asignaciones 
```JS
console.warn('Asignaciones')
const soyUndefidend = undefined;
const soyNull = null;
const soyFalso = false;

const a1 = true && 'Hola mundo' && 150; // En asignaciones de variable el AND && tomara el ultimo valor si las condiciones antes de el son true
const a2 = "hola" && 'Mundo' && soyFalso && true;// false
const a3 = soyFalso || 'Ya no soy falso'; // Ya no soy falso
const a4 = soyFalso || soyUndefidend || soyNull || 'Ya no soy falso de nuevo' || true; // Ya no soy falso de nuevo, No va a llegar a ejecutar el true
const a5 = soyFalso || soyUndefidend || regresaTrue() || 'Ya no soy falso de nuevo' || true; //true ,  no va a llegar a ejecutar el true

```

---
# Operador condicional ternario
El valor ternario es una estructura de control flexible, lo que se asemeja al `if-else`

Estructura de un `if-else`
```JS
if(condicion){
	// codigo si es true
}else{
	// codigo si es false
}
```

Estructura de un ternario
```JS
(condicion) ? /* codigo si es true */ : /* codigo si es false */;
```

## Formas de usar ternarios

### Asignaciones
```JS
let mensaje = (condicion) ? 'True' : 'False';
```
### Retorno de funciones
```JS
const elMayor = (a, b) => (a > b) ? a : b;
const tieneMembresia = (miembro) => (miembro) ? '2 Dolares' : '10 Dolares';
```
### Asignación en arreglos
```JS
const amigo = true;
const amigosArr = [
    'Peter',
    'Tony',
    'Dr.Strange',
    amigo ? 'Thor' : 'Loki',
    // (() => 'Nick Fury')()
    elMayor(10, 15)
]
```

### Anidamiento de ternarios
```JS
const nota = 85; // A+ A B+
const grado = nota >= 95 ? 'A+' :
		      nota >= 90 ? 'A' :
	          nota >= 85 ? 'B+' : 'F';
```

---
# Switch
La sentencia de control `switch`, dicta que puedes utilizar en varios casos una condición, es decir, tienes un `if` con múltiples condiciones.

La anatomía del `swtich`:
```js
switch (key) {
    case value:
        
        break;

    default:
        break;
}
```
Ejemplo: 
```js
const dia = 0; // 0:domingo
```
Evaluando con `switch`: 
```js
switch (dia) {
    case 0:
        console.log('Domingo');
        break;
    case 1:
        console.log('Lunes');
        break;
    case 2:
        console.log('Martes');
        break;
    default:
        console.log('No es lunes, Martes o Domingo');
        break;
}
```

El default sirve para evaluar un caso en el cual no está evaluando, es decir una excepción.

---
# Ciclos `While` `do-while`
Las estructuras de control cíclicas son aquella que nos servirá para poder recorrer varios datos o acciones en nuestro código.

Los ciclos se componen como los `if else` de una condición para poder entrar a ejecutar el código entre las llaves`{ }`. Entonces la condición de ser cierta entrar en el scoop (paréntesis `{ }`), de no ser ciertas, también existen algunos primitivos que por defecto serán denegadas por la condición. 
#### Condiciones Falsas:
- `undefined`
- `null`
- `false`
## `While`
Estructura básica:
```JS
while (condition) {
    // Codigo
}
```

Ejemplo:
```JS
const carros = ['Ford', 'Mazda', 'Honda', 'Toyota'];

let i = 0;
while (i < carros.length) {
     console.log(carros[i]);
     i++;
}
```

El punto es el recorrido de arreglos, para ello tendremos que recorrerlo desde la posición `0` hasta la última, y lo que pasaría es que cuando llegue a una posición que no tenga ningún valor, entonces al ser `undefined` saldría del scoop (paréntesis`{ }`).

Pero, ¿Cómo recorrerá uno por uno, es decir, como decirle la posición? 
Fuera del scoop (paréntesis`{ }`) se encuentra `let i = 0;` y dentro del scoop está `i++` que cada vez que se ejecute el valor `i` sumara un más `+1`.

Como resultado:
![[Pasted image 20240422202416.png]]
### Otra forma de recorrer sin operadores lógicos
También podemos recorrer otra forma, la cual no usemos [[#Lógica Booleana|Operadores lógicos]]:
```JS
const carros = ['Ford', 'Mazda', 'Honda', 'Toyota'];
let i = 0;
while (carros[i]) {
    console.log(carros[i]);
    i++;
}
```
Si notamos es el mismo recorrido, el cual podrá recorrer de la misma manera de la posición `0` hasta la posición que marque `undefined`.

¿Por qué la posiciones que tenga un valor los marca como true? 
En JavaScript, los índices de un `array` que no tienen un valor asignado se consideran `undefined`, lo que en un contexto booleano se evaluará como falso, mientras que los índices que tienen algún valor asignado (incluyendo `0`, `false`, o cualquier otro valor) se considerarán verdaderos.

### Palabras reservadas en ciclos

#### `Continue`
La palabra reservada `continue` permite "exentar", saltar, omitir, una ejecución de un ciclo.
```JS
const carros = ['Ford', 'Mazda', 'Honda', 'Toyota'];
let i = 0;
while (carros[i]) {
    if (i === 1) {
        // break;
        i++
        continue; // LLegaste hasta este punto pero sal del ciclo solo por este scope
    }
    console.log(carros[i]);
    i++;
}
```
El código anterior cumple una condición, lo que en lenguaje normal seria, si la variable `i` por ende carros en la posición `i` es igual a 1 entonces aumenta `i` y al llegar `continue` omite el resto del código dentro del ciclo, y vuelve a la condición del ciclo

Como resultado:
![[Pasted image 20240423002046.png]]

## `do while`
El ciclo `do while` a diferencia de `while` la evaluación de una condición (`condition`) se da al final del `scope`, esto significa que el código dentro del ciclo se ejecutara una vez, y si la condición es verdadera el ciclo empezará.

Estructura básica:
```JS
do{

}while (condition);
```

```JS
const carros = ['Ford', 'Mazda', 'Honda', 'Toyota'];

let j = 0;
do {
    console.log(carros[j]);
    j++;

} while (carros[j]);
```
Como resultado: 
![[Pasted image 20240423002533.png]]

---
# `for, for-in, for-of`
El ciclo `for` a diferencia del `while` y `do-while` contiene los 3 elementos básicos al hacer un ciclo correctamente.
 - `let index = 0`; La iniciación de la variable.
 - `index < array.length;` La condición para el ciclo.
 - `index++` El contador, la expresión que aumenta la variable.

Estructura Básica
```JS
for (let index = 0; index < array.length; index++) {
 //codigo   
}
```

Ejemplo:
```JS
const heroes = ['Batman', 'Superman', 'Mujer Maravilla', 'Aquaman']
for (let i = 0; i < heroes.length; i++) {
    console.log(heroes[i]);
}
```
El código anterior es únicamente la impresión del arreglo, como resultado:
![[Pasted image 20240423161401.png]]

## `for in`
El ciclo `for in` en el ejemplo continuación hace más simple el recorrido del arreglo, pero `for in` tiene sus límites:
```JS
const heroes = ['Batman', 'Superman', 'Mujer Maravilla', 'Aquaman']
for (let i in heroes) {
    console.log(heroes[i])
}
```
En este caso el `for in` recorrerá el arreglo, no es necesario la condición para ejecutar el ciclo, se ejecutará cuando el navegador llegue al código.

La variable `i` almacenará la posición del ciclo, por ello para imprimir el valor de la posición del arreglo lo haremos de la misma manera que `console.log(heroes[i])`.

Como resultado:
![[Pasted image 20240423162814.png]]

### `for...in` Se creó para objetos 
El bucle `for...in` en JavaScript está diseñado principalmente para iterar sobre las propiedades de un objeto. No está diseñado para recorrer matrices (arrays), aunque técnicamente sí es posible usarlo para recorrer las propiedades numéricas de una matriz. Sin embargo, esta práctica no se recomienda, ya que el bucle `for...in` no garantiza el orden en el que se iteran las propiedades, y puede causar problemas si se utilizan matrices con propiedades adicionales o si el orden de las propiedades es importante.

Para recorrer matrices, se recomienda utilizar el bucle `for` estándar o los métodos de iteración de matrices como `forEach()`, `map()`, `reduce()`, `filter()`, entre otros, que proporcionan una forma más segura y predecible de recorrer y manipular los elementos de una matriz.
### `for..in` Objetos
El bucle `for...in` en JavaScript es una forma de iterar sobre las propiedades de un objeto. Aquí tienes una explicación detallada:

Sintaxis básica:
```js

for (variable in objeto) {
  // código a ejecutar
}
```
- **Uso**:
    - `variable`: Es una variable que toma el valor de cada propiedad del objeto en cada iteración.
    - `objeto`: Es el objeto sobre el cual quieres iterar.
- **Funcionamiento**:
    - En cada iteración del bucle, la variable toma el nombre de una propiedad del objeto.
    - Puedes utilizar esta variable para acceder al valor de la propiedad correspondiente dentro del cuerpo del bucle.
Ejemplo:
```js
const persona = {
  nombre: 'Juan',
  edad: 30,
  ciudad: 'Madrid'
};

for (let propiedad in persona) {
  console.log(propiedad + ': ' + persona[propiedad]);
}
```
En este ejemplo:
propiedad tomará los valores 'nombre', 'edad' y 'ciudad' en cada iteración.
Persona[propiedad] accede al valor de la propiedad correspondiente en cada iteración.

![[Pasted image 20240423162942.png]]

## `for of` 
El bucle `for...of` en JavaScript es una forma de iterar sobre elementos iterables, como matrices, cadenas, conjuntos, mapas, etc.

Sintaxis básica:
```JS
for (variable of iterable) {
  // código a ejecutar
}
```

Ejemplo:
```js
const heroes = ['Batman', 'Superman', 'Mujer Maravilla', 'Aquaman'];
for (let heroe of heroes) {
    console.log(heroe)
}
```
El código anterior, a diferencia del `for` y `for in`, la variable héroe toma el valor dentro de la posición del arreglo por cada vuelta del ciclo, por ello al imprimirlo solo se necesita la variable héroe.
>El nombre la de la variable por buenas prácticas tiene que estar en singular 

Como resultado:
![[Pasted image 20240423164104.png]]
>No funciona en objetos

**Importante**
El bucle `for...of` en JavaScript está diseñado para iterar sobre elementos iterables, como matrices, cadenas, conjuntos y mapas, pero no sobre objetos en sí mismos. La razón de esto radica en la diferencia fundamental entre los objetos y los iterables.

- **Objetos**: En JavaScript, los objetos son colecciones de pares clave-valor, donde cada valor está asociado a una clave única. Pueden contener cualquier tipo de dato como valor y las claves pueden ser cadenas o símbolos.
    
- **Iterables**: Son objetos que implementan el protocolo de iterador, lo que significa que tienen un método `next()` que devuelve los elementos en secuencia. Ejemplos comunes de iterables incluyen matrices, cadenas, conjuntos y mapas.

---
