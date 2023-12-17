Existen dos tipos de imágenes, sin perdida o con perdida, y esto depende de como el formato maneja las imágenes.

# Lossy vs. Lossless

La principal diferencia entre los formatos de imágenes sin pérdida y con pérdida radica en la calidad de la imagen y el tamaño del archivo resultante. Los formatos sin pérdida, como PNG, conservan todos los detalles de la imagen original, pero pueden generar archivos más grandes. Por otro lado, los formatos con pérdida, como JPEG, comprimen la imagen para reducir el tamaño del archivo, pero pueden perder algo de calidad en el proceso.

## Lossless

Sin perdida

Los formatos de imagen sin perdida capturan todos los datos de su archivo original. No se pierde nada del archivo original, foto u obra de arte, de ahí el término “sin perdida”. El archivo aún puede estar comprimido, pero todos los formatos sin perdida podrán reconstruir su imagen a su estado original.

## Lossy

Con perdida

Los formatos de imagen con perdida se aproximan a su imagen original. Por ejemplo, una imagen con perdida podría reducir la cantidad de colores en su imagen o analizar la imagen en busca de datos innecesarios. Estos reducirá el tamaño del archivo, aunque pueden reducir la calidad de su imagen.

Por lo general, los archivos con perdida son mucho más pequeños que los archivos sin perdida, lo que los hace ideales para usar en línea donde el tamaño del archivo y la velocidad de descarga son vitales.

---

# Formatos de imagen

- JPEG: Ampliamente utilizado para fotografías en línea debido a su capacidad de compresión y tamaño de archivo más pequeño.
- PNG: Preferido cuando se necesita una imagen sin pérdida de calidad, como logotipos o gráficos con transparencia.
- GIF: Utilizado a menudo para animaciones simples.
- BMP: Comúnmente utilizado en aplicaciones y sistemas operativos.

Es importante elegir el formato de imagen adecuado según las necesidades específicas de cada proyecto.

## PNG 8 - Lossless

Portable Network Graphics

Es un formato de imagen sin pérdida que admite hasta 256 colores. Es ideal para imágenes con áreas planas de color y transparencia, como logotipos y gráficos simples.

## PNG 24 - Lossless

Portable Network Graphics

Es un formato de imagen sin pérdida que admite hasta 16 millones de colores. Se utiliza cuando se necesita una alta calidad de imagen y transparencia, como fotografías o ilustraciones detalladas.

## JPG / JPEG - Lossy

Photographic Experts Group

JPEG es un formato de imagen con pérdida que se utiliza ampliamente para fotografías en línea debido a su capacidad de compresión y tamaño de archivo más pequeño. Es ideal cuando se necesita equilibrar la calidad de la imagen con el tamaño del archivo.

## SVG - vector / lossless

Scalable Vector Graphics

SVG es un formato de archivo gráfico vectorial que utiliza un lenguaje de marcado basado en XML para representar imágenes. Las imágenes SVG se pueden escalar sin pérdida de calidad y se pueden comprimir sin pérdida de calidad.

![[Pasted image 20231010014950.png]]

---

# Optimizando Imágenes

Tamaño promedio de una imagen web es de 70 kB - 100 kB

