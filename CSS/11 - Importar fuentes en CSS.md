# Grupos de Familias de Fuentes

Para entender la importancia de las fuentes en los navegadores hay que establecer que el navegador por defecto cuenta con 5 grupos de familia de fuentes que son: 

- **Fuente genérica** estándar (`Generic Font Family`):** Esta es la fuente predeterminada utilizada por el navegador si ninguna otra fuente está especificada. Puede variar según el navegador y el sistema operativo.
    
- **Fuente Serif (`Serif`):** Incluye fuentes que tienen pequeños detalles en los extremos de las letras, conocidos como "serifas". Ejemplos son Times New Roman y Georgia.
    
- **Fuente Sans-serif (`Sans-serif`):** Consiste en fuentes que carecen de serifas, lo que les da una apariencia más limpia y moderna. Algunos ejemplos son Arial, Helvetica y Verdana.
    
- **Fuente de ancho fijo (`Monospace`):** Todas las letras tienen la misma anchura, lo que es útil en contextos donde la alineación vertical es crítica, como en la programación. Ejemplos incluyen Courier New y Consolas.
    
- **Fuente matemática (`Cursive`):** Esta fuente se utiliza para representar contenido matemático. Algunos navegadores pueden interpretar esto como una fuente cursiva. Ejemplos son cursive y fantasy.

Esto se encuentra en navegadores, cabe decir que es un estándar en todos los navegadores el uso de estos 5 grupos de familia de fuentes
![[Pasted image 20231209071126.png|500]]

## ¿Qué significa grupos de familia de fuentes?

Entendimos anteriormente que existe este tipo de grupos o "categorías" de fuentes, que tiene el navegador

¿Pero qué incluye los grupos o que abarcan? 
En una explicación poco adecuada podrás ver en la siguiente imagen que:
- `serif` corresponde a una fuente de texto que aplica una pequeña línea a las letras que tiene extremos, como la `T` la `N` y la `R`
- `sans-serif` corresponde a una fuente de texto que aplica curvaturas a las líneas que tiene extremos
- `cursive` corresponde a una fuente de texto que aplica la escritura de palabras con base en que no haya espacio de entre letras de cada palabra.
- `monospace`  Corresponde a una fuente de texto que aplica la escritura de letras entre palabras con un espacio igualitario entre letras, esto permite la lectura de mejor manera
![[Pasted image 20231209070204.png]]

# Fuentes en CSS
Una vez entendido el funcionamiento de las fuentes en el navegador, tendremos que tener en cuenta que siempre que vayamos a usar una fuente externa, es crucial especificar a qué clase de grupo de fuentes corresponde. Esto se logra mediante la propiedad CSS llamada `font-family`.

Por ejemplo, si deseamos utilizar una fuente externa que pertenezca al grupo sans-serif, la declaración CSS podría lucir así:
```CSS
font-family: 'NombreDeLaFuente', Arial, sans-serif;
```
Y te preguntarás, ¿como voy a saber a qué grupo de fuentes pertenece la fuente qué deseo usar?
La mayoría de páginas de fuentes gratuitas contiene el grupo de fuentes que corresponde a la fuente que quieres importar, en [Google Fonts](https://fonts.google.com/) podrás encontrar un apartado así:

![[Pasted image 20231209072956.png]]
Como señala la imagen, la fuente a importar es `'Roboto'` y la fuente corresponde al grupo `sans-serif`

## Tipos de estilos en la fuente
Sé que en este punto puede resultar abrumador considerar la amplia gama de estilos de fuentes disponibles, como itálicas, medianas, negritas, entre otros. Sin embargo, esta parte es fundamental, y como desarrollador web, elegir cuidadosamente los estilos de fuente es esencial para garantizar una presentación coherente y atractiva del contenido en el sitio web.

### Importancia de los Estilos de Fuente en Google Fonts

En Google Fonts y otros servicios similares, la variedad de estilos de fuente ofrece a los desarrolladores una flexibilidad significativa en la presentación visual de sus proyectos. Algunos de los estilos comunes incluyen:

1. **`Regular` (normal):** Este es el estilo estándar de la fuente y se utiliza para el texto normal del contenido.
    
2. **`Italic` (itálica):** La versión itálica de una fuente proporciona un estilo inclinado o cursiva. Puede ser útil para resaltar texto sin usar negrita y agregar énfasis de una manera sutil.
    
3. **`Bold` (negrita):** La variante negrita de una fuente es más gruesa y se utiliza para resaltar o enfatizar ciertas secciones de texto. Es efectiva para títulos y encabezados.
    
4. **`Bold` `Italic` (negrita itálica):** Combina la negrita y la versión itálica, proporcionando un texto más destacado y enfatizado.
    
5. **`Light` (ligera):** Un estilo ligero ofrece una versión más delgada de la fuente. Puede ser útil para ciertos estilos de diseño más delicados.
    
6. **`Medium` (mediana):** Este estilo se encuentra entre el regular y el `bold` en términos de grosor. Puede ser útil cuando se desea un texto enfatizado pero no tan audaz como con la negrita.
    
Tienes que recordar que al importar estos tipos de estilos los podremos usar en nuestro CSS de la siguiente manera: 
```CSS
p{
 font-family: 'Roboto',sans-serif;
 font-style: bold; /*italic, medium, regular*/
 font-weight: 700; /*400,500,600 ...*/
}
```

# Importación de Fuentes
  
Ahora que hemos abordado la relevancia de las fuentes en un proyecto, es esencial comprender que existen dos tipos principales de fuentes: las importadas localmente y las importadas externamente. Las fuentes locales residen dentro del servidor que aloja el proyecto web, mientras que las fuentes externas están disponibles a través de sitios web que ofrecen opciones tanto gratuitas como de pago.

Gratuitas: 
1. `**Google Fonts:`** [Google Fonts](https://fonts.google.com/) proporciona una amplia variedad de fuentes gratuitas que se pueden incorporar fácilmente en proyectos web. Ofrece una interfaz fácil de usar y la posibilidad de personalizar la selección de fuentes.
    
2. **`Font Squirrel:`** [Font Squirrel](https://www.fontsquirrel.com/) es otra plataforma que ofrece fuentes de alta calidad de forma gratuita. Además, proporciona herramientas para ayudar a los usuarios a convertir fuentes para su uso en diferentes plataformas.
    
3. **`DaFont:`** [DaFont](https://www.dafont.com/) es un recurso popular que alberga una amplia colección de fuentes gratuitas creadas por diseñadores. Los usuarios pueden explorar diversas categorías y descargar las fuentes de su elección.
    
4. **`FontSpace:`** [FontSpace](https://www.fontspace.com/) es una comunidad en línea que permite a los diseñadores compartir y descargar fuentes gratuitas. Ofrece una amplia variedad de estilos y categorías.
    
5. **`1001 Fonts:`** [1001 Fonts](https://www.1001fonts.com/) es un sitio que alberga una extensa colección de fuentes gratuitas para diversos propósitos. Los usuarios pueden explorar, previsualizar y descargar fuentes de manera sencilla

Para esta documentación usaremos gratuitas de [Google Fonts](https://fonts.google.com/)

![[Pasted image 20231209074744.png]]
En la imagen podrás ver que en la barra de búsqueda seleccionamos `roboto`, esto despliega estilos varios de esta fuente, y a la derecha nos despliega un apartado de estilos seleccionados y el cómo los importará

Y para finalizar hay que tener en cuenta las buenas prácticas:

![[Pasted image 20231209070155.png]]