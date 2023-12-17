## Malas Practicas
```HTML
<body>
    <main>
        <div class="picture">
            <img src="img/large.jpg" alt="">
        </div>
    </main>
</body>
```
```CSS
.picture {
    width: 500px;
    height: 400px;
}

img {
    width: 100%;

}
```

¿Por qué esto se considera mala practica? 
Para empezar semánticamente está mal implementado,  hoy en día tenemos etiquetas que puedan especificar que estaremos utilizando una imagen de por medio, tenemos también una imagen que al ser tan pesada, no solo va a cargar para navegador, sino que también va a cargar en teléfonos, lo cual hace que la descarga de la imagen sea pesada y que en una pantalla tan pequeña perdamos calidad.
## Buenas Prácticas
```HTML
<body>
    <main>
        <picture>
            <source media="(min-width: 1300px)" srcset="./img/large.jpg">
            <source media="(min-width: 1000px)" srcset="./img/medium.jpg">
            <img src="./img/small.jpg" alt="Una persona arriba de una montana">
        </picture>
    </main>
</body>
```
```CSS
img{
    width: 100%;
}
```
La forma correcta de manipular imágenes es ponerlos alrededor de la etiqueta `<picture>`, con dicha etiqueta podremos manipular el tamaño deseado, pero la etiqueta `<img>` siempre tiene que tener un `width` del 100%, esto vuelvo a recalcar sirve para tener una mejor manipulación del tamaño, y dicha manipulación se tiene por medio de la etiqueta `<picture>` a esta etiqueta se le asignará el tamaño deseado.

Una vez hemos manipulado el tamaño de la imagen con las etiquetas `<picture>` y `<img>`, tenemos que hablar de optimización de la página, para ello, como mencionamos antes, el usuario de teléfono no tiene que descargar lo mismo que el usuario de teléfono, tiene que ser diferente la experiencia de ambos y por ello siempre hay que tener presente que al tener una imagen debemos tener por lo menos 3 tamaños por cada imagen en nuestra página.

- Grande (`large`)
- Mediano (`medium`)
- Pequeño (`small`)

Una vez teniendo los recursos que utilizaremos, en este caso las imágenes, tendremos que usar la etiqueta `<source>` dicha etiqueta permite el uso de cierta imagen en específico en casos específicos, es decir, que al igual al uso de `mediaquerys` o `breakpoints`, con la etiqueta `<source>` podremos darle al usuario la imagen adecuada al dispositivo que esté usando.

```HTML
<source media="(min-width: 1300px)" srcset="./img/large.jpg">
```

- **media:** Este atributo especifica las condiciones en las que se debe utilizar la fuente. En este caso, la fuente se utilizará cuando la anchura mínima de la ventana del navegador sea de 1300 píxeles.
- **srcset:** Este atributo especifica una lista de fuentes alternativas, cada una con su propio tamaño y resolución. En este caso, la única fuente alternativa es `./img/large.jpg`, que tiene un tamaño de 1920 x 1080 píxeles.

Es esencial subrayar la importancia de la secuencia al redactar las etiquetas `<source>` dentro de la estructura HTML. Se recomienda encarecidamente seguir un orden de mayor a menor al especificar los puntos de quiebre (`breakpoints`), es decir, comenzar con el `breakpoint` de mayor tamaño y continuar de manera descendente. Este principio se ejemplifica en el siguiente código:

```HTML
     <source media="(min-width: 1300px)" srcset="largeImage.ext">
     <source media="(min-width: 1000px)" srcset="mediumImage.ext">
     <source media="(min-width: 800px)" srcset="smallImage.ext">
```

Observamos que se inicia con el breakpoint de 1300px, seguido por 1000px y 800px respectivamente. Esta disposición estratégica es fundamental para asegurar una correcta visualización de las imágenes asociadas con los respectivos breakpoints en función del ancho de la pantalla. Si no se respeta este orden, podrían surgir dificultades al intentar presentar adecuadamente las imágenes según los diferentes puntos de quiebre.
	
Esto permitirá que si el tamaño del dispositivo en el que se está viendo sea un teléfono, entonces los recursos que se descarguen en un principio siguiendo el patrón mobile first, sea **small.jpg,** tendremos la imagen en el teléfono de la siguiente forma: 

![[Pasted image 20231217092634.png|400]]
Y el único recurso que se habrá descargado será el **small.jpg**:

![[Pasted image 20231217092722.png]]

Y así será de igual forma con las condiciones de los `breakpoints` y los recursos que le hallamos asignado con la etiqueta `<source>`.
