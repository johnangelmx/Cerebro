Los metodos son funciones que van a ir con el objeto instancia do, esto nos permite mejor manipulación de datos en nuestros datos.

Unos de los ejemplos más simples son hacer operaciones aritméticas, las cuales nos permiten, pero para agregar un grado de dificultad hagamos la suma de listas dentro de C-Sharp.

El main:
```cs
 static void Main(string[] args)
 {
     var v1 = new Vector(new List<int> { 3, 4 });
     var v2 = new Vector(new List<int> { 1, 2 });
     Vector vectorSuma = v1.Suma(v2);
     vectorSuma.Impresion();
     Console.Read();
}
```
La clase que estamos trabajando:
```cs
class Vector
{
    // Campo 
    private List<int> _componentes;
    // Propiedades
    public List<int> Valores { get; set; }

    public List<int> Componentes
    {
        get
        {
            return _componentes;
        }
    }

    public int Dimension { get { return _componentes.Count; } }

    public string Nombre { get; set; }

    // Indexador
    public int this[int i]
    {
        get { return _componentes[i]; }
        set { _componentes[i] = value; }
    }
    // Constructores
    public Vector()
    {

    }

    public Vector(List<int> valores)
    {
        this._componentes = valores;
    }
}
```


Los metodos a trabajar, la primera problemática es que tendremos que sumar 2 vectores, ambos tienen que tener una dimensión o `lenght` igual y cada uno tiene que sumarse:

```cs
      // Metodos
      public Vector Suma(Vector v2)
      {
          if (Dimension != v2.Dimension)
          {
              throw new ApplicationException("Las dimensiones son diferentes");
          }
          List<int> resultado = new List<int>();

          for (int i = 0; i < Dimension; i++)
          {
              resultado.Add(this[i] + v2[i]);
          }

          return new Vector(resultado);
      }
```

Como resultado:

![[Pasted image 20240529103509.png]]
Pero para tener una impresión en consola tuvimos que tener otro método que nos ayudara con eso:
```cs
public void Impresion()
{
    this.Componentes.ForEach(i =>
    {
        Console.WriteLine(i);
    });
}
```
## Métodos complementándose

Cuando hacemos la suma de 2 vectores en nuestro main tenemos la siguiente sintaxis , la cual no es la mas normal , o la mas ideona al momento de plasmar de manera natural una suma:

```cs
Vector vectorSuman = v1.Suma(v2)
```

Por lo general querriamos ver algo asi:

El main:
```cs
 static void Main(string[] args)
 {
     var v1 = new Vector(new List<int> { 3, 4 });
     var v2 = new Vector(new List<int> { 1, 2 });
     Vector vectorSuman = v1.Suma(v2);
     Vector vectorSuma2 = v1 + v2;
     Console.Read();
}
```

Para ello el método a implementar en la clase `Vector` sería:
```cs
     public static Vector operator +(Vector v1, Vector v2)
     {

         return v1.Suma(v2);
     }
```

Al hacer lo anterior nos permite reutilizar un método que ya teníamos en nuestra clase, esto al final nos permite reutilizar código de manera idónea y como tal podremos tener un código más limpio, esto son muy buenas prácticas, al final la sintaxis esperada es válida:

```cs
Vector vectorSuma2 = v1 + v2;
```
Como resultado al implementar la impresión sería: 
![[Pasted image 20240529104056.png]]