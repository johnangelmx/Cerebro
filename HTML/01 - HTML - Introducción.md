# HTML

HTML (HyperText Markup Language) es el lenguaje de marcado estándar utilizado para crear páginas web. Permite estructurar y presentar el contenido de una página web mediante etiquetas y elementos. Estas etiquetas definen la estructura y el significado del contenido, como encabezados, párrafos, enlaces, imágenes y mucho más. HTML se combina con CSS (Cascading Style Sheets) y JavaScript para crear páginas web interactivas y atractivas.

En resumen, HTML es el lenguaje fundamental para construir páginas web y define la estructura y el contenido de una página. Es esencial para cualquier desarrollador web comprender y utilizar HTML para crear sitios web efectivos y funcionales.

## Estructura básica semántica

```html
<!DOCTYPE html> <!-- Explica que es HTML5 -->
<html lang="es"> <!-- Contenedor de toda la pagina, el atributo lang="" especifica el idioma  -->

<head> <!-- Cabecera , en donde tendremos exportacion e informacion adicional para el navegador -->
    <meta charset="UTF-8"> <!-- Le dice al navegador que estrucutura del lenguaje usaremos en la pagina utf-8 es para espanol -->
    <meta name="description" content="Esta pagina te mostrara fotos de gatos"> <!-- Describe la pagina actual -->
    <meta name="robots" content="index,follow"> <!-- Autorizacion a los navegadores de busqueda -->
    <title>Es mi pagina</title> <!-- El titulo de la pagina -->
    <meta name="viewport" content="width=device-width, initial-scale=1,0">
    <!-- Le dice al navegador que sea responsivo de manera basica -->
    <link rel="stylesheet" href="./css/style.css"> <!-- Relacion con una hoja de estilos CSS -->
</head>

<body><!-- Cuerpo , lugar donde estructuraremos lo que se visualizara en el navegador -->
<header> <!-- Etiqueta contenedora que contendra el encabezado -->
        <nav></nav> <!-- Barra de navegacion -->
    </header>
    <main> <!-- Contenido principal -->
        <section> <!-- seccion -->
            <article><!-- articulos -->
                <ul><!-- Lista desordenada -->
                    <li>Soy una manzana</li>
                </ul>
                <ol><!-- Lista Ordenada -->

                </ol>
            </article>
        </section>
    </main>
    <footer> <!-- Pie de pagina -->

    </footer>
</body>

</html>
```

## Estructura básica dentro del body
```html
<body>
    <header> <!-- Etiqueta contenedora que contendra el encabezado -->
        <nav></nav> <!-- Barra de navegacion -->
    </header>
    <main> <!-- Contenido principal -->
        <section> <!-- seccion -->
            <article><!-- articulos -->
                
            </article>
        </section>
    </main>
    <footer> <!-- Pie de pagina -->

    </footer>
</body>
```

## Etiquetas de texto

Algunas etiquetas de texto comunes en HTML incluyen:

- `<h1>` a `<h6>`: Se utilizan para definir los encabezados de diferentes niveles, donde `<h1>` es el encabezado principal y `<h6>` es el encabezado de menor importancia.
- `<p>`: Se utiliza para crear párrafos de texto.
- `<strong>` y `<em>`: Se utilizan para resaltar texto, donde `<strong>` indica un énfasis fuerte y `<em>` indica un énfasis leve.
- `<a>`: Se utiliza para crear enlaces, donde el atributo `href` especifica la URL de destino del enlace.

Estas etiquetas son solo algunas de las muchas disponibles en HTML para formatear y organizar el texto en una página web.

Ejemplo en código:
```html
	<p>Soy un texto</p>
	<h1>Soy un titulo</h1>
    <h2>Soy otro titulo</h2>
    <h3>Soy un titulo mas</h3>
    <a href="#">Soy un link</a>
```

Así como también existen las listas:
```html
<ul>
    <li>Lista desordenada</li>
    <li>Elemento de lista</li>
    <li>Otro elemento de lista</li>
</ul>

<ol>
    <li>Lista ordenada</li>
    <li>Elemento de lista</li>
    <li>Otro elemento de lista</li>
</ol>

```
Estas etiquetas <ul> y <ol> se utilizan para crear listas desordenadas y ordenadas, respectivamente. Los elementos de la lista se definen con la etiqueta <li>.

