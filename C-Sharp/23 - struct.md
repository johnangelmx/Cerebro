Una `struct` un tipo de valor que nos permite guardar lo que queramos en él.

- `struct`: tipo de valor que podemos definir.
- `class`: tipo de referencia que podemos definir.

Podemos tener campos, propiedades, indexadores, constructores, metodos, todo lo que pusimos en una clase, podemos usarlo es una estructura `struct`.

¿Cuándo usarla? 

En general, una estructura se utiliza cuando las instancias de una estructura tenga un corto tiempo de vida.

En C#, tanto los `struct` como las clases son herramientas que te permiten organizar y estructurar tu código al agrupar datos relacionados. Sin embargo, existen algunas diferencias importantes entre ellos.

1. **Definición y Uso**:
    
    - **Clases**: Las clases son tipos de referencia en C#. Esto significa que cuando creas una instancia de una clase, estás creando una referencia a un objeto en la memoria. Puedes crear métodos dentro de las clases para operar en los datos y puedes pasar instancias de clases como parámetros a métodos y funciones.
    - **Structs**: Por otro lado, los `struct` son tipos de valor. Esto significa que cuando creas una instancia de un `struct`, estás almacenando los datos directamente en la memoria en lugar de una referencia. Los `structs` son más adecuados para estructuras de datos pequeñas y simples, como los puntos en un espacio tridimensional.
2. **Propiedades y Campos**:
    
    - **Clases**: Las clases pueden tener campos (variables) y propiedades (variables con métodos asociados). Las propiedades son útiles para controlar el acceso y la modificación de los datos almacenados en los campos, permitiendo una encapsulación más sólida y facilitando la validación y la lógica adicional si es necesario.
    - **Structs**: Los `structs` también pueden tener campos, pero no pueden tener propiedades auto-implementadas. Esto significa que no puedes definir métodos asociados directamente con los campos dentro de un `struct`, aunque puedes crear métodos de instancia que operen en los campos.
3. **Constructores**:
    
    - **Clases**: Puedes definir constructores en las clases para inicializar los objetos cuando se crean instancias de ellas. Los constructores pueden tener parámetros para aceptar valores iniciales y pueden realizar operaciones de inicialización adicionales si es necesario.
    - **Structs**: Los `structs` pueden tener constructores también, pero no pueden tener constructores sin parámetros. Esto se debe a que los `structs` deben inicializarse completamente cuando se crean, ya que son tipos de valor y no admiten valores nulos.
4. **Métodos**:
    
    - **Clases**: Puedes definir métodos en las clases para realizar diversas operaciones en los datos almacenados en ellas. Los métodos pueden ser públicos, privados o protegidos, y pueden acceder y modificar los datos de la clase según sea necesario.
    - **Structs**: Los `structs` también pueden tener métodos, pero hay algunas limitaciones. Por ejemplo, no puedes definir métodos que modifiquen directamente los campos de un `struct` dentro del método, a menos que el `struct` sea explícitamente marcado como `mutable`. Esto se debe a que los `structs` son tipos de valor y la modificación de campos dentro de métodos implicaría copiar el `struct` en lugar de modificar el original.

Ejemplo sintaxis basica:
```cs
// Definición de la estructura
struct NombreDeLaEstructura
{
    // Declaración de campos (variables) dentro de la estructura
    tipoDeDato nombreDelCampo1;
    tipoDeDato nombreDelCampo2;
    // ... más campos si es necesario
}

// Ejemplo de uso
class Program
{
    static void Main(string[] args)
    {
        // Crear una instancia de la estructura
        NombreDeLaEstructura instancia;

        // Acceder y asignar valores a los campos de la estructura
        instancia.nombreDelCampo1 = valor1;
        instancia.nombreDelCampo2 = valor2;

        // Acceder a los campos de la estructura
        tipoDeDato valorCampo1 = instancia.nombreDelCampo1;
        tipoDeDato valorCampo2 = instancia.nombreDelCampo2;

        // Usar la instancia de la estructura como sea necesario
    }
}

```