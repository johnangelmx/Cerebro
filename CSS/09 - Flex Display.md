Flexbox, o "Flexible Box Layout," es un modelo de diseño en CSS que fue creado para facilitar el diseño de interfaces web complejas y mejorar la distribución de elementos en un contenedor, incluso cuando el tamaño de los elementos es desconocido o dinámico.

Flexbox introduce un nuevo valor para la propiedad `display`, llamado `flex`. Cuando un contenedor se establece como `display: flex`, se convierte en un contenedor flexible que permite a sus elementos hijos ajustarse automáticamente según el espacio disponible.

Es decir, Flexbox es un módulo en el cual permite la organización de hijos en el contenedor padres, todo esto ayuda a la organización y manipulación de mejor manera de los hijos. 

---
## Flexbox Explicación
Primero que nada, para iniciar el uso de este módulo tendremos que asignar el valor `flex` a la propiedad `display`: 
```CSS
.parent{
display: flex;
}
.child-1{}
.child-2{}
.child-3{}
```

Recordemos que para que funcione siempre tiene que haber un contenedor padre `.parent` que es al que se le asigna el `display: flex;` y sus hijos son los que se organizaran de mejor manera.

#### El Padre
Entendiendo esto de manera más visual, el padre tendría la siguiente forma:
```HTML
<section class="parent"></section>
```
```CSS
.parent{
  border: 5px solid black;
  height: 500px;
  width: 500px;
}
```
![[Pasted image 20231111061454.png|200]]
#### Los Hijos
Agregando a los hijos tendrían la siguiente forma:
```HTML
<section class="parent">
  <div class="child child-1">1</div>
  <div class="child child-2">2</div>
  <div class="child child-3">3</div>
</section>
```
```CSS
.parent{
  border: 5px solid black;
  height: 500px;
  width: 500px;
}
.child {
  height: 150px;
  width: 150px;
  font-size: 2.5rem;
}
.child-1 {
  background-color: red;
} 
.child-2 {
  background-color: yellow;
}
.child-3 {
  background-color: blue;
}
```
![[Pasted image 20231111062143.png|250]]

---
## Usando Flexbox
Ahora que entendemos la estructura del ejemplo anterior, es crucial notar que el elemento principal, identificado como `.parent`, junto con sus hijos etiquetados como `<div>`, poseen una propiedad por defecto llamada `display: block;`. Este atributo significa que, al ser elementos en bloque, naturalmente intentarán ocupar todo el ancho de la página y, como resultado, se alinearán uno tras otro en forma de bloques apilados.

Ahora, para empezar a usar flexbox, tendremos que usar la propiedad `display` con el valor `flex`
```CSS
.parent{
  border: 5px solid black;
  height: 500px;
  width: 500px;
  display: flex;
}
```

Automáticamente, los hijos, ya no ocupan todo el ancho de la página, sino que ahora solo ocupan el tamaño asignado y proceden a apilarse en fila, todo esto porque la primera propiedad que vienen incluido con el módulo flexbox es `flex-direction` y el valor por defecto de esta propiedad es `row`.
![[Pasted image 20231111063533.png|250]]

---
## Flex-direction
Para entender un poco a partir de ahora de lo que paso, es necesario saber que la forma de organizar flexbox es de forma bidimensional, es decir, solo hay forma de moverlo en 2D, sé que es un poco extraño a estas alturas, pero solo imagina la siguiente imagen a comparación del ejemplo que hemos venido trabajando:   
![[Pasted image 20231111075801.png]]

![[Pasted image 20231111063533.png|250]]

Ahora bien, el contenedor en este caso sería el padre `.parent`, el ítem sería los hijos en singular `.child` y el eje principal y secundario ya estarían en nuestro ejemplo, pero estos no están representados de manera visual. 

Una vez entendido eso, por defecto, cuando simplemente ponemos `display: flex;`, nuestro eje principal se encuentra en forma de fila `row` y se lee de izquierda a derecha y como podemos ver están ordenados de manera numérica y apilados.

La propiedad que puede manipular la orientación del eje principal es flex-direction
### Tipo de valores de la propiedad flex-direction

La propiedad `flex-direction`, como previamente destacamos, desempeña la función de modificar la dirección del flujo de los elementos hijos dentro de un contenedor flexible. En otras palabras, esta propiedad nos permite especificar si los elementos se deben organizar en una fila horizontal, una fila inversa horizontal, una columna vertical o una columna inversa vertical.

#### flex-direction: row;
Por defecto, cuando no ingresamos la propiedad flex-direction, el módulo flexbox denomina esa propiedad en row:

`row`: El eje principal va de izquierda a derecha
![[Pasted image 20231111063533.png|250]]
Esto se lee de izquierda a derecha y los hijos se apilan de la misma forma empezando de izquierda a derecha

