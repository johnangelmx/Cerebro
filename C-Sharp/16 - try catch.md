# Manejo de excepciones
`try-catch` es una estructura de control en C# (y en muchos otros lenguajes de programación) que se utiliza para manejar excepciones o errores durante la ejecución de un programa.

```cs
try
{
    // Bloque de código que puede lanzar una excepción
}
catch (TipoDeExcepción1 ex)
{
    // Manejo de la excepción TipoDeExcepción1
}
catch (TipoDeExcepción2 ex)
{
    // Manejo de la excepción TipoDeExcepción2
}
// Puedes agregar más bloques catch según sea necesario
finally
{
    // Bloque opcional que se ejecuta siempre, independientemente de si se lanzó una excepción o no
}

```

1. **`Try`**: La palabra clave `try` marca el comienzo del bloque de código donde se puede producir una excepción. Este bloque de código es aquel que queremos monitorear en busca de posibles errores.

2. **`Catch`**: Después del bloque `try`, puedes tener uno o más bloques `catch`. Cada bloque `catch` maneja un tipo específico de excepción que podría ser lanzada dentro del bloque `try`. Dentro de cada bloque `catch`, puedes escribir el código que maneja la excepción de manera apropiada.

3. **`Finally` (Opcional)**: Después de los bloques `catch`, puedes tener un bloque `finally`. Este bloque se ejecutará siempre, ya sea que se haya lanzado una excepción o no dentro del bloque `try`. Se utiliza comúnmente para realizar tareas de limpieza, como cerrar archivos o liberar recursos.

Véase como un manejo o modulador de errores en nuestro código, en ocasiones cuando nosotros programamos hay ciertos errores que no podremos identificar si lo hacemos de manera individual es decir:

Tomemos el siguiente ejemplo:
```cs
 int a = 1;
 int b = 0;
 int c = a / b;
 Console.Read();
```
Al ejecutarlo  tendremos un error, el cual sería:
![[Pasted image 20240527111547.png]]
Este es un error que en C-Sharp tiende a ocurrir, el cual dicta que no puedes dividir entre cero si tu primer número es mayor

---

## Para ello tendremos el try-catch

El `try-catch` tendremos una forma de poder manejar el código, ya sea en general o en individual, esto al manejar `excepciones`. 

>En cuestión de `excepciones` podremos tener una en general, otros predefinidos por el código , y otras creadas por nosotros.

Para manejar de manera general el problema de código anterior tendremos:
```cs
 int a = 1;
 int b = 0;

 try
 {
     int c = a / b;
 }
  catch (Exception ex)
 {
     Console.WriteLine("Hubo un error");
 }
```

El código anterior vemos que envuelve el código que podríamos vincular como erróneo, o que pueda saltar un código erróneo en una declaración `try` y el código que podríamos manejar si salta la excepción envuelta en un `catch`

Como resultado, en nuestro `IDE` no tendremos un marcado de error y el usuario tendrá:
![[Pasted image 20240527112426.png]]
Esto tiene como objetivo que el usuario no salga del flujo normal de su navegación o tarea.

# `Finally`
`Finally`  Es una declaración y palabra reservada que nos permite ejecutar un fragmento de código siempre y cuando halla un `try-catch` declarado, es decir, que no importa que se haya ejecutado en nuestro `try-catch` siempre va a ejecutar nuestro `finally`.

Funcionalidad principal prever que una declaración de código anterior tenga un fin, el ejemplo más simple, es que al hacer una consulta del `try-catch` hacia una base de datos, `finally` pueda cerrar la conexión y no quede conexiones abiertas.

```cs
int a = 1;
int b = 0;

try
{
    int c = a / b;
}
catch (Exception ex)
{
    Console.WriteLine("Hubo un error");
}
finally
{
    Console.WriteLine("Esto siempre se va a ejecutar");
}
```

Como resultado:
![[Pasted image 20240527112922.png]]

# Tipos de excepciones
Como hablamos anteriormente en el lenguaje c-sharp podemos encontrar una variedad de diferentes tipos de excepciones, algunas predefinidas y otras podemos crearlas.

```cs
   catch (IndexOutOfRangeException)
   {
       Console.WriteLine("Index");
   }
   catch (DivideByZeroException)
   {
       Console.WriteLine("DivideByZero");
   }
```

Este tipo de excepciones podremos manejarlas de forma tal que cuando sabremos que tipo de excepción pueda ocurrir en nuestro código podremos manejarlas cada una de cierta manera.

De no tener idea de como manejar dichas excepciones tendremos que crearla o manejar la excepción en "**General**":
```cs
catch (Exception ex)
{
    Console.WriteLine("Hubo un error");
}
```

### Creación de excepción

En C#, puedes crear excepciones personalizadas heredando de la clase `Exception`. Aquí tienes un ejemplo básico de cómo hacerlo:
```cs
using System;

// Definición de una excepción personalizada
public class MiExcepcionPersonalizada : Exception
{
    public MiExcepcionPersonalizada() { }
    public MiExcepcionPersonalizada(string message) : base(message) { }
}

class Program
{
    static void Main(string[] args)
    {
        try
        {
            // Lanzar la excepción personalizada
            throw new MiExcepcionPersonalizada("¡Esto es una excepción personalizada!");
        }
        catch (MiExcepcionPersonalizada ex)
        {
            // Manejar la excepción personalizada
            Console.WriteLine("¡Se ha producido una excepción personalizada!");
            Console.WriteLine("Mensaje: " + ex.Message);
        }
    }
}

```