Los `namespaces` son utilizados para instancia un código fuera de la región.  Un `namespace` (espacio de nombres) es una forma de organizar y controlar el ámbito de las declaraciones en un programa. Puedes pensar en ellos como contenedores que agrupan clases, estructuras, interfaces, delegados y otros `namespaces` relacionados. Esto ayuda a evitar conflictos de nombres entre diferentes partes de un programa.

```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
namespace ConsoleApp1
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string estatusOperacion = "K15";

            if (estatusOperacion == EstatusOperaciones._exitoso)
            {
                // ....
            }
            else if (estatusOperacion == EstatusOperaciones._clienteNoEncontrado)
            {
                // ....
            }
            else if (estatusOperacion == EstatusOperaciones._errorDelSistema)
            {
                // ....
            }
            Console.Read();

        }
    }
}

namespace Operaciones
{
    public static class EstatusOperaciones
    {
        public const string _exitoso = "K120";
        public const string _clienteNoEncontrado = "P4";
        public const string _errorDelSistema = "K15";
    }

}

```

Imagina el siguiente escenario, tenemos un problema con el alcance que pueda tener el `namespace`, conforme al código requerido.

Bien, hasta ahora ya sabemos que un `namespace` permite que podamos contener en un lago diferente de nuestro código , un código almacenado. Pero como accedemos a él?

# `Using`
  
En C#, la palabra clave `using` tiene varios usos, pero uno de los más comunes es facilitar el acceso a tipos (como clases, estructuras, interfaces, etc.) que están definidos en un `namespace` específico.

En el apartado anterior tendríamos la interrogante de como podríamos poner al alcance un `namespace`. El uso de `using` en nuestro código nos permite la importación a ciertos elementos manipulados, como el caso de `namespace`:

```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

// Codigo using
using Operaciones;

namespace ConsoleApp1
{
	...
```

Con esto en nuestro código tenemos acceso al `namespace` **Operaciones**.