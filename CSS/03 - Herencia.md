La herencia en CSS es un principio fundamental que determina cómo se aplican los estilos a los elementos HTML en función de la jerarquía y la estructura del documento. En otras palabras, la herencia permite que los estilos se propaguen automáticamente desde un elemento principal a sus elementos secundarios.

Para entender la herencia en CSS, primero debemos tener en cuenta que cada elemento HTML hereda estilos de sus elementos contenedores y también de los estilos predeterminados del navegador. Aquí tienes una explicación más detallada y ejemplos:

1. Estilos predeterminados del navegador: Cada navegador web tiene estilos predeterminados para todas las etiquetas HTML. Por ejemplo, los navegadores suelen establecer un tamaño de fuente predeterminado, un margen alrededor del cuerpo del documento, un espaciado entre párrafos y otros estilos por defecto. Estos estilos se aplican automáticamente a todas las etiquetas HTML a menos que los reemplaces con estilos personalizados.
    
2. Herencia de estilos: La herencia permite que los estilos aplicados a un elemento padre se hereden por defecto por sus elementos hijos. Esto significa que si aplicas un estilo a un elemento HTML específico, como un párrafo (`<p>`), los elementos de texto dentro de ese párrafo heredarán esos estilos a menos que se especifiquen estilos diferentes para los elementos hijos.

HTML:
```html
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" type="text/css" href="styles.css">
  </head>
  <body>
    <div id="contenedor">
      <p>Este es un párrafo de ejemplo.</p>
    </div>
  </body>
</html>
```

CSS (styles.css):
```CSS
#contenedor {
  font-family: Arial, sans-serif; /* Establece la fuente para el contenedor */
  font-size: 20px; /* Establece el tamaño de fuente para el contenedor */
  color: blue; /* Establece el color de texto para el contenedor */
}
```

En este ejemplo, hemos aplicado estilos al elemento con el ID "contenedor". Los estilos incluyen una fuente, tamaño de fuente y color de texto. Debido a la herencia, el párrafo dentro del contenedor heredará automáticamente estos estilos. Por lo tanto, el texto del párrafo será de color azul, tendrá un tamaño de fuente de 20px y utilizará la fuente Arial o una fuente sans-serif si Arial no está disponible en el sistema.

En resumen, la herencia en CSS permite que los estilos se propaguen de los elementos padres a los elementos hijos, lo que facilita la aplicación de estilos de manera eficiente y coherente en un sitio web. Sin embargo, los estilos pueden ser anulados o personalizados en elementos hijos según sea necesario.