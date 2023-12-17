# Column Drop
El patrón **Column Drop** es un patrón de diseño responsive que consiste en dividir el contenido de una página web en columnas. Estas columnas se distribuyen horizontalmente en pantallas grandes, pero se apilan verticalmente en pantallas pequeñas.

La idea es que el contenido sea fácil de leer y navegar en cualquier dispositivo, ya sea un ordenador, una tablet o un smartphone.

![[Pasted image 20231217050331.png]]

El ordenamiento esperado es una manipulación de contenedores de información apilados en teléfonos y dispersos a medida que crezca la pantalla del dispositivo.

## Reglas 

- **Utiliza un sistema de cuadrícula.** Un sistema de cuadrícula ayudará a mantener el diseño consistente en diferentes tamaños de pantalla.
- **Elige un ancho de columna adecuado.** El ancho de columna debe ser lo suficientemente ancho para que el contenido sea legible y utilizable en dispositivos móviles.
- **Evita el desbordamiento de contenido.** Asegúrate de que el contenido no se desborde de la pantalla en dispositivos móviles.
- **Utiliza animaciones o transiciones suaves.** Las animaciones o transiciones suaves ayudarán a que el cambio de diseño sea más fluido.

## Explicación
Este patrón tiene como objetivo la distribución de información de manera dinámica , el contenido tendrá que ser coherente, a medida que crezca los contenedores el contenido tendrá que tener mejor organización de información

## Ejemplo Proyecto
Vamos a generar un ejemplo a partir de la imagen de esta sección.

## Mobile view
```HTML
<body>
    <main class="container">
        <div class="c1"></div>
        <div class="c2"></div>
        <div class="c3"></div>
        <div class="c4"></div>
        <div class="c5"></div>
    </main>
</body>
```
```CSS
/*.... Cofiguraciones iniciales*/
.container {
    display: flex;
    flex-wrap: wrap;
}

.c1,
.c2,
.c3,
.c4,
.c5 {
    width: 100%;
    min-width: 150px;
    height: 150px;
}
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
    background-color: #b0e4b3;
}
.c5 {
    background-color: #e4badd;
}
```

Como resultado: 
![[Pasted image 20231217062049.png|250]]

En este punto la explicación será más simple, a medida que reconoceremos que lo que vemos no es más que un ordenamiento de contenedores que se apilan uno sobre otro, el contenedor padre no cambiara de tamaño, por lo que queremos que crezca con los contenedores hijos y lo de más del código CSS es para asignarle ciertos colores a diferenciar.

## iPad view
Para demostrar de forma simple el patrón **Column drop,** lo que haremos a continuación es el ordenamiento de dos contenedores en una misma fila, es decir, reduciremos el tamaño para que puedan caber en la misma fila.

```CSS
@media (min-width: 600px) {
    .c1 {
        width: 25%;
        order: 1;
    }

    .c2 {
        width: 75%;
        order: 2;
    }

    .c3 {
        width: 100%;
        order: 3;
    }

    .c4 {
        width: 100%;
        order: 4;
    }

    .c5 {
        width: 100%;
        order: 5;
    }
}
```

El código aplica una asignación de tamaños con porcentajes, esto nos ayuda a calcular de mejor manera los contenedores, y aplicamos un ordenamiento para poder manejar que los contenedores no cambien de lugar.

Como resultado: 

![[Pasted image 20231217062522.png|400]]

## Desktop view
Ahora que ya tenemos la idea un poco clara del patrón, sigamos con los contenedores restantes, esto, al ser un ejemplo, no estamos tomando a cuenta el contenido dentro de dichos contenedores, cuando vayas a manipular tamaños para que ocupen la misma fila procura también considerar que la información dentro de los mismos sea coherente. 

```CSS
@media (min-width:800px) {
    .c1 {
        width: 30%;
    }

    .c2 {
        width: 40%;
    }

    .c3 {
        width: 30%;
    }

    .c4 {
        width: 50%;
    }

    .c5 {
        width: 50%;
    }
}
```
Ahora la manipulación que hemos hecho es que en la primera fila, tendremos 3 contenedores que ocuparan diferentes tamaños, pero coexistirán juntos, en la segunda fila, con los 2 contenedores restantes les asignaremos el tamaño igualitario para que ambos ocupen la misma fila.

Como resultado: 

![[Pasted image 20231217062921.png|400]]

## Comentarios finales
Hemos visto 3 tipos de patrones a lo largo de esta sección, dichos patrones no son los únicos que existen, pero son los más utilizados a la hora de manipular información, existen otros de manera que se utilizan procedimientos más elaborados para poder obtener el resultado deseado, dichos procedimientos son el uso de JavaScript para poder manipular el DOM y tener mejor interacción con el usuario, pero no quita que el uso exclusivo de CSS como estos patrones sean de mejor manera más rápido y optimizados. 

El patrón column drop es enfocado a la distribución de información de manera amena, es decir, que el usuario sí tiene una interfaz amigable, pero la importancia no recae en que el usuario tenga la mejor experiencia de navegación, sino que el usuario pueda encontrar y ver la información que él está buscando de manera simple y limpia. 
