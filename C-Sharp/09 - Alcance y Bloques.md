```cs
class Program
    {

        static void Main(string[] args)
        {
            string nombre = "felipe";
            nombre = "Juan";
            edad = 45;

            var p = new Persona();
            p.PaisOrigen = "Republica dominicana";
            p.obtenerEdad();

            Console.Read();

        }
        static void Main2() {
            nombre = "pedro";
        }
        // Solo al ingresar static puede leer la variable en diferentes scoopes
        static int edad = 21;

        class Persona
        {
            public string PaisOrigen;
            private int edad2;
            public int obtenerEdad()
            {
                return edad2;
            }
        }
    }
```

Las diferentes formas de interactuar por scoop dentro de C-Sharp

La primera es que los scoop's no puede comunicarse entre sí a menos que sé un `return`
La siguiente sentencia marcaría un error
```cs
  static void Main(string[] args)
        {
            string nombre = "felipe";
            nombre = "Juan";
        }
        static void Main2() {
            nombre = "pedro";
        }
```

Por segundo, las variables externas del scoop si se pueden comunicar, pero esto solo aplica en la cuando la variable se convierte en `static`, estas pueden interactuar dentro de su mismo scoop mayor:
```cs
class Program
    {

        static void Main(string[] args)
        {
            string nombre = "felipe";
            nombre = "Juan";
            edad = 45;
            Console.Read();
        }
// Solo al ingresar static puede leer la variable en diferentes scoopes
static int edad = 21;


... }
```

Tercero, tanto como las clases y las los métodos en ello, estas también pueden llegar a tener un alcance:
```cs
class Persona
        {
            public string PaisOrigen;
            private int edad2;
            public int obtenerEdad()
            {
                return edad2;
            }
        }
```
Por ejemplo, al crear una instancia de Persona, tendremos a la vista que no podemos alcanzar la variable edad 2, porque está en privado.
```cs
    var p = new Persona();
            p.PaisOrigen = "Republica dominicana";
            p.obtenerEdad();
```
Pero un método que puede leer la edad si lo podremos invocar porque está en público:
```cs
    var p = new Persona();
            p.PaisOrigen = "Republica dominicana";
            p.obtenerEdad();
```

