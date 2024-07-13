Los comentarios en c-sharp nos permite desde agregar información extra, comentar código y para documentar el código en cuestión.

Comentario simple
```cs
//
```

Documentar el código:
```cs
 /// <summary>
 /// Metodo que sirve para sumar
 /// </summary>
 /// <param name="a"></param>
 /// <param name="b"></param>
 /// <returns></returns>
 private static int Suma(int a, int b)
 {
     return a + b;
 }
```

Al ingresar tres veces el signo `/` en Visual Studio, integra el fragmento de comentario del código anterior, ese fragmento permite con diferentes sistemas de integración de documentación, o simplificado en código , al hacer `hover `  en este caso cuando se llame esta función:

![[Pasted image 20240524151537.png]]

Visualizarlo de la siguiente manera
