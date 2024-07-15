```cs
 static void Main(string[] args)
 {

     Console.WriteLine( 5.ElevadoALa(3) );
 }
 public static class IntegerExtensionMethods
 {
     public static double ElevadoALa(this int valor, int exponente) => Math.Pow(valor, exponente);
 }
```