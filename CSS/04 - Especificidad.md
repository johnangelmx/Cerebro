¿Cómo se controla el orden al declarar CSS?

1. Importancia
2. Especificidad 
3. Orden en las fuentes

## Importancia

1. Hoja de estilo de agente de usuario (Estilos del navegador)
2. Declaraciones normales en hojas de estilo de autor (Nuestro .css)
3. Declaraciones importantes en hojas de estilos de autor (utilizar el !important)

## Especificidad
![[Pasted image 20231016053321.png]]

### Regla de cascada
![[Pasted image 20231016053616.png]]

### Orden de las fuentes 
En tus estilos, las declaraciones al final del documento anularán a las que sucedan antes en caso de conflicto.


---
La especificidad en CSS es un concepto fundamental que determina cuál regla de estilo se aplicará cuando varias reglas compiten por estilizar un mismo elemento HTML. Se mide en términos de cuán específica, es una regla en la selección de elementos HTML y se representa mediante un conjunto de cuatro valores que determinan su peso. Estos valores son: el número de ID selectors, el número de class selectors, el número de type selectors (elementos HTML) y el número de pseudo-selectores utilizados en una regla. Estos valores se suelen representar en una notación específica, como (a, b, c, d), donde "a" representa el número de IDs, "b" el número de clases, "c" el número de elementos HTML y "d" el número de pseudo-selectores.

Para entender mejor la especificidad, considera este ejemplo:
```CSS
/* Regla 1 */
p {
  color: blue;
}

/* Regla 2 */
#miParrafo {
  color: red;
}

/* Regla 3 */
p.miClase {
  color: green;
}

```

En este ejemplo, tenemos tres reglas de estilo que compiten por estilizar un párrafo (`<p>`) con la clase "miClase" y el ID "miParrafo". Ahora, veamos cómo se calcula la especificidad para cada regla:

- Regla 1: (0, 0, 1, 0) - Un selector tipo (elemento HTML).
- Regla 2: (1, 0, 0, 0) - Un selector ID.
- Regla 3: (0, 1, 1, 0) - Un selector tipo (elemento HTML) y un selector de clase.

En este caso, la Regla 2 tiene la mayor especificidad debido al selector de ID. Por lo tanto, el párrafo con el ID "miParrafo" se mostrará en rojo.

Acerca de tu pregunta sobre VS Code, la numeración que mencionas (1, 0, 0 o 0, 2, 0) se utiliza comúnmente en herramientas de desarrollo, editores de código y extensiones para mostrar la especificidad de una regla CSS. Por ejemplo, si ves que una regla tiene una especificidad de (0, 2, 0), significa que tiene dos selectores de clase en esa regla y ningún otro tipo de selectores. Esto te ayuda a comprender por qué una regla en particular está siendo aplicada en lugar de otra cuando hay conflictos en tu CSS.

En resumen, la especificidad en CSS es crucial para determinar qué regla se aplicará cuando hay conflictos en las hojas de estilo. Entender cómo se calcula la especificidad y cómo se representan sus valores puede ayudarte a escribir CSS más efectivo y a solucionar problemas en tu código de manera más precisa. Además, las herramientas como VS Code proporcionan información sobre la especificidad para facilitar el proceso de desarrollo.