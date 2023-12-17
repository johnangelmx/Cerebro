# Posicionamiento de elementos

![[Pasted image 20231016101740.png]]

En CSS, la propiedad `position` juega un papel fundamental en la ubicación y el flujo de los elementos en una página web. Por defecto, la mayoría de los elementos tienen su propiedad `position` establecida en `static`. Esto significa que los elementos se comportan de manera estática y siguen el flujo normal del documento.

**Elementos en Bloque:** Los elementos en bloque ocupan todo el ancho disponible y se apilan uno encima del otro en el flujo normal del documento. Ejemplos de elementos en bloque incluyen:

- Párrafos (`<p>`)
- Encabezados (`<h1>`, `<h2>`, etc.)
- Divisiones (`<div>`)
- Listas (`<ul>`, `<ol>`)
- Elementos de formulario (`<form>`, `<input>`, `<textarea>`)

**Elementos en Línea:** Los elementos en línea se colocan uno al lado del otro en la medida de lo posible, en línea con el texto que los rodea. Ejemplos de elementos en línea incluyen:

- Enlaces (`<a>`)
- Texto dentro de un párrafo
- Imágenes (`<img>`)
- Elementos de énfasis (`<strong>`, `<em>`)
- Elementos de lista (`<li>`)

**Elementos en Línea con Bloque:** Algunos elementos pueden comportarse tanto como elementos en línea como elementos en bloque, dependiendo de cómo se configuren. Ejemplos de elementos en línea con bloque incluyen:

- Elementos de encabezado dentro de un párrafo (`<h1>` dentro de un `<p>`)
- Elementos de lista dentro de un párrafo (`<ul>` dentro de un `<p>`)

La propiedad `position: static` es la configuración por defecto y hace que los elementos se comporten de esta manera estática. Es importante destacar que la mayoría de las etiquetas HTML siguen este comportamiento por defecto.

Imaginemos que tenemos un cuadrado que sería el padre, y le ingresamos un cuadrado azul que sería el hijo, si ingresamos otro hijo azul, este mismo se situaría en la parte de abajo del primer hijo, y no a la derecha, como esperaríamos, todo esto es porque por defecto el navegador tiene el `position` en `static`

![[Pasted image 20231029204724.png]]

---
## Position: absolute

En CSS, la propiedad `position` con el valor `absolute` juega un papel importante en la ubicación y el flujo de los elementos en una página web. A diferencia de `position: static`, que es el valor por defecto y hace que los elementos sigan el flujo normal del documento, `position: absolute` permite a un elemento "escapar" del flujo normal y posicionarse de manera absoluta con respecto a su elemento padre o a un elemento posicionado de manera relativa.

Aquí hay algunas características clave de `position: absolute`:

1. **Posicionamiento absoluto:** Un elemento con `position: absolute` se posiciona en relación con su elemento padre más cercano que tiene una propiedad de posición diferente a `static`. Si ningún elemento padre tiene una posición diferente a `static`, el elemento con `position: absolute` se posicionará en relación con el cuerpo del documento.
    
2. **No afecta al flujo:** Los elementos con `position: absolute` no ocupan espacio en el flujo normal del documento. Esto significa que otros elementos pueden ocupar el espacio que dejaría un elemento posicionado de esta manera.
    
3. **Coordenadas personalizadas:** Puedes especificar las coordenadas de un elemento con `position: absolute` utilizando las propiedades `top`, `right`, `bottom` y `left`. Estas propiedades permiten controlar exactamente dónde se ubicará el elemento en relación con su elemento padre o el cuerpo del documento.
    
4. **Superposición:** Al utilizar `position: absolute`, puedes superponer elementos en la página, lo que es útil para crear capas y diseños complejos.
    
5. **Z-index:** Además de las coordenadas, puedes controlar la profundidad de apilamiento de elementos con `position: absolute` utilizando la propiedad `z-index`. Esto determina cuál elemento se mostrará por encima de otro cuando se superponen.
    

En resumen, `position: absolute` es una propiedad CSS que permite posicionar un elemento de manera absoluta en relación con su elemento padre o el cuerpo del documento, lo que lo hace útil para crear diseños sofisticados y superposiciones en una página web.

