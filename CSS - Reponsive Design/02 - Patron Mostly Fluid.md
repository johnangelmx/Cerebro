# Patrones de maquetación Responsive Design

El diseño responsive es una metodología de diseño web que permite que las páginas web se adapten a diferentes tamaños de pantalla. Los patrones de maquetación responsive son una serie de estrategias que se pueden utilizar para crear páginas web que se vean bien y sean fáciles de usar en cualquier dispositivo.

## Mostly Fluid
El patrón de diseño Mostly Fluid es un enfoque de diseño web responsivo que se centra en crear una experiencia de usuario óptima para dispositivos móviles. El patrón se basa en la idea de que el contenido de una página web debe estar organizado en una cuadrícula fluida, lo que significa que el ancho de las columnas se adapta al ancho de la pantalla.

En el patrón Mostly Fluid, el contenido de la página web se organiza en una serie de columnas que se distribuyen de forma horizontal. Las columnas se pueden anidar para crear una estructura de contenido jerárquica. El ancho de las columnas se define en términos de porcentajes, lo que permite que se adapten al ancho de la pantalla sin problemas.

![[Pasted image 20231211054112.png]]
## Reglas: 
- **Empieza con el diseño para dispositivos móviles.** El patrón Mostly Fluid se basa en el enfoque mobile first, por lo que es importante empezar con el diseño para dispositivos móviles. Esto garantizará que la experiencia de usuario sea óptima para los usuarios de dispositivos móviles, que son cada vez más numerosos.
- **Organiza el contenido en una cuadrícula fluida.** El contenido de la página web debe estar organizado en una cuadrícula fluida, lo que significa que el ancho de las columnas se adapta al ancho de la pantalla. Para ello, se pueden utilizar las propiedades CSS `width` o `column-width`.
- **Define el ancho de las columnas en términos de porcentajes.** El ancho de las columnas se define en términos de porcentajes, lo que permite que se adapten al ancho de la pantalla sin problemas. Por ejemplo, si se define el ancho de una columna como `50%`, la columna ocupará la mitad del ancho de la pantalla, independientemente del tamaño de la pantalla.
- **Utiliza márgenes y rellenos para controlar el espaciado.** Los márgenes y rellenos se pueden utilizar para controlar el espaciado entre las columnas y los elementos del contenido. Esto es importante para garantizar que el contenido se vea bien en diferentes tamaños de pantalla.
- **Prueba la página web en diferentes dispositivos.** Es importante probar la página web en diferentes dispositivos para asegurarse de que el contenido se ve bien y se puede interactuar con él de forma sencilla.

---
## Ejemplo Proyecto
Como es costumbre en esta documentación demostraremos paso a paso el funcionamiento de e implementación del tema, en este caso mostly fluid.

En su mayor parte esto se trabajará con flexbox y porcentajes, la idea es que por medio de los porcentajes podremos acaparar contenedores, sé que es algo confuso, pero para iniciar tendremos los archivos index.html y styles.css

Antes de empezar quiero que imagines que para "mobile firts" vamos a tener 5 contenedores apilados uno sobre otro, la altura será de 150px, pero la anchura será de 100%, y se verá algo así: 
![[Pasted image 20231211061643.png|300]]
## Mobile First
Empecemos en tu archivo `index.html` tendremos lo siguiente: 
```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <main class="container">
        <div class="c1"></div>
        <div class="c2"></div>
        <div class="c3"></div>
        <div class="c4"></div>
        <div class="c5"></div>
    </main>
</body>
</html>
```
Y para estilos primero definiremos él [[00 - Reseteo de CSS|Reseteo de estilos]] y después el código a continuación: 
```CSS
.container {
    display: flex;
    flex-flow: row wrap;
}
```
Recordemos que esto es "mobile first" así que usaremos por defecto las propiedades de flex, exceptuando el `flex-wrap` que de ser `nowrap` pasara a `wrap`, recordemos que la propiedad `flex-flow` se le puede asignar las propiedades `flex-direction` y `flex-wrap` en una sola declaración.

```CSS
.c1,
.c2,
.c3,
.c4,
.c5 {
    width: 100%;
    min-width: 150px;
    height: 150px;
}
```
Ahora lo que estamos haciendo aquí es asignar el tamaño como las reglas de "Mostly Fluid" lo requiere, expliquemos un poco más lo que pasa aquí:

**Propiedades CSS:**
- `width: 100%;`: Esta propiedad establece que el ancho de los elementos con estas clases será el 100% del ancho de su contenedor. En otras palabras, ocuparán todo el ancho disponible.
- `min-width: 150px;`: Aquí se establece que el ancho mínimo de los elementos será de 150 píxeles. Esto significa que, aunque los elementos pueden ocupar el 100% del ancho, no se contraerán más allá de 150 píxeles.
- `height: 150px;`: La altura de los elementos con estas clases se fija en 150 píxeles. Todos los elementos tendrán la misma altura.

