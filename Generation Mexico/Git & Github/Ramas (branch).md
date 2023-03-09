# ¿Qué son las Ramas (`branch`) en Git?
Las ramas en Git son como versiones separadas de un proyecto en el que estás trabajando. Digamos que estás escribiendo un libro y quieres tener una versión con el final feliz y otra con el final triste. Puedes crear dos ramas: una rama "final feliz" y otra rama "final triste". Luego puedes trabajar en cada rama por separado, hacer cambios en cada final y guardarlos en su propia rama. 

De esta manera, no mezclas los cambios y siempre puedes volver atrás o comparar las dos versiones fácilmente. ¡Es como si tuvieras dos libros diferentes en tu computadora, pero sin duplicar todo el trabajo!

![[Pasted image 20230308050139.png]]

## Conocer Ramas
Para identificar en que ramas estas, o cuantas ramas existen utilizas el comando: 
```git
git branch
```

## Crear Rama
Para poder crear una nueva rama tendrás que situarte en la rama en la cual quieres duplicar y crear una nueva, como consiguiente tendrás que ingresar el siguiente comando: 
```git 
git branch <nombre-de-la-nueva-rama>
```

## Cambiar entre Ramas
Para poder cambiar el lugar en el que te encuentras entre ramas tendrás que ingresar el siguiente comando: 
```git
git checkout <nombre-rama>
```

## Fusionar Ramas
Esto permite fusionar los cambios, tienes que situarte en la rama en la cual quedara la fusión, e ingresar el siguiente comando:
```git
git merge <nombre-rama>
```
Es decir, pararnos sobre la rama en la cual queremos hacer fusión , y traer los cambios desde la rama que queramos.