# Primeros Pasos Con Git

Inicializar un espacio de trabajo o un repositorio
```Shell
git --init
```

>Recomendación: Usar `main` y no `master` 

## Carpeta `.git`

![[Pasted image 20230309055812.png]]
Esta carpeta tiene como finalidad guardar los cambios, los cuales serán los que ayuden a git a mantener un control. La eliminación de esta carpeta es la misma eliminación de todo lo que hagamos con git, así que la recomendación es no tocar, a menos que sepas lo que haces.

---
## Entendiendo el flujo de trabajo de git 

### Analogía Escenario y Fotografía

Imagina la siguiente analogía, tenemos documentos dentro de un espacio de trabajo, carpeta o repositorio, los cuales queremos respaldar información, crear una versión a través del tiempo de esos documentos. 

Para ello con git tendremos dos estados, un **Staging** y **Commits**, pero usemos la analogía del escenario (`staging`) y la fotografía (`commit`), los documentos que vayamos a tomar una fotografía tienen que estar en el escenario, y para ello podremos agregarlos simplemente poniéndolos en el mismo. 

Git tiene tres pasos para los cuales podremos crear versiones de nuestros documentos a través del tiempo, y como cualquier documento tendremos que primero verificar si ya podemos o no incluirlo en el escenario, una vez listo podremos ponerlo en el escenario y este estará a la espera de que le tomen la foto o que más documentos entren al escenario, Una vez que ya tengamos en el escenario los documento que necesitamos tomarle una fotografía podremos tomar dicha foto y guardarla a través del tiempo.

Tomando la analogía anterior, ahora podremos ver paso a paso lo que pasa en git.

---
### git status
Permite ver dentro del repositorio los documentos, los cuales no tienen seguimiento, no están en el `stage`, han sido modificados dentro del `stage` o han sido modificados después de algún `commit`
```Shell
git status
```

---
### git add
Permite añadir los documentos al `staging` (Escenario), se refiere a la fase intermedia antes de confirmar o "commitear" cambios en un archivo.

Para incluir todos los documentos dentro del repositorio staging:
```Shell
git add .
```

Para incluir documentos específicos al staging:
```Shell
git add <archivo1> <archivo2> ...
```

Para incluir todos los documento de un mismo tipo
```Shell
git add *.<nombre-de-la-extension-del-archivo>
```
Ejemplo *Archivos HTML*:
```Shell
git add *.html
```

Para incluir todos los documento de un mismo tipo de un directorio
```Shell
git add <directorio>/*.<extension>
```
Ejemplo *Archivos JS, en un directorio llamado js*:
```Shell
git add js/*.js
```

#### Quitar elementos del `staging`
Puede que no queramos que un archivo o archivos estén en el `staging`  o no hallamos hecho la modificación correcta, para ello podemos utilizar: 
```Shell 
git reset <archivo1> <archivo2> ...
```

---
### git commit
Un commit es como una fotografía instantánea de los archivos en un momento determinado, lo que permite registrar y mantener un historial de cambios en el tiempo

Comando para agregar los cambios de archivos en seguimiento y hacer con `commit` al mismo tiempo:
```Shell
git commit -am "Mensaje-Del-Commit"
```

Comando usual, permite hacer el `commit` y el parámetro `-m` nos permite incluir un mensaje
```Shell
git commit -m "Mensaje-Del-Commit"
```

---
## Restaurar repositorio de commit's 
Hasta este punto hemos visto el flujo habitual para versionar un repositorio, pero ¿Cómo restauro un documento u todo el repositorio de una versión guardada?

### git checkout
Restaurar todo el repositorio del último commit:
```Shell
git checkout -- .
```

---
## Archivos Git Útiles

**Git Keep**
```Shell
.gitkeep
```
Permite la integración de una carpeta vacía, por defecto git no toma en cuenta carpetas vacías , pero hay veces que son necesario en la integración de nuestro proyecto, por ello la existencia del .gitkeep. 
Suele estar vació