Imaginemos el panorama anterior; 

![[Pasted image 20231029211941.png]]

> Claramente, es una sección dentro de otra sección, de forma estilizada por CSS, etc. Pero eso no es lo que nos importa por ahora.

Ahora bien, si nosotros al `container` le agregamos `position:absolute;` aparentemente no ocurre nada, pero si ingresamos como el punto 3, coordenadas, podremos moverlo a través de documento completo, es decir,  moverlo a través de la página entera.

```CSS
.container {
  background: #09f;
  width: 100px;
  height: 100px;

  /*Explicando el position*/
  position: absolute;
  top: 0;
  right: 0;

}
```

Tendremos algo como esto: 
![[Pasted image 20231029212520.png]]

También podríamos usar porcentajes o cualquier tipo de medidas, pero al tener esta herramienta, podemos decirle a los elementos que tengan un comportamiento diferente en cuestión de la posición. 

---
## Position: relative

En CSS, la propiedad `position` con el valor `relative` es fundamental para la ubicación y el flujo de los elementos en una página web. A diferencia de `position: static`, que es el valor por defecto y hace que los elementos sigan el flujo normal del documento, `position: relative` permite realizar desplazamientos o ajustes en la posición de un elemento en relación con su posición normal en el flujo del documento.

Aquí hay algunas características clave de `position: relative`:

1. **Desplazamiento relativo:** Cuando se aplica `position: relative` a un elemento, se puede utilizar las propiedades `top`, `right`, `bottom` y `left` para mover el elemento desde su posición normal en el flujo del documento. Estos valores pueden ser positivos (desplazamiento hacia abajo y hacia la derecha) o negativos (desplazamiento hacia arriba y hacia la izquierda).
    
2. **Afecta al flujo:** A diferencia de `position: absolute`, los elementos con `position: relative` siguen ocupando espacio en el flujo normal del documento, incluso después de aplicar desplazamientos. Esto significa que otros elementos respetarán el espacio ocupado por el elemento con `position: relative`.
    
3. **Referencia a sí mismo:** Los desplazamientos definidos con `position: relative` se aplican en relación con la posición normal del propio elemento. Por lo tanto, si un elemento se desplaza hacia abajo (`top: 10px`), se moverá hacia abajo en relación con su posición original.
    
4. **Orden de apilamiento:** Los elementos con `position: relative` mantienen su orden de apilamiento en relación con otros elementos en el flujo normal del documento. Esto significa que no se superpondrán automáticamente a otros elementos como lo haría `position: absolute`.
    

Dado el ejemplo anterior, estábamos en un predicamento, porque, ¿cómo podríamos decirle al `container` que solo respete al padre y se mueva en forma de coordenadas pero dentro del padre?
![[Pasted image 20231029212520.png]]

Tendríamos que decirle al padre que él es `relative`, ¿por qué? Dado que el `abosulute` trabaja de forma que estaría buscando por [[03 - Herencia|Herencia]] al padre y sus propiedades, el padre en el ejemplo anterior al no tener una propiedad que le indique como comportarse, el hijo busca más arriba y al no tener se quedaría en el documento completo, es decir la página completa.

Así que al padre que es un `section` hay que indicarle que es `relative`:

```CSS
section {
  border: 5px solid #000;
  width: 250px;
  height: 250px;
  box-sizing: border-box;
  position: relative;

}

.container {
  background: #09f;
  width: 100px;
  height: 100px;
  /*  */
  position: absolute;
  right: 0;
  top: 0;

}
```
![[Pasted image 20231029214254.png]]

algo curioso de esto es que podríamos centrar el elemento en su totalidad solo con las herramientas hasta aquí vistas, cosa que no es recomendable, pero seria de al siguiente forma:
```CSS
.container {
  background: #09f;
  width: 100px;
  height: 100px;
  /*  */
  position: absolute;
  right: 0;
  top: 0;
  bottom: 0;
  left: 0;
  margin: auto;
}
```
Si le indicamos de esta forma que se comporte el `container` tendríamos esto: 
![[Pasted image 20231029214452.png]]

