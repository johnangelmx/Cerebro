
# Problemática en JS
Vale hay que tener en cuenta que en el pasado JavaScript era un lenguaje que no estaba pensado para poder manejarse como los lenguajes convencionales de su tiempo como Java, sus características eran muy limitadas, pero los desarrolladores que usaban el lenguaje demostraban que querían usarlo como se usaría cualquier otro lenguaje.


## Programación orientada a objetos

Con esto en mente, veamos que es la programación orientada a objetos, la programación orientada a objetos es un paradigma de programación que su finalidad es usar los datos como objetos, al decir, como objetos se refiere a las características de un individuo.

Ejemplo:
```JS
pedro = {
nombre: 'pedro',
edad: 20,
soltero: true
}
```

A esto nos referimos con POO, esto porque como el ejemplo anterior podemos definir una persona en programación como objeto, y `nombre, edad, soltero` son propiedades que una persona tiene.

# POO en JavaScript

```JS
const fher = {
    nombre: 'Fernando',
    edad: 30,
    imprimir() {
        console.log(`Nombre: ${this.nombre} - edad: ${this.edad}`);
    }
}

const pedro = {
    nombre: 'Pedro',
    edad: 15,
    imprimir() {
        console.log(`Nombre: ${this.nombre} - edad: ${this.edad}`);
    }
}
```

En el ejemplo anterior implementamos el `POO` con los objetos literales y una vez implementado ingresamos una función la cual permite imprimir el nombre y la edad

>**Nota**: para poder acceder a una propiedad dentro del objeto literal tienes que ingresar la palabra reservada **`this`**. Ejemplo `${this.nombre}`

Al imprimir `fher.imprimir();` tenemos como resultado:
![[Pasted image 20240505074809.png]]

## ¿Clases en Emacs anteriores?
El problema del ejemplo anterior es que si tenemos más datos, sería repetitivo el agregar manualmente todos los objetos y si queremos ingresar más funciones, tendríamos que hacerlo en todos los objetos manualmente.

¿Ya entiendes el problema?
Esto se puede resolver con clases, pero ¿sabes como se intentaba resolver esto en JavaScript antes de la integración de clases en el lenguaje?

```JS
function Persona(nombre, edad) {
    console.log('Se ejecuto esta linea');
    this.nombre = nombre;
    this.edad = edad;
    this.imprimir = () => {
        console.log(`Nombre: ${this.nombre} - edad: ${this.edad}`);
    }
}
```
>La P mayúscula en el nombre de la función es indicativo para crear instancias.

A esto se le llama generador de instancias, en este punto te preguntarás esto es una función común y corriente, ¿cómo podría ser un generador de objetos? 

Si nosotros accedemos y guardamos en una variable esto:
```JS
const maria =  Persona('Maria', 18);
```
Como resultado, al imprimir `maria`:
![[Pasted image 20240505075853.png]]
y este es el resultado esperado dado que es una función sin `return`.


Como 
```JS
const maria = new Persona('Maria', 18);
```

En JavaScript, el uso de la palabra clave `new` crea un nuevo objeto, incluso si no estás utilizando una clase en el sentido tradicional de la programación orientada a objetos.
```JS
maria.imprimir();
```
Como resultado:
![[Pasted image 20240505080522.png]]

# Clases en JavaScript

