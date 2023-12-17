# Layout Shifter
El patrón de diseño Layout shifter es uno de los patrones de diseño responsive más comunes. Se basa en la idea de que el contenido de una página web se puede dividir en bloques que se pueden reacomodar de forma diferente según el ancho de la pantalla.

En el caso de dispositivos móviles, el contenido se suele mostrar apilado en columnas verticales. A medida que la pantalla se vuelve más grande, los bloques se pueden reacomodar en columnas horizontales, o incluso en una sola columna.

Este patrón es muy flexible, ya que permite que el contenido se ajuste a cualquier ancho de pantalla. Sin embargo, también es el más complejo de implementar, ya que requiere que los bloques de contenido sean completamente independientes entre sí

![[Pasted image 20231211074927.png]]

## Reglas
Las reglas del patrón de diseño Layout shifter son las siguientes:

- **El contenido debe dividirse en bloques independientes.** Cada bloque debe poder mostrarse de forma independiente en cualquier ancho de pantalla.
- **Los bloques deben estar bien organizados.** Los bloques deben estar bien organizados para que el contenido sea fácil de encontrar y navegar.
- **Los cambios de diseño deben ser suaves.** Los cambios de diseño deben ser suaves para evitar que el usuario se distraiga o se confunda.
## Explicación
Se que puede ser confuso en este punto del porqué es diferente a lo que hemos implementado con el patrón "Mostly Fluid", bueno, la mejor forma de explicar dicho patrón es la reorganización de elementos a medida que crece, es decir, manipular los elementos de tal modo que pueda ser coherente y mejor visto los bloques ya sea verticalmente u horizontalmente.

El siguiente ejemplo demuestra el objetivo, omite el tono gris que sé denota en cada cuadro;

![[Pasted image 20231214055804.png]]

Empecemos por lo que sabemos, **mobile firts**:
![[Pasted image 20231214060859.png|100]]
Como podemos observar son 3 secciones, las cuales la primera de arriba hacia abajo correspondería a una `navbar` (barra de navegación), la segunda y la tercera a un contenido apilado `wrap` las 3 están en forma de columna.

El segundo para un tamaño de iPad: 
![[Pasted image 20231214061231.png]]
El contenido aún sigue apilado, extendido de anchura `width` y de altura `height`, aún no ha cambiado del todo.

El tercero para una pantalla de escritorio estándar:
![[Pasted image 20231214061537.png]]
Aquí es donde patrón "**Layout Shifter**" se hace presente y adquiere, a como su nombre lo indica, un cambio de diseño en una medida en específico. La barra de navegación cambia para tomar el lugar de una columna de navegación y el contenido de los dos bloques de información ahora se apilan a la derecha de la columna de navegación. Lo que permite una experiencia de usuario más amena a lo que el tamaño del dispositivo lo requiera.

El cuarto y último diseño es para una pantalla de escritorio más grande: 
![[Pasted image 20231214062100.png]]
Es aquí donde el programador tomara la decisión de cambiar más el diseño para un sector de pantallas más grandes o como la imagen lo demuestra el diseño se queda fijo en una medida y no perderá la idea principal que tenía para su página.

## Ejemplo Proyecto
Ya que tenemos una idea de como es el cambio de "**Layout Shifter**", que en pocas palabras sería el cambio de estilos de diseño en cada **Breakpoint** (Punto de quiebre), hagamos el **layout** de la imagen:
![[Pasted image 20231211074927.png]]

### Antes de empezar
A comparación de otras lecciones, es crucial hacer una aclaración importante aquí. A lo largo de esta documentación, hemos observado que el uso de unidades relativas y absolutas varía según el propósito que le demos a nuestro proyecto. Cuando comenzamos un proyecto desde cero, las mejores prácticas sugieren el uso exclusivo de unidades relativas, como porcentajes. Esta elección nos permite aprovechar al máximo el espacio disponible en la pantalla y garantiza que nuestro proyecto sea receptivo a una amplia gama de dispositivos y tamaños de pantalla.

Sin embargo, conforme avanzamos en la fase de desarrollo, nos damos cuenta de que el uso de unidades absolutas puede volverse crucial para lograr una precisión específica en la disposición de elementos. Esto es especialmente relevante cuando necesitamos establecer dimensiones exactas o posiciones fijas para ciertos elementos en la interfaz.

Es fundamental tener en cuenta la naturaleza dinámica del diseño web y la evolución de las mejores prácticas a lo largo del tiempo. Por lo tanto, recomendamos evaluar cuidadosamente las necesidades de cada proyecto y ajustar el enfoque en consecuencia.

Además, es importante destacar que el uso de unidades relativas no se limita exclusivamente al tamaño de la pantalla. También se extiende a otros elementos, como márgenes, rellenos y fuentes, brindando así una flexibilidad adicional en la adaptación del diseño.

En resumen, la elección entre unidades relativas y absolutas no es estática, sino más bien una consideración estratégica que debe ajustarse a las particularidades y requisitos de cada proyecto en distintas etapas de su desarrollo. Al ser conscientes de esta dinámica, podemos tomar decisiones informadas que optimicen tanto la adaptabilidad como la precisión en el diseño de nuestras interfaces web.

---


