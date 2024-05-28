En **C#** tenemos 4 tipos:

1. Los procedimientos que ejecutan un código a petición sin devolver ningún resultado.
2. Las funciones que ejecutan un código y devuelven el resultado al código que las llamó.
3. Los procedimientos de propiedades que permiten manejar las propiedades de los objetos creados.
4. Los procedimientos de operador utilizados para modificar el funcionamiento de un operador cuando se aplica a una clase o una estructura.

# **Procedimiento**
La visibilidad de un procedimiento viene determinada por la declaración `_**private`**_, _**`public`**_ o _**`internal`**_. Por defecto, si no se indica nada se entiende que es `public`.
```cs
void VerResultado(){
Console.WriteLine("Ganador");
}
```

# **Función**
La función devuelve un resultado al código invocante. La ejecución de `return` provoca la salida de la función
```cs
int calculo () {
  ...
  instrucciones
  ...
  return resultado;
}
```

# **Procedimiento de propiedades**

Estos procedimientos se llaman "Encapsuladores", ya que el valor de la propiedad se encapsula. Se utilizarán cuando queramos modificar y/o recuperar un valor (`Set`/`Get`).

```cs
public tipoDeLa Propiedad nombrePropiedad {
  get {
    ...
    //código que se ejecuta cuando se lee la propiedad
    ...
    return variable;
  }
  set {
    ...
    //código que se ejecuta durante la asignación de una propiedad
    //existe una variable que se declara implícitamente y que contiene
    //el valor que se debe asignar a la propiedad
    ...
    variable = value;
    ...
  }
}
```
Si una propiedad es de solo lectura o solo escritura, se eliminará el bloque **`set`** y/o **`get`** correspondiente. También podemos implementar automáticamente la encapsulación cuando no haya tratamiento alguno de la siguiente manera.
```cs
public int tasa {get; set;}
```

# **Procedimiento de operador**
Permite la redefinición de un operador estándar del lenguaje para utilizarlo en tipo personalizados (clase o estructura).
```cs
struct Cliente {
public int codigo;
public string apellido;
public string nombre;
}
```

```cs
  Cliente c1, c2, c3;
  c1.codigo = 200;
  c1.nombre = "Juanjo";
  c1.apellido = "Pedraza";

  c2.codigo = 125;
  c2.nombre = "Perico";
  c2.apellido = "Palotes";

  c3 = c1 + c2;
  //Aquí el compilador daría error porque no se pueden aplicar el operando al tipo.
}
```

Para que el código anterior funcione se podría hacer esto:
```cs
struct Cliente {
  public int codigo;
  public string apellido;
  public string nombre;
  public static Cliente operator + (Cliente cl1, Cliente cl2) {
    Cliente c;
    c.codigo = cl1.codigo + cl2.codigo;
    c.apellido = cl1.apellido + cl2.apellido;
    c.nombre = cl1.nombre + cla2.nombre;
    return c;
  }
}
```
Esto lo que hace es la creación de un constructor extra.

>En C#, es posible definir varios constructores para una clase, cada uno con diferentes parámetros. Los constructores pueden tener parámetros opcionales y predeterminados, lo que permite que la creación de objetos de la clase sea más flexible y adaptada a las necesidades específicas del programa

# **Argumentos de los procedimientos y funciones**
### Por valor
```cs
public static double CalculoNETO (double Pbruto, double Tasa) { 
  return Pbruto * (1+(Tasa/100));
}
...
double PrecioBruto = 100;
double PrecioNeto;
PrecioNeto = TestEstructura.CalculoNETO(PrecioBruto, 5.5);
Console.WriteLine(PrecioNeto);
```

En este caso `PrecioBruto` se está pasando por valor, ya que de forma predeterminada los valores enteros, números flotantes, decimales, booleanos y estructuras definidas por el usuario se pasan por valor. Los demás tipos siempre se pasan por referencia, es decir, se le pasa la dirección de memoria a la que apunta la variable, de forma que el procedimiento o función pueden manipular directamente el valor de esa variable.

### Por referencia
Podemos forzar el paso por referencia de una variable que por defecto se pasa como valor. para ello utilizaremos la palabra reservada “**`ref`**” o “**`out`**“, la etiqueta “`**ref**`” se debe utilizar tanto en la lista de parámetros de la función o procedimiento, como en la propia llamada a la función o procedimiento y además debe ser inicializada, por el contrario, la etiqueta “**`out`**” funciona de igual manera pero sin la exigencia de inicializar la variable.

```cs
public static double CalculoNETO (double Pbruto, double Tasa, ref double iva) {
  iva = Pbruto * (Tasa/100);
  return Pbruto+iva; }

...
double PrecioBruto = 100;
double PrecioNeto;
double importeIva=0;
PrecioNeto = TestEstructura.CalculoNETO(PrecioBruto, 5.5, ref importeIVA);
Console.WriteLine("Precio neto: {0}", PrecioNeto);
Console.WriteLine("Importe iva: {0}", importeIva);
```

Ejemplo de procedimiento con número de parámetros indeterminado.
```cs
public staic double media(params double[] notas) {
  double suma=0;
  foreach (double nota in notas) {
    suma = suma + nota;
  }
  return suma /notas.Length;
}
```
Y alguna de las llamadas a esta función "media" serían.
```cs
Resultado = media(1,4,67,233);
Resultado = media(23,33);
```

# **Parámetros opcionales**
Se puede indicar que un parámetro es opcional asignándole un valor, pero con la precaución de asignar también a todos los parámetros restantes un valor que al declarar un parámetro como opcional, el resto de parámetros también deberían serlo.

```cs
double calculoNeto(double Pbruto, double Tasa = 21);
```

La siguiente declaración estaría mal, ya que el último parámetro no sería opcional:
```cs
double calculoNeto(double Pbruto, double Tasa = 21; String divisa);
```

Lo correcto seria:
```cs
double calculoNeto(double Pbruto, double Tasa = 21; String divisa="€");
```

Por otro lado, en la llamada a la función si se específica un parámetro opcional, todos los anteriores también se deberían definir:
```cs
calculoNeto(10);
```
```cs
calculoNeto(10,5.5);
```
```cs
calculoNeto(10,5.5,"$");
```
En cambio, este daría error:
```cs
calculoNeto(10, ,"$");
```

# **Parámetros nominados:**
Podemos hacer la llamada a la función sin tener en cuenta el orden siempre que nominemos los parámetros. Por ejemplo:
```cs
calculoNeto(divisa:"$",Pbruto:250);
```

Incluso podemos combinar los parámetros de posición y por nominación.
```cs
calculoNeto(10, divisa: "$");
```

Pero hay que seguir la regla de que un parámetro nominado solo puede ser utilizado después delos parámetros por posición, el siguiente ejemplo fallaría.
```cs
//daría error
calculoNeto(10,Tasa: 5.5 ,"$");
```