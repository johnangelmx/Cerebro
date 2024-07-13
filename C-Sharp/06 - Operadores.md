# Operadores en **C#**
- De asignación. =
- Aritméticos. + – * / % (resto de la división entera)
- Binarios: & (Y binario) | (O binario) ^ (O exclusivo) ˜ (negación)
- Comparación: == (igual) != (distinto) < (menor) > (mayor) <= (menor o igual) >= (mayor o igual) `is` (compara el tipo de variable con el tipo dado

```cs
if ( edad is int) { ... }
```
Concatenación. Podemos concatenar con el símbolo +, o mejor con `StringBuilder` que realiza la operación más rápida
```cs
string cadena = "123";
Console.writeLine (cadena + 456);
// Visualizará 123456
```

```cs
long duracion
string liebre;
string tortuga="";
dateTime principio, fin;

principio = DateTime.Now;
for (int i = 0; i <= 100000; i++) {
    tortuga = tortuga + " " + i; }
fin = DateTime.Now;
duracion = new TimeSpan(fin.Ticks - principio.Ticks).Seconds;
Console.WriteLine("duración para la tortuga: " + duracion +"s");

principio = DateTime.Now;
StringBuilder sb = new StringBuilder();
for (int i = 0; i <= 100000; i++) {
    sb.Append(" ");
    sb.Append(i);}
liebre = sb.ToString();
fin = DateTime.Now;
duracion = new TimeSpan(fin.Ticks - principio.Ticks).Seconds;
Console.WriteLine("duración para la liebre: " + duracion +"s");
if (liebre.Equals(tortuga)) {
    Console.WriteLine("las dos cadenas son idénticas");
```

# Lógicos

|          |             |                       |                                                        |
| -------- | ----------- | --------------------- | ------------------------------------------------------ |
| Operador | Operación   | Ejemplo               | Resultado                                              |
| &        | Y lógico    | If (test1)&(test2)    | Cierto si ambos son ciertos                            |
| \|       | O lógico    | If (test1) \| (test2) | Cierto si alguno de los dos es cierto                  |
| ^        | O exclusivo | If (test1)^(test2)    | Cierto si alguno es cierto y el otro NO lo es          |
| !        | Negación    | If ! test             | Invierte el resultado de test                          |
| &&       | Y lógico    | If (test1)&&(test2)   | Igual que &, pero solo evalua test2 si test1 es cierto |
| \|       | O lógico    | If (test1)\|(test2)   | Igual que \|, pero solo evalua test2 si test1 es falso |

# Orden de evaluación 

1. Operaciones aritméticas
    1. Negación
    2. Multiplicación y división
    3. Módulo
    4. Suma y resta, o concatenación de cadenas
2. Operaciones de comparación
3. Operadores lógicos