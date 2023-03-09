Git es un sistema de control de versiones que te permite rastrear los cambios que realizas en los archivos de tu proyecto. Con Git, puedes guardar diferentes versiones de tus archivos y volver a versiones anteriores si es necesario. 

Además, Git te permite trabajar en equipo de manera colaborativa, permitiendo a múltiples personas trabajar en el mismo proyecto al mismo tiempo. También te permite fusionar diferentes versiones del código para combinar el trabajo de diferentes personas. En resumen, Git es una herramienta muy útil para desarrolladores de software y cualquier persona que necesite rastrear y colaborar en cambios de archivos.

## Ejemplo 

Imagina que estás escribiendo un libro y guardas diferentes versiones en tu computadora a medida que avanzas. En algún momento, decides que quieres eliminar un capítulo completo y volver a la versión anterior del libro. Si no has estado utilizando Git, es posible que pierdas todo el trabajo que hiciste en ese capítulo, pero si utilizas Git, podrás ver todas las versiones anteriores de tu libro y volver a una versión anterior sin perder tu trabajo. Además, si estás trabajando en equipo con otros escritores, Git te permitirá combinar fácilmente diferentes versiones del libro y mantener un registro de quién hizo qué cambios.

--- 
## Empezando con git - Comandos Iniciales

>Nota: Cuando estemos trabajando en consola, el `--` (menos menos) viene una palabra completa
>En cuanto a solo un `-` (menos) Significa que lo que venga después son abreviaturas 

```git
git --version
```
Nos proporciona la versión de Git.

```git
git help
```
Nos Proporciona una ayuda en cuanto en la línea de comando, esto es útil para cuando olvidamos ciertas funciones.

```git
git help <comando>
```
También puedes proporcionar directamente el comando al que quieres tener más información.

--- 
## Configuraciones Iniciales
Cuando empecemos con git, tendremos que proporcionar información inicial para que, de cierta forma, las modificaciones tengan un autor, para ello Iniciaremos con:

**Configurar Globalmente El Nombre De Usuario**
```git
git config --global user.name "Nombre-Usuario"
```

**Configurar Globalmente El Email Del Usuario**
```git
git config --global user.email "Email"
```

Con estas dos configuraciones, git por defecto trabaja mucho con la confianza del usuario que trabaja este equipo, es decir, la persona que tiene acceso el computador es la persona que solo va a manipular el repositorio.

**Visualizar Configuración Global**
```git
git config --global -e 
```
Permite ver en un editor de texto, en mi caso VIM![[Pasted image 20230307092909.png]]
