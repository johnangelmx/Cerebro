```cs
 static void Main(string[] args)
 {

     double numero1 = 5;
     double numero2 = 7;
     double numero3 = 10;
     double promedio = CalcularPromedio(4, 5, 6, 7, 3, 5, 7, 10, 100);
     Console.WriteLine(promedio);
     Console.Read();

 }
 private static double CalcularPromedio(params int[] numeros)
 {
     double suma = 0.0;

     foreach (var num in numeros)
     {
         suma += num;
     }

     return suma / numeros.Length;
 }
```