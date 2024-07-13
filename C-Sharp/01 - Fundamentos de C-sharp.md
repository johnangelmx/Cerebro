# Historia de C-Sharp
- Se pronuncia C Sharp
- Lenguaje de programación orientado a objetos 
- Tiene soporte para programación orientada a componentes
- Es un lenguaje Type-Safe

# Propiedades de C-Sharp
- Es parte del framework .NET
	- .NET agrega herramientas que permite la integración de base de datos , para procesar páginas web, etc.
- Es un lenguaje basado en C
- Comparte Sintaxis con C, C++ y Java
- Crear aplicaciones multiplataforma
	- Windows ( Escritorio, tabletas móviles)
	- iOS (Xamarin. IOS)
	- Android (Xamarin. Android)
	- Mac y Linux (Proyecto Mono)

# Sintaxis básica
La sintaxis que usa C-sharp es muy parecida a la de java, pues en un principio esa era la idea, tener una alternativa a java de ese entonces, pero hoy en día ha desarrollado su camino, basándonos en que no solo es un lenguaje orientado a objetos, sino que es un lenguaje orientado a componentes.

> La **programación orientada a componentes** (que también es llamada _basada en componentes_) es una rama de la [ingeniería del software](https://es.wikipedia.org/wiki/Ingenier%C3%ADa_del_software "Ingeniería del software"), con énfasis en la descomposición de sistemas ya conformados en componentes funcionales o lógicos con [interfaces](https://es.wikipedia.org/wiki/Interfaces "Interfaces") bien definidas usadas para la comunicación entre componentes.


```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Holamundo
{
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
}

```

# Hola mundo
```cs
   static void Main(string[] args)
        {
            // Permite imprimir en consola
            Console.WriteLine("Hola mundo");
            // Permite ingresar datos en el CLI
            Console.Read();
        }
```

Como resultado: 
![[Pasted image 20240520125838.png]]

