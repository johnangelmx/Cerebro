## Movimiento de líneas
```VSCode
Alt + ↑ / ↓
```

---
## Movimiento de varias líneas
Seleccionaremos el texto con: 
```VSCode
Shift + ↑ / ↓
```
Y una vez seleccionado podremos usar [[#Movimiento de líneas]]:  
```VSCode
Alt + ↑ / ↓
```

---
## Comentarios
```VSCode
Ctrl + /
```

---
## Comentar partes del código
Si queremos comentar solo una parte seleccionada del código:
```VSCode
Shift + Alt + A
```

Ejemplo comentaremos con el atajo [[#Comentar partes del código]] la palabra amet, como resultado tendremos:    
```html
<div>
    <p>
        Lorem ipsum dolor sit <!-- amet --> consectetur adipisicing elit.
        Eum maiores nostrum cum quasi totam.
    </p>

</div>
```

---
## Creación rápida de archivos

Para la creación rápida de archivo, carpeta u ambos tendremos que definir la ruta como si ya estuviera creado el archivo, a su vez dando el siguiente comando , nos preguntara si deseamos crear la ruta especificada:
```VSCode
Ctrl + Clic derecho
```
Ruta de ejemplo: 
```javascript
<script src="assets/js/app.js"></script>
```
Al no tener ni la carpeta, ni el archivo, al dar clic en VS Code podremos crear al instante .


---
## Ir a la definición

```VSCode
Ojear definición   Ctrl + F12
Ir a la definición F12
Ir a la definición Ctrl + Clic
```

---
## Seleccionar todas las ocurrencias de la selección
Para poder seleccionar todos los fragmentos de texto que se repitan en el código tendremos que seleccionar el texto y luego: 
```VSCode
Ctrl + Shift + L
```

Esto permitirá la selección de todas las veces que se repita en el documento el texto seleccionado, una vez selección todas las ocurrencias podremos copiar, cortar, pegar, editar y eliminar dichas ocurrencias

---
## Borrar líneas
Para poder eliminar líneas de código tendremos que usar el atajo:
```VSCode
Ctrl + Shift + K
```

Ahora bien, este atajo puedes usarlo con el atajo "[[#Seleccionar todas las ocurrencias de la selección]]"  ambos podrás eliminar todas las líneas de código que tengan las mismas ocurrencias, haciéndola un par de herramientas asombrosas.

---
## Deshacer y Rehacer
```VSCode
Ctrl + Z Deshacer
Ctrl + Shift + Z Rehacer
```

---
## Zen Mode
VS Code nos permite un modo en el cual podremos ocultar barras laterales, superiores e inferiores, teniendo una vista más cómoda de tu código 
```VSCode
Ctrl + K Z
```

---
## Terminal integrada
```VSCode
Ctrl + `
```

---
## emmet wrap 

Existe una forma en la cual podremos seleccionar un fragmento de código y asignarle etiquetas ==HTML== de una manera rápida, lo que conocemos como emmet wrap abbreviation.

Primero seleccionaremos el fragmento de código a envolver en etiquetas, luego con el atajo [[02- General#Mostrar la paleta de comandos|Mostrar la paleta de comandos ]], buscaremos ==emmet wrap abbreviation==  y en el recuadro: 

![[Pasted image 20230122104454.png]]
Podremos elegir el nombre de dichas etiquetas a envolver.

---
## Manejo de ventanas equivalente a navegadores
Como te abras dado cuenta, VS Code nos permite la manipulación de ventanas de la misma manera que se desarrolla en navegadores, claramente con algunos cambios, pero la navegación es la misma en cuando espacio de trabajo se refiere, para ello no explicaremos cada uno de ellos dado que si usas un navegador ya deberías haber conocido estos atajos: 

```VSCode
Ctrl + W            Cerrar tab
Ctrl + K  Ctrl + W  Cerrar todas
Ctrl + Shift + T    Reabrir anterior
Ctrl + TAB          Cambiar de tab
```

---

Siguiente parte [[04- Multi Cursor y edicion rapida]]
