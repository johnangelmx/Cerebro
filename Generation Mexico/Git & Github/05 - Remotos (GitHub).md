# Conectarse a GitHub por medio de SSH
El primer paso es generar las llaves [[Llaves SSH para uso en Github]]
Cabe resaltar que puede tener algún token para la autenticación del repositorio.

![[Pasted image 20230313133950.png]]

---

## Clonar repositorio
Para ello tendremos que tener un repositorio, ya creada, o un repositorio ya trabajado.
Con las herramientas SSH nos permite tener un sistema de autenticación dentro de nuestro entorno de trabajo, es decir, nos permite la subida de archivos con contraseña, a diferencia del Token que se nos pedirá el token único proporcionado por GitHub.

Clonamos con SSH:
```Shell
git clone git@github.com:johnangelmx/Prueba_Git.git
```

## Git Remote

Una herramienta importante es `git remote` es un comando en Git que se utiliza para gestionar las conexiones entre el repositorio local y los repositorios remotos.

Con `git remote`, puedes listar, agregar y eliminar repositorios remotos asociados con tu repositorio local. También puedes obtener información sobre un repositorio remoto en particular, como la dirección URL y el nombre del repositorio.

En términos prácticos, la gestión de conexiones con `git remote` implica agregar, listar, renombrar y eliminar repositorios remotos, lo que te permite establecer una comunicación efectiva entre tu repositorio local y los repositorios remotos asociados.

Por ejemplo, si estás trabajando en un proyecto en equipo, es posible que cada miembro tenga su propio repositorio remoto para enviar sus cambios. En este caso, debes agregar los repositorios remotos de tus compañeros a tu repositorio local utilizando `git remote add`. De esta forma, podrás descargar los cambios que ellos hayan realizado y enviar los tuyos a sus repositorios remotos correspondientes.

```Shell
git remote
git remote -v
```

Como resultado:
```Shell
origin  git@github.com:johnangelmx/Prueba_Git.git (fetch)
origin  git@github.com:johnangelmx/Prueba_Git.git (push)
```

En este ejemplo, "`origin`" es el nombre del repositorio remoto, y se muestra dos veces porque se utiliza para "`fetch`" (descargar cambios desde el repositorio remoto) y "push" (enviar cambios al repositorio remoto). Luego, se muestra la dirección URL correspondiente a cada operación.

En resumen, `git remote -v` es una herramienta útil para obtener información detallada sobre los repositorios remotos vinculados a tu repositorio local.

## Subiendo Cambios al Repositorio
Actualmente con los pasos anteriores tenemos las herramientas para tener un repositorio remoto, pero hay un diferenciador que tendremos en cuenta, al tener nuestro git y cambios de forma local, estos no se suben automáticamente al repositorio, eso lo tendremos que hacer nosotros.

Digamos que tenemos todos los `commit` listos y son los que queremos subir al dar un: 
```Shell 
git status
```
Tendremos una respuesta como: 
```Shell
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

Esto significa que has realizado uno o más commits en tu rama local que aún no se han enviado al repositorio remoto. Por lo tanto, si deseas sincronizar tu repositorio local con el repositorio remoto, deberás enviar esos cambios al repositorio remoto utilizando el comando `git push`.

## Git Push
`git push` es un comando de Git que se utiliza para enviar los cambios realizados en tu repositorio local a un repositorio remoto. Es decir, "empuja" los commits locales que aún no están presentes en el repositorio remoto, actualizando así la versión del repositorio remoto con los últimos cambios realizados en tu rama local.

La sintaxis básica de `git push` es la siguiente:
```Shell
git push <remote> <branch>
```
Donde `<remote>` es el nombre del repositorio remoto y `<branch>` es el nombre de la rama a la que deseas enviar los cambios.

Por ejemplo, si deseas enviar los cambios de tu rama local `main` al repositorio remoto `origin`, debes ejecutar el siguiente comando:
```Shell
git push origin main 
```

## Bajando Cambios Al Repositorio
Tenemos el repositorio en GitHub, pero ¿qué pasaría si estamos trabajando con otra persona? Bueno, llegaríamos a ver los cambios de esta otra persona y trabajar con ellos, así colaborando en el mismo lugar, claramente esto tendría conflictos a evaluar. 

Trabajar en un repositorio de GitHub con alguien puede ser una experiencia desafiante, especialmente si hay conflictos en el proceso. Los conflictos pueden ocurrir cuando varias personas están trabajando en el mismo archivo o línea de código al mismo tiempo y hacen cambios que pueden chocar entre sí.

Pero más adelante los evaluaremos

## Git Pull
`git pull` es un comando de Git que se utiliza para obtener y fusionar los cambios realizados en un repositorio remoto en el repositorio local. Básicamente, se utiliza para actualizar el repositorio local con los cambios realizados en el repositorio remoto.

Cuando ejecutas el comando `git pull`, Git descarga los cambios realizados en el repositorio remoto y los fusiona con los cambios realizados en el repositorio local. Si no hay conflictos, la fusión se realiza de forma automática y los cambios se aplican al repositorio local.

La sintaxis básica de `git pull` es la siguiente:
```Shell
git pull <remote> <rama> 
```
Por ejemplo, si deseas enviar los cambios de tu rama remota `main` al repositorio local, debes ejecutar el siguiente comando:
```Shell
git pull origin main 
```

Si hay conflictos, Git te notificará y te pedirá que resuelvas los conflictos manualmente antes de continuar con la fusión. Para ello, deberás abrir los archivos afectados, resolver los conflictos y hacer un nuevo commit.