Iniciemos partiendo que tendremos que tener 4 bloques: 
```HTML
<body>
    <main class="container">
        <section class="box box__block1">
        </section>
        <div class="group1">
            <section class="box box__block2"></section>
            <section class="box box__block3"></section>
        </div>
        <section class="box box__block4"></section>
    </main>
</body>
```
En este apartado empezaremos a usar él [[01 - CSS - Introduccion#Pseudoclases y la importancia del BEM|BEM]] , e integraremos un grupo de secciones con la clase `.group1` esto nos servirá para poder organizar de mejor manera la agrupación de los contenedores que por la imagen ya te habrás dado cuenta que se organizan de diferente manera.

Ahora inicialicemos el CSS:

```CSS
* {
    box-sizing: border-box;
    padding: 0;
    margin: 0;
}

html {
    height: 100%;
    font-size: 62.5%;
}

body {
    height: 100%;
    font-size: 1.6rem;
}
```
En este apartado hay algo diferente a otras inicializaciones que hemos hecho, si no leíste el apartado [[#Antes de empezar]], vamos a trabajar únicamente con porcentajes en este ejemplo, por ello el `html` tiene la propiedad valor `height: 100%` que a su vez lo hereda el `body`, todo esto para que al iniciar el proyecto el body ya tenga un 100% del tamaño de la pantalla al iniciar.

![[Pasted image 20231214064918.png|500]]
![[Pasted image 20231214064939.png]]

## Mobile view

```HTML
<body>
    <main class="container">
        <section class="box box__block1">
        </section>
        <div class="group1">
            <section class="box box__block2"></section>
            <section class="box box__block3"></section>
        </div>
        <section class="box box__block4"></section>
    </main>
</body>
```
```CSS
.container {
    height: 50%;
    display: flex;
    flex-flow: row wrap;
    align-content: flex-start;
}

.box {
    height: 100px;
    width: 100%;
    border: 1px solid #21405f;
}

.box__block1 {
    background-color: #154e87;
}

.box__block2 {
    background-color: #fcfeff;
}

.box__block3 {
    background-color: #9cdbff;
}

.box__block4 {
    background-color: #d0f282;
}
```

`.container`
- Tiene la altura de 50% del 100% de la pantalla que se esté visualizando, claramente esto es para este ejemplo.
- Contiene las configuraciones de flex para que se organicen en fila, que se apilen, y que el apilado se acomode al inicio.

`.box`
- Tiene una altura de 100px y un ancho del 100%
- Tiene un borde de 1 pixel, sólido y de color azul

`.box__block1`al `.box__block4`
- Tiene cada uno la asignación de cada color individual.

Como resultado tenemos:
![[Pasted image 20231215131421.png|250]]

El problema que tenemos aquí es que no podemos visualizar 2 secciones, como tenemos envuelto `.box__block2` y `.box__block3` en `.group1` esto para que podamos organizar de mejor manera en el siguiente `breakpoint` esto porque es parte del patrón Layout Shifter.

Con lo siguiente resolveremos el problema
```CSS
.group1 {
    flex: auto;
}
```
Recordemos que `.group1` es un hijo de `.container`. Al asignarle `flex: auto`, indicamos que puede crecer y encogerse según sea necesario, tomando automáticamente el tamaño disponible. Dado que las dos secciones ya tienen tamaños predefinidos, ocuparán el espacio que necesiten y se visualizarán sin problemas. El resultado final será el siguiente:
![[Pasted image 20231215132306.png|250]]

## iPad view
El diseño de iPad, requiere una manipulación de dichos contenedores de manera que se vea así: 
![[Pasted image 20231215132458.png]]

Para ello trabajaríamos de la siguiente manera:
```CSS
@media (min-width:600px) {
	.container{
        height: 100%;
    }
    .box__block1 {
        width: 33.3%;
        height: 50%;
    }

    .group1 {
        width: 66.3%;
        display: flex;
        flex-flow: row wrap;
    }

    .box__block2,
    .box__block3 {
        height: 50%;
    }

    .box__block4 {
        height: 50%;
    }
}
```

1. El contenedor podrá ocupar todo el alto de la pantalla.
2. El primer bloque ahora tendrá un ancho reducido del 33% y una altura aumentada del 50%.
3. El grupo 1 que contiene el bloque 2 y 3, tomara el ancho de 66% e indicará ahora que los elementos tenga configuraciones flexibles, se acomodara en forma de fila y se podrán apilar uno sobre otro.
4. Que los bloques 2 y 3 tomaran la altura del 50% del padre que es grupo 1.
5. Que el bloque 4 ocupe la altura del 50%.

Teniendo como resultado: 
![[Pasted image 20231215133422.png|300]]

## Desktop view
El diseño de escrito, requiere una manipulación de contenedores y orden entre ellos:

![[Pasted image 20231215133510.png]]

Para ello trabajaríamos de la siguiente manera:
```CSS
@media (min-width: 800px) {
    .container {
        height: 80%;
        margin: 10% auto;
    }

    .box__block1 {
        order: 3;
        width: 33.3%;
        height: 100%;
    }

    .group1 {
        order: 2;
        width: 33.3%;
        height: 100%;
    }

    .box__block4 {
        order: 1;
        width: 33.3%;
        height: 100%;
    }
}
```

1. El contenedor tendrá el tamaño del 80% de la pantalla y le asignamos un espacio de 10% en la parte superior e inferior del mismo.
2. El bloque 1 le asignaremos el orden 3, tendrá un ancho de 33% y podrá ocupar el 100% de la altura.
3. Al grupo 1 le asignamos el orden 2, tendrá un ancho de 33% y podrá ocupar el 100% de la altura.
4. El bloque 4 le asignamos el orden 1, tendrá un ancho de 33% y podrá ocupar el 100% de la altura.

Como resultado: 
![[Pasted image 20231215134235.png|400]]


## Comentarios Finales

Los patrones de diseños son creados para la visualización de manera amena del usuario, el patrón layout shifter esto implica la personalización por cada tipo de dispositivo, una experiencia diferente, esto para nosotros los programadores significa cambios de posición y tamaño en los diferentes breakpoints, que como finalidad se trabajaría hacia la experiencia del usuario únicamente.