Integremos colores: 
```CSS
.c1 {
    background-color: #003476;
}

.c2 {
    background-color: #0062d2;
}

.c3 {
    background-color: #b4d2f7;
}

.c4 {
    background-color: #d5dfef;
}

.c5 {
    background-color: #dfe1e5;
}
```

Como resultado tendremos: 
![[Pasted image 20231211063402.png|300]]

Puedes probar los demás tamaños, pero por ahora lo único que verás es que los contenedores seguirán apilados y se extenderán en todo el ancho de la pantalla, aún no hemos implementado para tablets y escritorios.

---

## Tablet viewport
Ahora viene el uso de media-queries dentro de CSS, como nos dimos cuenta vamos de adentro hacia afuera, para el uso de tablets dentro de este ejemplo será de 600px y la forma en el cual le diremos que él cambiará será por medio de `min-width` : 

>**Nota**: Los media-queries tienen que estar siempre al final del archivo CSS, y en el caso de "Mobile First" tienen que ir de menor a mayor

```CSS
@media (min-width: 600px) {
	/* Codigo*/
}
```
En este caso, se está diciendo que los estilos dentro de esta regla se aplicarán solo si el ancho de la ventana del navegador es de al menos 600 píxeles. Si es menos de 600px, entonces tomará los estilos que hemos escrito hasta ahora, los de [[02 - Patron Mostly Fluid#Mobile First|Mobile First]].

```CSS
@media (min-width: 600px) {
    .c2,
    .c3,
    .c4 {
        width: 50%;
    }
}
```
Le asignaremos al contenedor 2,3 y 4, que puedan tomar ahora 50% de la ventana, como resultado: 

![[Pasted image 20231211070409.png|500]]

En este punto te dirás, si tenemos 5 contenedores, dos de ellos ocuparán el mayor ancho de la página y 3 de ellos solo ocuparán el 50%, el espacio sobrante ¿de quién es?, bueno, el espacio sobrante es del contenedor padre, y se hizo a propósito para que estés al tanto de la manipulación de contenedores. La forma idónea es tener un contenedor más para llenar ese espacio o acomodar y manipular los tamaños de los contenedores que cuentas.

---
## Desktop viewport
Ahora tendremos que escalar para los ordenadores, para este ejemplo tendremos que usar 800px para el media-query:
```CSS
@media (min-width: 800px) {
    .container {
        width: 800px;
        margin-left: auto;
        margin-right: auto;
    }

    .c1 {
        width: 60%;

    }

    .c2 {
        width: 40%;
    }

    .c3,
    .c4,
    .c5 {
        width: 33.3%;
    }
```

  Expliquemos lo siguiente:
  - c1 y c2, como te lo imaginaras, tomaran juntos una fila 
  - c3,c4,c5 tomaran otra fila 
  
  Como resultado: 
  ![[Pasted image 20231211071958.png|500]]

Ahora, ¿Qué pasa con el código de `.container`?
Bueno, esta es una forma de que tu diseño deje de crecer si tenemos dispositivos más grandes, visualizando nuestra página.

- `width: 800px;`: Cambia su tamaño para que no crezca.
- `margin-left: auto;`: Le indica que su margen izquierdo crezca automáticamente
- `margin-right: auto;`: Le indica que su margen derecho crezca automáticamente

Como resultado, si lo visualizamos en una anchura más grande se verá así: 
![[Pasted image 20231211072725.png|500]]
Nunca perderá su diseño de esta forma.

## Buenas Prácticas
Como mencionamos, la mayoría de los recursos de cada página vendrán con los media-queries dentro del mismo archivo CSS único. Sin embargo, esto no es una buena práctica. Una buena práctica es organizar y modularizar tu código CSS para mejorar la mantenibilidad y la legibilidad.

#### Media-Queries en Archivos Independientes:
Crea archivos separados para tus media-queries, organizándolos según las necesidades de los distintos tamaños de pantalla.

```plaintext
media-queries/
|-- desktop.css
|-- tablet.css
|-- mobile.css

```

Lo que pondremos en cada uno de los archivos será el código CSS únicamente sin el `@media`
por ejemplo en el archivo `tablet.css` pondremos:
```CSS
.c2,
.c3,
.c4 {
    width: 50%;
}
```

Y te preguntarás, ¿Dónde se le indica la media-query? Este se indicará en el HTML de la siguiente forma: 
```HTML
<head>
	<!-- ...Demas Codigo del HEAD -->
    <link rel="stylesheet" href="style.css">
    <link rel="stylesheet" href="tablet.css" media="screen and (min-width: 600px)">
    <link rel="stylesheet" href="desktop.css" media="screen and (min-width: 800px)">
</head>
```

¿Esto en qué ayuda? 
Esto le indicara al navegador que la página tiene medidas que pueda usar, entonces descargara más rápido el archivo que necesitara para entregarle al usuario:
![[Pasted image 20231211074453.png]]
Por ejemplo en esta imagen podemos ver que al descargar el estilo principal también lo hace al mismo tiempo de la tablet y después el de `desktop.css` 
![[Pasted image 20231211074602.png]]