- Mejora el tamaño de tus imágenes
    
    - Tiny PNG
    
    [TinyPNG – Compress WebP, PNG and JPEG images intelligently](https://tinypng.com/)
    
- Retira meta datos de tus imágenes
    
    - Verexif
    
    [Ver Exif online , quitar Exif online](https://www.verexif.com/)
    

---

# Etiqueta img y figure

Desglosemos el siguiente código:

```html
<section>
	<figure>
			<img src="./pics/tinified/small.jpg" alt="Perrito corriendo con fondo arboles de pinos">
			<figcaption>Perrito corriendo atraves de pinos</figcaption>
	</figure>
</section>

```

Lo que vemos es la forma correcta y semánticamente bien colocada, para poder manipular imágenes en HTML. Pero empecemos con la etiqueta `img`.

La etiqueta `img` no tiene cierre, es decir, es una etiqueta única, y esta se tiene que poner dos atributos, el `src` y el `alt`, el `src` permite decirle donde se ubica el archivo original, este puede estar dentro del mismo proyecto o un enlace externo, y el `alt` permite de manera correcta describir la imagen en caso de que esta se extravíe , pierda o se escriba incorrectamente sin que el usuario deje de saber que se situaba ahí.

**¿Por qué hablamos tanto de semántica?**

La semántica es importante en el diseño web porque ayuda a los navegadores a comprender el significado de la página. Esto permite que los navegadores rendericen la página de manera correcta y que los motores de búsqueda la entiendan y la indexen de manera adecuada.

**¿Por qué es importante la semántica?**

- **Buenas prácticas:** Las etiquetas semánticas permiten describir de manera clara y concisa el contenido de la página web. Esto ayuda a que el navegador entienda el significado de la página y que la renderice de manera correcta.
- **SEO:** Los motores de búsqueda utilizan la semántica para comprender el contenido de las páginas web. Al utilizar etiquetas semánticas, las páginas web son más fáciles de entender para los motores de búsqueda, lo que puede mejorar su clasificación en los resultados de búsqueda.
- **Compatibilidad con navegadores:** Las etiquetas semánticas son estándares y son compatibles con todos los navegadores modernos. Esto ayuda a garantizar que las páginas web se vean correctamente en todos los dispositivos.

**Conclusión:** La semántica es un aspecto importante del diseño web que tiene beneficios para la usabilidad, el SEO y la compatibilidad con diferentes navegadores.

### Uso de `<figure>` y `<figcaption>`

Las etiquetas `<figure>` y `<figcaption>` se utilizan en HTML para agrupar y etiquetar el contenido multimedia, y se utilizan junto con la etiqueta `<figcaption>` para proporcionar una leyenda o descripción para el contenido multimedia.

**Etiqueta `<figure>`**

La etiqueta `<figure>` se utiliza para agrupar el contenido multimedia, como imágenes, gráficos, tablas, diagramas, fragmentos de código, etc. El contenido de la etiqueta `<figure>` se representa como un bloque independiente del flujo principal del documento.

**Etiqueta `<figcaption>`**

La etiqueta `<figcaption>` se utiliza para proporcionar una leyenda o descripción para el contenido multimedia contenido en la etiqueta `<figure>`. La etiqueta `<figcaption>` se coloca dentro de la etiqueta `<figure>` y se utiliza para proporcionar información adicional sobre el contenido multimedia.

---
## Etiqueta de video

```html
<section>
	<video controls preload="auto">
		<source src="./GODS.mp4#t=30,60">
		<source src="./GODS.m4v#t=30,60">
	</video>
</section>\
```


El elemento `<section>` crea una sección en la página web. El elemento `<video>` representa el video que se va a reproducir. La etiqueta `controls` indica al navegador que muestre controles para el video, como un botón de reproducción/pausa y un control deslizante de tiempo. La etiqueta `preload="auto"` indica al navegador que cargue automáticamente el video cuando la página web se cargue por completo.

Los elementos `<source>` especifican la ruta a los archivos de video que se pueden reproducir en el elemento `<video>`. La etiqueta `#t=30,60` indica al navegador que el video debe comenzar a reproducirse desde los 30 segundos hasta los 60 segundos.

En resumen, este código HTML creará un elemento `<video>` que mostrará el video `GODS.mp4` o `GODS.m4v` desde los 30 segundos hasta los 60 segundos, si es posible.

Aquí hay una explicación más detallada de cómo funciona este código:

1. El navegador intentará cargar primero el archivo MP4.
2. Si el archivo MP4 no se puede encontrar o no se puede cargar correctamente, el navegador intentará cargar el archivo MOV.
3. Una vez que el navegador haya cargado uno de los archivos de video, comenzará a reproducirlo desde los 30 segundos hasta los 60 segundos.

Este código puede ser útil para mostrar un video específico a los usuarios, sin que tengan que esperar a que se cargue por completo. Por ejemplo, podrías usar este código para mostrar un video de introducción a los visitantes de tu sitio web, o para mostrar un video tutorial a los usuarios que están aprendiendo a usar tu producto.