CSS, siglas de Cascading Style Sheets, es un lenguaje de programación que se utiliza para definir la apariencia de los documentos HTML. Es un lenguaje de hojas de estilo que permite especificar el diseño de los elementos de una página web, como el tamaño, la fuente, el color, el espaciado, la alineación, etc.

Para invocar CSS en un archivo HTML, existen diferentes métodos:

1. **Vincular un archivo CSS externo**: Utiliza la etiqueta `<link>` en la sección `<head>` del documento HTML para vincular un archivo CSS externo. Debes especificar la ruta del archivo CSS en el atributo `href`. Por ejemplo:

```html
	<link rel="stylesheet" href="styles.css">
```

2. **Estilos en línea**: Puedes aplicar estilos directamente a una etiqueta HTML utilizando el atributo `style`. Por ejemplo:

```html
	<p style="color: blue; font-size: 16px;">Este es un párrafo con estilo en línea.</p>
```

3. **Estilos internos**: Puedes definir los estilos CSS dentro de las etiquetas `<style>` en la sección `<head>` del documento HTML. Por ejemplo:

```html
<style>
    p {
        color: blue;
        font-size: 16px;
    }
</style>

```

Recuerda que es recomendable utilizar archivos CSS externos para mantener un código más organizado y facilitar la reutilización de estilos en diferentes páginas HTML.

## Pseudoclases y la importancia del BEM

Las pseudoclases en CSS son selectores especiales que se utilizan para aplicar estilos a elementos en estados específicos o en relación con otros elementos. Por ejemplo, la pseudoclase `:hover` se aplica cuando el cursor se sitúa sobre un elemento, y la pseudoclase `:first-child` se aplica al primer hijo de un elemento padre.

Aquí tienes ejemplos de cómo se utilizan algunas pseudoclases:

- `:hover`: Permite aplicar estilos cuando el cursor se sitúa sobre un elemento. Por ejemplo:

```css
a:hover {
    color: red;
}

```

- `:first-child`: Permite aplicar estilos al primer hijo de un elemento padre. Por ejemplo:

```css
ul li:first-child {
    font-weight: bold;
}

```

Estos son solo algunos ejemplos, pero existen muchas otras pseudoclases disponibles en CSS, como `:active`, `:visited`, `:focus`, entre otras. Cada una de ellas se utiliza para aplicar estilos en diferentes situaciones.

Además, es importante mencionar la importancia de utilizar la metodología BEM (Block Element Modifier) al escribir estilos CSS. Esta metodología propone una forma de organizar y nombrar las clases de CSS de manera clara y estructurada, lo que facilita el mantenimiento y la reutilización de estilos en un proyecto.

El enfoque BEM se basa en dividir los componentes de una página en bloques (blocks), elementos (elements) y modificadores (modifiers). Los bloques representan componentes independientes y reutilizables, los elementos son las partes internas de un bloque y los modificadores permiten modificar el estilo de un bloque o elemento de manera específica.

Aquí tienes un ejemplo de cómo se estructura una clase utilizando la metodología BEM:

```css
/* Bloque */
.form {
    /* Estilos del bloque */
}

/* Elemento */
.form__input {
    /* Estilos del elemento */
}

/* Modificador */
.form__input--error {
    /* Estilos del modificador */
}

```

Al utilizar pseudoclases de manera efectiva y seguir una metodología como BEM, se puede mejorar la legibilidad y la mantenibilidad del código CSS, lo que resultará en un desarrollo más eficiente y escalable de la apariencia de una página web.