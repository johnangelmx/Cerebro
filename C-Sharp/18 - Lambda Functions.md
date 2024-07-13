En C#, las funciones lambda son una característica que permite crear funciones anónimas de manera concisa. Son útiles cuando necesitas pasar una pequeña funcionalidad como argumento a otro método, especialmente en situaciones donde solo se requiere una función simple y no deseas definir un método separado.

```cs
     // Definir una función lambda que suma dos números
     Func<int, int, int> suma = (a, b) => a + b;

     // Llamar a la función lambda
     int resultado = suma(3, 5);
     Console.WriteLine(resultado); // Output: 8
```

---

# A lo que se le puede llamar lambda
Tenemos la siguiente función:

```cs
List<int> numeros = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8 };
numeros = numeros.Where(x => x > 5).ToList();
```
 Uso del método `Where`: Después, utilizamos el método `Where` en nuestra lista `numeros`. Este método es parte de LINQ (Language Integrated Query), una característica de C# que permite hacer consultas sobre colecciones de datos. `Where` toma una función lambda como argumento y devuelve una nueva colección que contiene solo los elementos que cumplen con la condición especificada en la función lambda.

Función lambda: La función lambda `x => x > 5` actúa como un filtro. Toma cada elemento `x` de la lista y devuelve `true` si `x` es mayor que 5, y `false` en caso contrario.

Conversión a lista: Finalmente, llamamos al método ToList() para convertir el resultado de la operación Where de nuevo en una lista. Esto actualiza nuestra variable numeros para que ahora contenga solo los números mayores que 5.


