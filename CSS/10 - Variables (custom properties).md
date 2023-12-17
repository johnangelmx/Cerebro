
El uso de variable a comparación de la programación normal, permite almacenar valores de cualquier propiedad de CSS, esto para poder reutilizar de manera limpia en varias declaraciones sin perder en el código ciertos valores

Aquí un ejemplo de ello: 
```CSS
:root {

    --primary-color: #003476;

    --secondary-color: #b4d2f7;

    --header-size: 4rem;

    --font: 1.8rem;

}
```

# Variables en CSS
- `:root`: Se refiere al elemento raíz del documento, que es el elemento HTML. Declarar las variables en `:root` las hace globales y accesibles en todo el documento.

    - `--nombre-variable`: Es el nombre que le das a tu variable, precedido por dos guiones (--). Puedes nombrarlas según su función para facilitar su comprensión.

    - `valor`: Es el valor que asignas a la variable. Puede ser cualquier valor de propiedad CSS, como colores, tamaños, márgenes, etc.

    Ejemplo:

    ```css
    :root {
      --color-primario: #3498db;
      --tamanio-fuente: 16px;
    }
    ```

## Uso de Variables

Una vez que has declarado las variables, puedes utilizarlas en otras partes de tu hoja de estilo. Para acceder a una variable, utiliza la función `var()`:

```CSS
.elemento {
      color: var(--color-primario);
      font-size: var(--tamanio-fuente);
    }
```

En este ejemplo, la clase `.elemento` hereda el color y el tamaño de fuente definidos por las variables.

## Modificación Dinámica

Las variables en CSS pueden ser modificadas dinámicamente mediante JavaScript, lo que permite cambiar estilos en tiempo real. Utiliza el método `setProperty` para actualizar el valor de una variable:

```javascript
document.documentElement.style.setProperty('--color-primario', '#ff5733');
```

Esto cambiará el color primario a un tono de naranja.

En resumen, las variables en CSS proporcionan una manera eficiente de gestionar y reutilizar valores en tu hoja de estilo, facilitando el mantenimiento y la modularidad del código. Su flexibilidad y capacidad para ser modificadas dinámicamente las convierten en una herramienta poderosa en el desarrollo web.
