## Clonar Líneas
Esta función permite la creación rápida de líneas de código seleccionada: 

```VSCode
Shift + Alt + ↑ / ↓
``` 

>**Nota:** Clonar líneas no crea multi cursores.

---

## Crear Cursores Arriba Y Abajo De La Posición Actual
Como recordamos en la sección [[03- Edicion Basica#Seleccionar todas las ocurrencias de la selección|Seleccionar todas las ocurrencias de la selección]], VS Code nos permite la creación de multi cursores, esta herramienta potencia la manera de escribir código, en especial al momento de hacer tareas repetitivas. 

Crear múltiples cursores para editar:
```VSCode
Ctrl + Alt+ ↑ / ↓
```

La creación de múltiples cursores, nos ayudará a escribir más rápido como el siguiente ejemplo, si desea puede tomarlo como un ejercicio:
```HTML
<!-- Desde aquí -->
<li>Hola Mundo</li> <!-- A partir de aqui usar Ctrl + Alt+ ↑ / ↓-->
  
  
  
  
  
  

<!-- Hasta aquí -->

<!-- Objetivo -->
<li>Hola Mundo</li>
<li>Hola Mundo</li>
<li>Hola Mundo</li>
<li>Hola Mundo</li>
<li>Hola Mundo</li>
<li>Hola Mundo</li>
```


---

## Multi Cursor Específico
En VS Code podremos utilizar el ratón para poder crear multi cursores, los cuales nos ayudaran cuando no tengamos la forma en la cual poner los multi cursores como queramos.

```VSCode
Mantener Alt + Doble click    Para seleccionar la palabra
Mantener Alt + Seleccionar    Para seleccionar varias palabras
```

Ejemplo:
![[Pasted image 20230122222104.png]]
La creación de dicho multi cursores no solo es por medio de palabras, sino también por varias palabras, esta herramienta se utiliza cuando no tengamos forma de hacerlo con [[#Crear Cursores Arriba Y Abajo De La Posición Actual|Cursores en línea]]

---

## Crear Múltiples Cursores Usando El "Next Find Match"
```VSCode
Ctrl + D
```
Esta nos permitirá seleccionar todas las ocurrencias de arriba hacia abajo, es decir, proporcionará la selección de la siguiente ocurrencia y asignándole un multi cursor.


--- 
