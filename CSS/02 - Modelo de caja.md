El modelo de caja en CSS es una representación conceptual de cómo se estructuran y se visualizan los elementos HTML en una página web. Cada elemento HTML está contenido dentro de una caja rectangular que incluye el contenido, el relleno, el borde y el margen. Estos componentes determinan el tamaño y la posición del elemento en la página.

![[Pasted image 20231011034004.png]]

Las propiedades básicas del modelo de caja son:

- **width:** El ancho de la caja, incluido el relleno y el borde.
- **height:** El alto de la caja, incluido el relleno y el borde.
- **padding:** El ancho del relleno.
- **border:** El ancho del borde.
- **margin:** El ancho del margen.

![[Pasted image 20231011035020.png]]

---

## Resetear estilos en CSS

Por defecto muchas de las etiquetas HTML vienen de forma en el cual el navegador le incluye estilos a dichas etiquetas, esto puede ocasionar un problema al tratar de usar las medidas correctas, entonces usamos las siguientes líneas de código: 
```CSS
/* Resetear estilos  */

* {
    /* le dice que sume el padding con el width del elemento  */
    box-sizing: border-box;
    padding: 0;
    margin: 0;

}
```

- `box-sizing: border-box;` - Este valor le dice al navegador que incluya el relleno y el borde del elemento en el ancho y el alto del elemento.
- `padding: 0;` - Este valor establece el relleno del elemento en 0.
- `margin: 0;` - Este valor establece el margen del elemento en 0.