#### flex-direction: row-reverse;
Ahora bien, existe una forma en la cual de manera inversa los elemente se muestren de derecha a izquierda, ese es el valor de `row-reverse`
`row-reverse`: El eje principal va de derecha a izquierda.
![[Pasted image 20231111082525.png|250]]

Esto se lee de derecha a izquierda, los números están organizados de igual manera, y los hijos se acomodan hasta el final del padre `.parent`

#### flex-direction: column;
Como previamente hemos visto `flex-direction` no solo nos permite organizar elementos de manera horizontal, sino que también nos brinda la capacidad de cambiar el eje principal para presentarlos de manera vertical. A pesar de esta orientación vertical, el eje que consideramos como principal continúa siendo el mismo, lo que significa que la distribución y el posicionamiento de los elementos se ajustan según este eje vertical principal.

`column`: El eje principal va de arriba hacia abajo.
![[Pasted image 20231111083249.png|250]]

Esto se lee de manera numérica de arriba hacia abajo, están organizados de igual manera, pero apilados uno sobre otro.
#### flex-direction: column-reverse;
Al igual que el `row-reverse` podemos invertir la forma en que se organiza el `column` con el `column-reverse`. 
`column-reverse`: El eje principal va de abajo hacia arriba.
![[Pasted image 20231111083433.png|250]]

Este se lee de manera inversa numérica, de abajo hacia arriba, están organizados los hijos de igual manera, pero apilados uno sobre otro.

---

## Justify-content:

Por ahora ya supimos como ordenar los elementos a través del contenedor o padre `.parent`, pero  que pasa con el ordenamiento entre ellos, es decir, todo el tiempo estarán juntos? Bueno, respuesta corta no, a menos que nosotros lo queramos así.

El ordenamiento entre ellos lo maneja la propiedad `justify-content` con valores que vamos a explicar a continuación, en este punto hay que tener en claro que: 

`justify-content` Controla el cómo se ordenan los elementos del contenedor de manera horizontal, es decir, como los hijos `.child` se visualizan y ordenan de manera horizontal, **No verticalmente**.

### `flex-start`
El contenido en el horizontal se acomoda de derecha a izquierda 
![[Pasted image 20231129145336.png|250]]
### `center;`
El contenido en el eje horizontal se acomoda céntricamente
![[Pasted image 20231129145442.png|250]]
### `flex-end`
El contenido en el eje horizontal se acomoda de izquierda a derecha
![[Pasted image 20231129145626.png|250]]
### `space-between`
Distribuir ítems uniformemente, el primer ítem al inicio, el último al final
![[Pasted image 20231129162052.png|250]]
### `space-around`
Distribuir ítems uniformemente, los ítems tienen el mismo espacio a su alrededor
![[Pasted image 20231129162142.png|250]]
### `space-evenly`
Los elementos tendrán el mismo espacio a su alrededor.
![[Pasted image 20231129162215.png|250]]

---
## Align-items:
Una vez que hemos aprendido a como orientarlos en su propio eje horizontal, ¿Que pasa con el eje vertical?

La gestión del orden entre ellos recae en la propiedad `align-items`, la cual determina la alineación vertical de los elementos dentro del contenedor. Es decir, dicta cómo los hijos `.child` se visualizan y organizan verticalmente, en lugar de horizontalmente.

Ahora para que se vea mejor representado orientaremos el `justify-content`en `space-around`

### `flex-start;`
![[Pasted image 20231130001438.png|250]]
### `center;`
![[Pasted image 20231130001507.png|250]]
### `flex-end;`
![[Pasted image 20231130001536.png|250]]
### `stretch;`
![[Pasted image 20231130001639.png|250]]

### `baseline;`
![[Pasted image 20231130001732.png|250]]

## **`flex-grow`**: 
Define cómo se distribuye el espacio adicional entre elementos flexibles. Un valor mayor significa que el elemento crecerá más en relación con los demás.

```CSS
.item {   flex-grow: 2; /* Este elemento crecerá el doble de rápido que los demás */ }`
```
   
## **`flex-shrink`**:
Controla cómo los elementos flexibles se contraen cuando hay espacio insuficiente. Un valor mayor significa que el elemento se contraerá más rápidamente.

```CSS
.item {   flex-shrink: 1; /* Este elemento se contraerá en la misma proporción que los demás */ }`
```
## **`flex-basis`**: 
Establece el tamaño inicial del elemento antes de distribuir el espacio adicional. Puede ser un valor fijo, un porcentaje o `auto`.
```CSS
.item {   flex-basis: 200px; /* Tamaño inicial del elemento antes de distribuir el espacio */ }`
```

