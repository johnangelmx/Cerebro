Markdown es un lenguaje de marcado ligero para crear texto formateado utilizando un editor de texto sin formato. John Gruber y Aaron Swartz crearon Markdown en 2004 como un lenguaje de marcado que atrae a los lectores humanos en su forma de código fuente.

---
## Texto Plano
Para poder ingresar texto normal, simplemente lo ingresamos como cualquier otro documento:  

```markdown
Texto plano
```

---
## Títulos
Para ingresar títulos dependerá del número de almohadillas que tengan antes del texto del título, este controla el tamaño del título a su vez la importancia de ser título y subtitulo:  

```markdown
# Título nivel 1

## Título nivel 2

### Título nivel 3

#### Título nivel 4
```
--- 

## Formateo del texto
El formato del texto en Markdown es variado, pero a su vez son pocas las opciones que delimitan la edición del mismo, este mismo pensado para la mayor velocidad de escritura de documento, ejemplos:   

```markdown
**negrita la palabra**

*cursiva*

***negrita y cursiva***

___negrita y cursiva___
```  

>**Nota:**
	Markdown no permite el subrayado para no confundirlo con los enlaces. Ni tampoco más de dos líneas en blanco, si las ves las unificará en una, el espacio.

### Tachado del texto
También podemos tachar texto, para ello utilizamos el carácter llamado **~tilde**

```Markdown
Este ~~texto~~ está tachado

~~este texto va a ir tachado~~
```

### Marcar el texto 
Lo que si está permitido en Markdown es el marcado con color del texto.
```Markdown
El texto puede estar ==resaltado palabra== por ==palabra==
```

--- 
## Divisores 
A través de la lectura de este documente te habrás percatado de ciertos separadores de temas, estos permiten la separación de temas y de lecturas para que sea más fácil leerla y comprender lo que estás leyendo, para ello se utiliza los tres guiones:   

```Markdown
    --- 
```

### Presentaciones en Obsidian

