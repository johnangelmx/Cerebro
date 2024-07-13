# `If`
```cs
if (condición) { ... }
if (condicion) { ... } else { ... }
```
# `Switch`
```cs
switch (variable) {
    case valor1:  ... 
                  break;
    case valor2:  ... 
                  break;
    ...
    deafault:     ...
                  break;
}
```
# `While`
```cs
while (condición) {
   ...
}
```

# `Do ... Hhile`
```cs
do { 
... 
} while (condición);
```

# `for`
```cs
for (inicialización del contador; condición; instrucción de iteración) { ... }

//Ejemplo
int k1;
for (k1=1; k1 < 10; k1++) {
  for (int k2=1; k2 < 10; k2++) {
    Console.Write(k1 * k2 + "\t"); }
  Console.WriteLine();
}
```

# `foreach`
```cs
foreach (elemento en matriz) { ... }

//Comparamos for con foreach
string[] matriz={"rojo","verde","azul","blanco"};
int contador;
for (contador=0; contador < matriz.Length; contador++) {
  Console.WriteLine(matriz[contador]);
}

foreach (string s in matriz) {
  Console.WriteLine(s);
}
```

# `using`
Está destinada a simplificar el desarrollo. Permite que en un bloque de código podamos utilizar un recurso externo, en el ejemplo, estamos utilizando los recursos que se encuentran en `System.IO.StreamReader`.

```cs
using (System.IO.StreamReader sr = new System.IO.StreamReader(@"C:\Users\Public\Documents\test.txt"))
{
    string s = null;
    while((s = sr.ReadLine()) != null)
    {
        Console.WriteLine(s);
    }
}
```