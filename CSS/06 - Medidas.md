  
En CSS, las medidas se utilizan para especificar el tamaño, la posición y otros atributos de los elementos. Las medidas se pueden expresar en una variedad de unidades, incluidas las unidades absolutas y relativas.

![[Pasted image 20231016092519.png]]


## EM
El EM en CSS es una unidad de medida relativa que se basa en el tamaño de la fuente del elemento. Un EM es igual al tamaño de la fuente del elemento.

Por ejemplo, si el tamaño de la fuente del elemento es de 16px, un EM también tendrá un tamaño de 16px. Si el tamaño de la fuente del elemento se cambia a 24px, un EM también tendrá un tamaño de 24px.

Los EM se utilizan a menudo para establecer el tamaño de la fuente, el margen, el relleno y otros atributos de los elementos.

**Ejemplos**

El siguiente ejemplo establece el tamaño de la fuente de un elemento a 2EM:

```CSS
h1 {
  font-size: 2em;
}
```
Este ejemplo establecerá el tamaño de la fuente del elemento `h1` a dos veces el tamaño de la fuente del elemento padre.

El siguiente ejemplo establece el margen superior de un elemento a 1EM:
```CSS
div {
  margin-top: 1em;
}
```

Este ejemplo establecerá el margen superior del elemento `div` a un tamaño igual al tamaño de la fuente del elemento.

**Ventajas de los EM**

Los EM tienen varias ventajas sobre otras unidades de medida relativas, como los píxeles y los porcentajes:

- **Son escalables:** el tamaño de los EM se escalará automáticamente en función del tamaño de la fuente del elemento.
- **Son consistentes:** el tamaño de los EM será el mismo en todos los dispositivos, independientemente de la resolución de la pantalla.
- **Son fáciles de usar:** los EM son una forma sencilla de establecer el tamaño de los elementos de manera proporcional.

**Desventajas de los EM**

Los EM también tienen algunas desventajas:

- **No son precisos:** el tamaño de los EM puede variar ligeramente en función del navegador y del sistema operativo.
- **No son adecuados para todos los casos:** los EM no son adecuados para establecer el tamaño de los elementos que deben tener un tamaño específico.

## REM
  
El rem en CSS es una unidad de medida relativa que se basa en el tamaño de la fuente de la raíz. Un rem es igual al tamaño de la fuente de la raíz, que es el tamaño de la fuente del elemento `html`

Por ejemplo, si el tamaño de la fuente de la raíz es de 16px, un rem también tendrá un tamaño de 16px. Si el tamaño de la fuente de la raíz se cambia a 24px, un rem también tendrá un tamaño de 24px.

Los rem se utilizan a menudo para establecer el tamaño de la fuente, el margen, el relleno y otros atributos de los elementos.

**Ejemplos**

El siguiente ejemplo establece el tamaño de la fuente de un elemento a 2rem:
```CSS
h1 {
  font-size: 2rem;
}
```

Este ejemplo establecerá el tamaño de la fuente del elemento `h1` a dos veces el tamaño de la fuente de la raíz.

El siguiente ejemplo establece el margen superior de un elemento a 1rem:
```CSS
div {
  margin-top: 1rem;
}
```

Este ejemplo establecerá el margen superior del elemento `div` a un tamaño igual al tamaño de la fuente de la raíz.

**Ventajas de los rem**

Los rem tienen varias ventajas sobre otras unidades de medida relativas, como los píxeles y los porcentajes:

- **Son escalables:** el tamaño de los rem se escalará automáticamente en función del tamaño de la fuente de la raíz.
- **Son consistentes:** el tamaño de los rem será el mismo en todos los dispositivos, independientemente de la resolución de la pantalla.
- **Son fáciles de usar:** los rem son una forma sencilla de establecer el tamaño de los elementos de manera proporcional.

**Desventajas de los rem**

Los rem también tienen algunas desventajas:

- **No son precisos:** el tamaño de los rem puede variar ligeramente en función del navegador y del sistema operativo.
- **No son adecuados para todos los casos:** los rem no son adecuados para establecer el tamaño de los elementos que deben tener un tamaño específico.

**Comparación de rem y em**

Los rem y los em son unidades de medida relativas, pero tienen algunas diferencias importantes:

- **Los rem se basan en el tamaño de la fuente de la raíz, mientras que los em se basan en el tamaño de la fuente del elemento.**
- **Los rem son más escalables que los em, porque el tamaño de la fuente de la raíz también se escalará en función de la resolución de la pantalla.**

En general, los rem son una mejor opción que los em para establecer el tamaño de los elementos en CSS.

Como un claro ejemplo que puede ser confuso el uso que se le tenga sin píxeles, hay una forma de trabajarlos los REM como si fueran píxeles y eso es de la siguiente forma, tomando en cuenta que en un navegador por defecto la fuente de la etiqueta HTML es de 16px, entonces la forma de resetearlo es la siguiente:
```CSS
html {

    font-size: 62.5%;

}
```
Al hacer esta anotación le decimos al navegador que prácticamente funcione en porcentaje la fuente, pero esto no implica ningún cambio, la fuente sigue en 16px.

¿Entonces qué cambia?
Cambia en que ahora podremos simular un pixelaje en los REM:
```CSS
p {

    font-size: 1.6rem;

}
```
Ahora en proporción a lo que sabemos que el HTML está en 16px, ahora para simular esos 16px tendremos que poner 1.6 rem = 16, 1.0 rem = 10px y así sucesivamente.

El uso de rem como si fueran píxeles es una técnica útil para crear diseños escalables. Sin embargo, es importante tener en cuenta las limitaciones de esta técnica, como el hecho de que el tamaño de los elementos no será el mismo en todos los navegadores

---
## Max_Min Width

**min-width** y **min-height** son propiedades CSS que se utilizan para establecer el ancho y el alto mínimos de un elemento. Esto significa que el elemento nunca será más pequeño que el ancho o alto especificado, incluso si el contenido del elemento es más pequeño.

**max-width** y **max-height** son propiedades CSS que se utilizan para establecer el ancho y el alto máximos de un elemento. Esto significa que el elemento nunca será más grande que el ancho o alto especificado, incluso si el ancho o alto disponible de su contenedor es mayor.

Estas propiedades son muy útiles para crear diseños responsivos, ya que permiten que los elementos se adapten a diferentes tamaños de pantalla sin romperse. Por ejemplo, puedes usar `min-width` para asegurarte de que un elemento nunca sea más pequeño que un cierto ancho, incluso en pantallas pequeñas. O puedes usar `max-width` para asegurarte de que un elemento nunca sea más grande que un cierto ancho, incluso en pantallas grandes.

Aquí hay algunos ejemplos de cómo usar las propiedades `min-width`, `min-height`, `max-width` y `max-height`:
```CSS
/* Establecer el ancho mínimo de un elemento a 200px */
.element {
  min-width: 200px;
}

/* Establecer el alto mínimo de un elemento a 100px */
.element {
  min-height: 100px;
}

/* Establecer el ancho máximo de un elemento a 500px */
.element {
  max-width: 500px;
}

/* Establecer el alto máximo de un elemento a 300px */
.element {
  max-height: 300px;
}
```

También puedes usar estas propiedades junto con unidades relativas, como porcentajes (`%`) y ems (`em`). Por ejemplo, puedes usar `min-width: 50%` para asegurarte de que un elemento nunca sea más pequeño que el 50% del ancho de su contenedor. O puedes usar `max-height: 100vh` para asegurarte de que un elemento nunca sea más alto que la altura de la ventana gráfica

