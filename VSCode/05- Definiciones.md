## Clases y Definiciones
VS Code nos permite, de manera rápida, en listar todas aquellas definiciones dentro de un código, esto a su vez es una herramienta fundamental al tener archivos con varias líneas de código 

```VSCode
Ctrl + P => luego escribir la @
Ctrl + Shift = O
```

Como recordaras en [[02- General#Mostrar la paleta de comandos|Mostrar la paleta de comandos]], Una de las funciones será enlistar todas las definiciones del archivo en el cual estés trabando, agregando un **@** podrás visualizar lo siguiente:

![[Pasted image 20230123062950.png]]

Pero si deseas tener una vista más detallada, solo tendrás que agregar **:** al **@** 
![[Pasted image 20230123063115.png]]

---

## Ir a La Línea
```VSCode
Ctrl + G
Ctrl + P => luego escribir la :
```

Como recordaras en [[02- General#Mostrar la paleta de comandos|Mostrar la paleta de comandos]], una de las funciones que podemos efectuar es la rápida ubicación en un número de línea específico, para ello solo es necesario poner **:** y este mismo nos pedirá el número al cual desplazarnos![[Pasted image 20230123063417.png]]

---

## Remplazar Definiciones
En VS Code tenemos un par de herramientas para poder manipular la edición de definiciones de manera conjunta, es decir, poder hacer el cambio de nombre de una definición, ya sea clase, función, método, etcétera y que a su vez el cambio sea automático en todo nuestro archivo.

Existe la herramienta de búsqueda en VS Code con el siguiente símbolo:![[Pasted image 20230123064556.png]]
El cual con el atajo `Ctrl + Shift + F` nos permite hacer la busque y remplazo de una definición en todo un archivo, o de manera global.

Pero existe actualmente un método más rápido en el cual el cambio puede ser de archivo o de manera global con una sola tecla: 
```VSCode
F2    Replace Symbol
```

El F2 Nos permite el cambio de nombre de manera local y global

Suponiendo el siguiente código: 
```typescript
import { SuperHeroe } from './extra/classes';
  

const wolverine = new SuperHeroe();
const ironman   = new SuperHeroe();
const spiderman = new SuperHeroe();

  

function saludar() {
    return 'El SuperHeroe Wolverine es genial!';
}

  

function gritar() {
    return 'El SuperHeroe en este string no se debe de cambiar';
}
```
Al querer cambiar de manera local, tocamos el atajo en `SuperHero`
![[Pasted image 20230123064920.png|800]]
Y como resultado, el cambio se da de manera local: 
```typescript
import { SuperHeroe as Hero } from './extra/classes';
  

const wolverine = new Hero();
const ironman   = new Hero();
const spiderman = new Hero();
  

function saludar() {
    return 'El SuperHeroe Wolverine es genial!';
}

function gritar() {
    return 'El SuperHeroe en este string no se debe de cambiar';

}
```

Para hace el cambio de manera global es tan sencillo como ir a la definicion , en este caso de la clase `SuperHero` en donde se aloja la clase y no es exportado , ingresar el atajo y este cambio se efectuara de manera global: 
![[Pasted image 20230123065425.png]]

---