Obsidian permite la función de presentación, la cual es una opción que hay que activar y que en cuanto entramos en modo presentación podremos ver nuestro documento como lo que mencionamos en una presentación como un PowerPoint .  
¿Y como delimitamos el texto que queremos por diapositiva?, de la misma forma que usamos los [Divisores](#Divisores), pero estos duplicados y limitados con un texto de no más de 2 párrafos:

```Markdown
	---
	presentacion 1 
	--- 
	presentacion 2
	--- 
```

Estos sin tabulaciones.

--- 
## Citas

Símbolo de mayor que y la cita:  

```Markdown
> 
```
Como resultado se verá así:  

> Lo importante no es lo que sabes, sino lo que haces con lo que sabes

---
## Casillas (Checkbox)
Markdown permite la creación de casillas de marcado, esto cotidianamente se usa para la gestión del tiempo:  

```Markdown
- [ ] Checkbox without marked

- [x] Checkbox marked
```
Como resultado: 

 - [ ] Checkbox without marked
 - [x] Checkbox marked

---
## Listas
Markdown te permite enlistar de la misma forma que lo hacemos con documentos normales.

### Listas sin enumerar 
Inicializamos con guion:

```Markdown
- artículo 1
- artículo 2
- artículo 3
```

Como resultado:  
- artículo 1
- artículo 2
- artículo 3

### Listas enumeradas

Inicializamos con número y podemos anidar listas una dentro de otras:

```Markdown
1. artículo 1

2. artículo 2

    1. artículo 1

    2. artículo 2

    3. artículo 3

        1. artículo 1

3. artículo 3

4. artículo 4
```

Como resultado:
1. artículo 1

2. artículo 2

    1. artículo 1

    2. artículo 2

    3. artículo 3

        1. artículo 1

3. artículo 3

4. artículo 4
  
>**Nota:**
	Ojo, aquí ya podemos ver que la idea es que estos caracteres extra no ensucien la nota, inclusive ayuden en la edición a entender mejor el texto. Los propios caracteres con los que enriquecemos tienen todo el sentido en relación con el detalle visual que añaden, o sea, no molestan en absoluto al leer en el estado edición.

---
## Imágenes

Si copias cualquier imagen y la pegas en obsidian en este caso, ya nos adapta el formato Markdown para insertar imágenes de forma directa, que es este:
```Markdown
![[Pasted image 20230117214157.png]]
```

Como Resultado:   
![[Pasted image 20230117214157.png]]

>**Nota:**
	En obsidian no muestra la ruta porque esta imagen, al pegarla, la ha incluido dentro de su vault, de su sistema de archivos, de hecho está aquí.
  
### Enlace externo 
Pero si la imagen estuviera fuera del alcance del vault, o la carpeta raíz de obsidian, el formato sería así, sin la primera tabulación:

```Markdown
	![Alan Turing|100](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Alan_Turing_Aged_16.jpg/220px-Alan_Turing_Aged_16.jpg)
```

Como resultado: 

![Alan Turing](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Alan_Turing_Aged_16.jpg/220px-Alan_Turing_Aged_16.jpg)

### Redimensión de imagen
Pero si la imagen la queremos redimensionar, también podemos hacerlo de una forma muy sencilla, sin la primera tabulación:
```Markdown
	![Alan Turing|100](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Alan_Turing_Aged_16.jpg/220px-Alan_Turing_Aged_16.jpg)
```
Como Resultado: 

![Alan Turing|100](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Alan_Turing_Aged_16.jpg/220px-Alan_Turing_Aged_16.jpg)

Recordando que esto es en general, también se puede hacer con las imágenes alojadas en obsidian.

---
## Código en Markdown

Para el lector casual puede ser bastante abrumador pensar que porque usaría lenguaje de programación en mi documento, aunque si, esta herramienta es indispensable para los programadores, tiene un uso importante para las personas que quieran representar el lenguaje Markdown como lo hemos estado haciendo.

A lo largo de este documento has estado percibiendo las cajas en las cuales explico como ingresar cierta acción en nuestro documento Markdown , estás a su vez sirven para encasillar un fragmento de código y como actualmente has hecho puedes copiar y pegar en la utilización de tu propio documento.

Su uso se delimita en usar las comillas invertidas ` ``` `  después el lenguaje que usaras para representar lo que necesitas y nuevamente cerrar con tres comillas invertidas ` ``` `  : 

```js

function fancyAlert(arg) {

  if(arg) {

    $.facebox({div:'#foo'})

  }

}

```

---
## Comentarios en Markdown
Uno de los temas más importantes es el comentar texto en Markdown, este a su vez debió ser uno de los primeros temas a tratar y a utilizar, pero es imposible comprenderlo si no antes has habido comprender todo Markdown.

Los comentarios sirven para que únicamente la persona que está escribiendo el documento de Markdown pueda hacer anotaciones que sirven para el mismo, es decir, fragmentos de texto que no se verán en el modo lectura de Obsidian.

```Markdown
%% Comentario %%
```

La representación anterior cambio de manera que la caja de código no dice ==Markdown== sino Md, esto para que el mismo documento no oculte el comentario

%% Por ejemplo estas anotaciones  %%
%% Si puedes ver esto, estás en modo editor o modo live de obsidian %%

--- 

## Caracteres Markdown que no quieras compilar
Cuando quieras ingresar caracteres que son por defecto de Markdown, únicamente tienes que Añadir `\` (barra invertida) delante del carácter:

```Markdown
\[\[no compila

\*\*no compila
```

Como resultado:

\[\[no compila

\*\*no compila

--- 

## Tablas
Al igual que tablas de Excel en un documento en Word, Markdown te permite la integración de estas, pero tienes que respetar la estructura de la misma, puedes tener de cualquier tamaño, ya sea por filas o columnas: 

```Markdown
| Nombre | Valor |
| ------ | ------ |
| Docena | 12 |
| Centena | 100 |
```

Como resultado: 

| Nombre | Valor |
| ------ | ------ |
| Docena | 12 |
| Centena | 100 |

---
## Enlaces 

Los documento Markdown nos permiten la integración de enlaces en nuestro documento, esto porque Markdown fue pensado para la lectura en línea, desde una página y dispositivo tecnológicos, facilitando la captura de información más detallada.

---
### Enlaces externos con Markdown
Estructura de un enlace en Markdown 
```Markdown
[texto subrayado](direccion de enlace)
```
Si no se escribe un texto, aparecerá una flecha en obsidian.

Enlace en duro: 

```Markdown
https://obsidian.md/
```
Como resultado:       
https://obsidian.md/

Enlace estructurado:

```Markdown
Este es la [Web de Obsidian](https://obsidian.md/)
```
Como resultado:   
Este es la [Web de Obsidian](https://obsidian.md/)

>**Nota:**
	Ctrl+K sale el formato para incluir una URL en Obsidian

---
### Enlaces externos formato Obsidian

Recurso externo en mi equipo o red local, mediante obsidian, esto no es Markdown.
Es decir, la forma en la cual si queremos ir a buscar de manera interpretada por el sistema, un archivo o un sistema de archivo, hay ciertas reglas que seguir para poder tener una dirección de enlace correcta.

Reglas: 
-  `/` diagonal `%2F`
-  `  ` Espacio en blanco `%20`

```Markdown 
[Link to note](obsidian://open?path=D:%2Fpath%2Fto%2Fficheroquesea.md)
```
El ejemplo anterior sería si quisiéramos llegar a un archivo obsidian, pero los enlaces así , hay que comprenderlos de una forma que el computador pueda interpretarlo y obsidian también, no hace falta recordar esto, dado que es poco usado este enlace.

Como resultado:  
[Link to note](obsidian://open?path=D:%2Fpath%2Fto%2Fficheroquesea.md)

---
### Enlaces entre notas con Markdown
Como en los enlaces normales, podemos tener enlaces entre notas, y a su vez enlaces a un título en específico. 

Enlace a notas: 
```Markdown
[Texto del Enlace](Nombre%20nota.md)
```

Enlace a nota por sistema de archivos:
```Markdown
[Texto del Enlace]("C:\Users\UserName\Google Drive\Carpeta\SubCarpeta\Nota.md")
```

Enlace dentro de la misma carpeta:
```Markdown
[Texto del Enlace](Reglas%20Markdown.md)
```  

Enlace de ruta:
```Markdown
[Texto del Enlace](../carpeta-atras/nota.md)
```

Enlace a título dentro del documento:
```Markdown
[Texto del Enlace](#NombreTitulo)
```

---
### Enlaces entre notas con wiki links

Puedes utilizar wikilinks para crear enlaces internos entre tus entradas.

**¿Por qué usar Wikilinks?**  
No es necesario conocer la URL de la entrada enlazada para crear un wikenlace, basta con el nombre del archivo. Además, algunas aplicaciones para tomar notas, como Obsidian, crean y actualizan los wikilinks automáticamente.  

Estructura:

```Markdown
[[Enlace]]
```

La ventaja abismal que tiene los wikis links, comparación de los links convencionales, es la fácil detección en obsidian de documentos, los cuales puedes acceder sin necesidad de escribir enlaces de Markdown.

**Cambiar el texto del enlace**
Puede especificar opcionalmente el texto del enlace después de una tubería dentro de los corchetes: 

```Markdown
[[Otro post|Texto del enlace]]
```

Como resultado:
> Para un mejor manejo de obsidian consulta [[Obsidian Cheat Sheet |Obsidian Atajos ]]

---
**Autor**: Johnangelmx
**Fecha**: 2023-01-18 03:59