Y del mismo modo, para no ocupar todas las coordenadas, podríamos remplazarlas con `inset`, que permite darle un solo valor, para todas las coordenadas:
```CSS
.container {
  background: #09f;
  width: 100px;
  height: 100px;
  /*  */
  position: absolute;
  inset: 0;
  margin: auto;
}
```

---
## Position: fixed

En CSS, la propiedad `position` con el valor `fixed` desempeña un papel importante en la ubicación y el flujo de los elementos en una página web. A diferencia de `position: static`, que es el valor por defecto y hace que los elementos sigan el flujo normal del documento, `position: fixed` permite posicionar un elemento de manera fija en relación con la ventana del navegador, de modo que permanece en la misma posición incluso cuando se desplaza la página.

Aquí hay algunas características clave de `position: fixed`:

1. **Posicionamiento fijo:** Un elemento con `position: fixed` se posiciona en relación con la ventana del navegador, en lugar de su elemento padre. Esto significa que el elemento permanece en la misma posición en la pantalla, incluso cuando se desplaza hacia arriba o hacia abajo en la página.
    
2. **No afecta al flujo:** Los elementos con `position: fixed` no ocupan espacio en el flujo normal del documento. Esto permite que otros elementos se superpongan a un elemento fijo sin afectar su posición.
    
3. **Coordenadas personalizadas:** Puedes especificar las coordenadas exactas de un elemento con `position: fixed` utilizando las propiedades `top`, `right`, `bottom` y `left`. Esto te permite controlar la posición precisa del elemento en la ventana del navegador.
    
4. **Uso común:** La propiedad `position: fixed` se utiliza comúnmente para elementos como barras de navegación fijas en la parte superior o inferior de una página, botones de acción que permanecen visibles en todo momento o anuncios que siguen al usuario mientras se desplaza por la página.
    
5. **Z-index:** Al igual que con `position: absolute`, puedes utilizar la propiedad `z-index` para controlar el orden de apilamiento de elementos con `position: fixed`, lo que determina cuál elemento se muestra por encima de otros si se superponen.

---

**Position: sticky**

En CSS, la propiedad `position` con el valor `sticky` es fundamental para la ubicación y el flujo de los elementos en una página web. A diferencia de `position: static`, que es el valor por defecto y hace que los elementos sigan el flujo normal del documento, `position: sticky` permite que un elemento se comporte de manera fluida hasta que alcanza una ubicación específica en la ventana del navegador, momento en el que se vuelve "pegajoso" o fijo en esa posición.

Aquí hay algunas características clave de `position: sticky`:

1. **Comportamiento pegajoso:** Un elemento con `position: sticky` se desplaza de manera normal en relación con su elemento padre o el cuerpo del documento hasta que alcanza una ubicación definida en la ventana del navegador. Una vez que llega a ese punto, el elemento se vuelve "pegajoso" y permanece fijo en esa posición mientras el usuario continúa desplazándose.
    
2. **Ubicación definida:** Para que un elemento sea pegajoso, debes especificar la posición en la que se volverá pegajoso utilizando la propiedad `top`, `right`, `bottom`, o `left`. Esto determina el umbral en el que el elemento cambia de su posición normal a una posición fija.
    
3. **No afecta al flujo:** Los elementos con `position: sticky` no ocupan espacio en el flujo normal del documento y, al igual que `position: fixed`, permiten que otros elementos se superpongan a ellos sin afectar su posición.
    
4. **Uso común:** La propiedad `position: sticky` es útil para crear efectos de navegación pegajosa, encabezados de tablas que permanecen visibles mientras se desplaza por una tabla larga o cualquier otro elemento que deba mantenerse en la vista del usuario.
    
5. **Z-index:** Al igual que con `position: fixed` y `position: absolute`, puedes utilizar la propiedad `z-index` para controlar el orden de apilamiento de elementos con `position: sticky`, lo que determina cuál elemento se muestra por encima de otros si se superponen.
    

En resumen, `position: sticky` es una propiedad CSS que permite que un elemento se comporte de manera fluida en relación con su elemento padre o el cuerpo del documento hasta que alcanza una ubicación específica en la ventana del navegador, momento en el que se vuelve pegajoso y permanece fijo en esa posición. Esto es útil para crear elementos de navegación pegajosa y mejorar la experiencia del usuario al navegar por una página web.