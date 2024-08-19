```cs
static void Main(string[] args)
{

    double numero1 = 5;
    double numero2 = 7;
    double numero3 = 10;
    double promedio = CalcularPromedio(numero1, numero2);
    Console.WriteLine(promedio);
    Console.Read();

}

private static double CalcularPromedio(int numero1, int numero2)
{
    return (numero1 + numero2) / 2.0;
}

private static double CalcularPromedio(double numero1, double numero2)
{
    return (numero1 + numero2) / 2.0;
}

private static double CalcularPromedio(double numero1, double numero2, double numero3)
{
    return (numero1 + numero2) / 2.0;
}
```