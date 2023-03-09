### Comando inicial
```git
git
```
Permite la visualización de ayuda de git.

### Versión
```git
git --version
```
Permite ver la versión instalada de git.

### Configuración inicial nombre
```git
git config --global user.name "Nombre"
```
Permite la visualización o cambio al insertar el nombre del nombre global en git.

### Configuración inicial email
```git
git config --global user.email "johnangelmx@gmail.com"
```
Permite la visualización o el cambio al insertar el email en git.

### Configuración inicial rama main
```git
git config --global init.defaultBranch main
```
Permite el cambio del nombre por defecto de la rama principal por defecto.

### Configuración inicial editor
```git
git config --global core.editor "nombre-editor-texto"
```
Permite el cambio del editor de texto que usara git 

--- 
### Inicializar Git
```git
git init 
```
Inicia el repositorio, es decir, Crea el directorio `.git` y permite usar git.

### Comandos Flujos Basicos 
![[Pasted image 20230306134746.png]]

---
## Git Status
git status es una herramienta que te ayuda a saber qué cambios has hecho en tus archivos y te muestra si hay algo que aún no has guardado. De esta manera, puedes mantener un registro de tus cambios y asegurarte de que todo esté organizado antes de guardar tus cambios definitivamente.

```git
git status
```


--- 
## Git Add
```git
git add <nombre archivo>
```
git add es un comando que te permite seleccionar los cambios que deseas guardar en tu proyecto y prepararlos para ser guardados de manera definitiva en el repositorio. En resumen, es el primer paso para guardar tus cambios en Git.

### Git Restore --Staged
Permite restaurar un archivo del staged, es decir, unos instantes antes del `git add` 
```git
git restore --staged <archivo>
```

---
## Git Commit
```git
git commit -m 'mensaje'
```
Git commit es el comando que utilizas para guardar definitivamente los cambios que seleccionaste con git add. Al hacer un commit, guardas los cambios de manera permanente en el historial del proyecto y agregas un mensaje que describe los cambios realizados. En resumen, git commit es el último paso para guardar tus cambios en Git.

### Git commit 
Permite ingresar un mensaje del commit más largo, con más caracteres.
```git
git commit 
```
Esto permitirá escribir el mensaje en el [[Comandos Iniciales Git#Configuración inicial editor|editor de texto]] previamente configurado

### Git commit --amend
Permite enmendar un mensaje escrito en el último commit
```git
git commit --amend -m "mensaje corregido"
```

---
## Git Log

```git 
git log 
```
Git log es un comando que te permite ver todos los cambios que se han realizado en tu proyecto, junto con información sobre quién hizo los cambios, cuándo los hizo y qué cambios realizó. En resumen, git log es una herramienta útil para ver la historia del proyecto y rastrear los cambios realizados.

--- 
## Git Show
Permite ver los cambio dentro de los hash de los commits
```git
git show <hash>
```
