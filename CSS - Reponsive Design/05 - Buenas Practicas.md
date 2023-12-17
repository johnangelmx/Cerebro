# Buenas prácticas Responsive Design

## Separación de `BreakPoints`
Es una buena recomendación la separación de los `breakpoints` de los archivos CSS y separarlos por archivos únicos.

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

