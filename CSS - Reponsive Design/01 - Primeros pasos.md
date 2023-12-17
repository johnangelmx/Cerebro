# Responsive Design
En el mundo del desarrollo web existe una infinidad de dispositivos en los cuales se podrá acceder tu página, para ello debemos tener en cuenta que lo que hemos visto hasta ahora, solo lo hemos implementado en laptop o PC de escritorios, son pantallas grandes y de mayor tamaño, pero la existencia de más dispositivos nos obliga a adaptarnos a todos ellos, claramente no sabremos en qué dispositivos se visualizará nuestro proyecto, para ello tenemos las medias queries.
## Medias Queries
En CSS existe algo llamado Media Queries, estas permiten manipular todo el CSS que hemos escrito antes, para poder adaptarlos a diferentes dispositivos.

Lo que hace es poner `breakpoitns` (puntos de quiebre) , que permite detectar el ancho del dispositivo en el que se está abriendo la página, ejemplo:

```CSS
@media ( min-width: 480px){
	*Codigo para ese tamano de dispositivo , como un movil...*
}
```
Es decir, si el dispositivo tiene un ancho mínimo de 480px, entonces las reglas para ese tamaño serían las que están entre ese `breakpoint`. 
### Mobile First/ Only
En el desarrollo de una página prever, el mayor sector de usuarios que visitaran la página es esencial, y hoy en día , todos tienen un celular, y al primer alcance de información siempre se accederá desde el celular.

Por ello existe una arquitectura de desarrollar primero la vista desde el celular, sé que podría ser un poco confuso, porque te preguntaras ¿cómo es que importa más el celular que la búsqueda en escritorios? Pues bueno, aparte de lo ya mencionado que los celulares son lo que todo el mundo tiene, también permite crear un diseño más rápido y conciso, es decir de a dentro hacia afuera.

![[Pasted image 20231211043509.png|450]]

Algo a tener en cuenta es que la mayoría de recursos que verás en internet, las media queries y breakpoints, están en la misma hoja de estilos principal, es decir, todo está junto, lo cual no es malo, pero sí es una mala práctica.

Para buenas prácticas primero desarrollaremos la primera hoja de estilos en "mobile first" y después un archivo para cada cierto tipo de dispositivos, ya se `tablet.css`, `desktop.css`, etc. Una vez teniendo esta separación de archivos, lo que permitirá que sea una buena práctica es que se le asigne el breakpoint directamente desde el HTML, a qué me refiero con esto, que le podremos decir al navegador: 

"Tengo estilos para mi página en diferentes tamaños, escoge y descarga únicamente el que se adecúe a tu tamaño de pantalla"

![[Pasted image 20231211043737.png|500]]

