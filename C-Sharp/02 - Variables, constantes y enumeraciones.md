# Variables

### **El nombre de las variables:**
- Empiezan por una letra.
- Pueden estar compuestas por caracteres alfanuméricos o el carácter subrayado “_”.
- Se distinguen mayúsculas de minúsculas
- No se pueden usar las palabras reservadas del lenguaje (`if`,`switch`, `void`, …) a no sé qué se utilice el carácter arroba “**@**” precediendo al la variable. Por ejemplo.: **@if** sí podría ser una variable.

### **Tipos numéricos enteros:**

- Con signo
    - **`sbyte`** (8 bits)
    - **`short`** (16 bits)
    - **`int`** (32 bits)
    - **`long`** (64 bits)
- Sin signo
    - **`byte`** (8 bits)
    - **`ushort`** (16 bits)
    - **`uint`** (32 bits)
    - **`ulong`** (64 bits)

### **Tipos numéricos decimales** (todos son con signo).

- **`float`** (4 bytes = 32 bits)
- **`double`** (8 bytes = 64 bits)
- **`decimal`** (16 bytes = 128 bits)

### **Tipos de carácter**:

- **`char`** (2 bytes = 16 bits): código Unicode donde se pueden representar hasta 256 caracteres, de los cuales los primeros 128 son los mismos que el juego de caracteres ASCII.
- **`String`**: es el objeto que utilizamos para representar cadenas.

```cs
Char Car1 = "A";
String Cad1 = "Esto esa una cadena de caracteres";
```

### **Secuencias de escape:**

| \’ = comillas simples | \a = alerta          | \r = retorno de carro      |
| --------------------- | -------------------- | -------------------------- |
| \” = comillas dobles  | \b = backspace       | \t = tabulación horizontal |
| \\ = barra invertida  | \f = salto de página | \v = tabulación vertical   |
| \0 = carácter nulo    | \n= salto de línea   |                            |
Otra alternativa a la utilización de algunas secuencias de escape la encontramos en el operador “**@**“, que vendría a ser algo parecido a instrucción `<pre>` de HTML.

```cs
cadena = "¿Qué es lo que dice?\rÉl dice \"hola\"";
cadena = @"¿Qué es lo que dice?
Él dice ""hola""";
```

### **Tipo Boolean**
- true
- false

```cs
Boolean EsCierto = true;
Boolean Esfalso = false;
```

### **Tipo `Objetc`**
Es un variable tipo `Object` podemos almacenar cualquier cosa, en realidad la variable almacena la dirección de memoria donde se encuentra el valor de la variable.

### **Tipo `dymanic`:**
A veces puede ocurrir que solo podemos conocer el tipo de una variable en tiempo de ejecución y no cuando estamos programando o diseñando la aplicación, para este tipo de casos tenemos la palabra reservada **`dynamic`** para utilizar junto con la variable afectada y la cual no sabemos de qué tipo va a ser.

```cs
public static dynamic operacion (dynamic op1, dynamic op2) {
    return op1 + op2;
}
```

A esta función "operación" la podríamos invocar por ejemplo:
```cs
int i1;
int i2;
i1 = 2;
i2 = 3;
Console.WriteLine(operacion(i1,i2));
String s1;
String s2;
s1 = "2";
s2 = "3";
Console.WriteLine(operacion(s1,s2));
Cliente c1;
c1 = new Cliente();
Cliente c2;
c2 = new Cliente();
Console.WriteLine(operación(c1,c2));
```

Las dos primeras llamadas se ejecutarían sin problemas, la primera, sumando y la segunda concatenando, la tercera saltaría una excepción, ya que la operación “+” no es aplicable al tipo de dato Objeto directamente.

### Los tipos `Nullables`

Para asignar a una variable el valor **Null** (nulo) solo tenemos que utilizar el carácter “**`?`**”, después del tipo de variable. 

Por ejemplo podemos hacer la recuperación de ciertos datos de una base de datos y cuando recuperamos esos datos nos damos cuenta de que no tienen ningún valor, por ejemplo campos booleanos, enteros. Para estos casos puede ser interesante no asignar ningún valor a la variable, o mejor dicho asignar el valor **Null** a dicha variable. Luego para saber si una variable tiene valor podemos utilizar la función **`Hasvalue`**. 

Si intentáramos utilizar el valor de una variable que no tiene valor (null) nos saltaría una excepción, por lo que a las variables que permitimos tener valor nulo siempre debemos tener la precaución de comprobar antes si tienen algún valor asignado.

```cs
int? CodigoPostal;
float? SueldoBase;
...
CodigoPostal = 46022;
if (CodigoPostal.HasValue) {
    Console.writeLine(CodigoPostal.Value); }
else {
    Console.WriteLine("Código Postal vacío"); }
...
//podemos volver a asignar el valor nulo
CodigoPostal = null;
```

# Declaración de Variable
Sintaxis general de declaración de una variable(los parámetros entre corchetes son opcionales.)
```cs
Tipo nombreVariable = valor iniical, nombrevariable2
```
En caso de que se omita el valor inicial, la variable será inicializada a **cero** si corresponde a un tipo **numérico**; a una cadena de **carácter vacío** si es del tipo **String**; al valor **null** si es del tipo **Object**, y a **false** si es del tipo **bool**.

### **Inferencia de tipo**

El compilador puede determinar el tipo que se ha de utilizar para una variable local. La inferencia sólo sirve para variables declaradas en una función (variables locales).

```cs
var apellido= "Pedraza";
```
Ejemplo con clases:
```cs
    class Program
    {

        static void Main(string[] args)
        {
            var Nombre = "Felipe";
            var mes = 5;
            var procesoTerminado = false;

            string direccion;
            var p = new Persona();
            p.Nombre = "Felipe";

            Console.Read();
        }

        class Persona
        {
            public string Nombre;
            public int Edad;
            public string Direccion;

            public void MostrarDatosEnConsola()
            {
                Console.WriteLine($"El nombre es {this.Nombre} la edad es de {this.Edad} y mi direccion es {this.Direccion} ");


            }

        }
    }
```

### **Las constantes**
Valores numéricos o cadenas que no serán modificados durante el funcionamiento de la aplicación.

```cs
const int ValorMax = 100;
const string Mensaje = "Muy grande";
...
If (resultado>Valormax) 
  Console.writeLine(Mensaje);
...
```
Podemos también calcular el valor de una constante a partir de otra constante.
```cs
public const int Total = 100;
public const int Semi = Total / 2;
```

# Enumeraciones
```cs
enum DiasSemana {Lunes, Martes, Miércoles, Jueves, Viernes, Sábado, Domingo};
// Que sería equivalente a ....
const int Lunes=0;
const int Martes=1;
const int Miércoles=2;
const int Jueves=3;
const int Viernes=4;
const int Sábado=5;
const int Domingo=6;
// Si queremos interrumpir la secuencia de incremento automático
enum DiasSemana2 {Lunes=10, Martes=20, Miércoles=30, Jueves=40, Viernes=50, Sábado=60, Domingo=70};
// Los valores de las enumeraciones siempre son números enteros.
//Podemos utilizar la enumeración como un tipo de variable
DiasSemana2 VarDia;
VarDia = DiasSemana.Lunes;
Console.WriteLine(VarDia);
```

