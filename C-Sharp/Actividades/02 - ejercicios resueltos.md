1) Permitir al usuario escribir dos números y mostrar en pantalla cuál de los dos es el más grande. Si son iguales, mostrar cualquiera.
```cs
  int num0;
  int num1;
  Console.WriteLine("Por favor ingrese un numero");
  num0 = int.Parse(Console.ReadLine());
  Console.WriteLine("Por favor ingrese un numero");
  num1 = int.Parse(Console.ReadLine());
  Console.WriteLine("--------------------------------");
  if (num0 > num1)
  {
      Console.WriteLine($"{num0} es mayor que {num1}");
  }
  else
  {
      Console.WriteLine($"{num1} es mayor que {num0}");

  }
  Console.Read();
```
2) Escribir un método que acepte un número y devuelva True si el número es par, o false si es impar.
```cs

```

3) Escribir un método que acepte dos strings y devuelva el string con más caracteres. Si ambos tienen lamisma cantidad de caracteres, devolver cualquiera de los dos.
4) Escribir un método que acepte dos catetos y devuelve la hipotenusa (usar la clase Math para calcularla raíz cuadrada)
5) Utilizando un iterador escribir en pantalla los números del 1 al 100 de dos en dos.
6) Escribir un método que acepte un double que represente un número en grados Celcius y lotransforme a grados Fahrenheit.
7) Escribir un método que acepte una lista de números y devuelva el producto de dichos números.
8) Escribir un método que acepte un int y te devuelva el factorial de dicho número.Nota: El factorial de 3 es 3*2*1, el factorial de 5 es 5*4*3*2*1, etc.
9) Escribir un método que acepte una lista de números y devuelva su promedio.

10) Escribir un método que acepte una lista de números y devuelva el número más grande.

 

 11) Escribir un método que acepte un datetime que represente la fecha de nacimiento de una persona yretornar su edad al día de hoy.Nota: DateTime.Today te da la fecha de hoy.

 12) Escribir un fizzbuzz: Iterar los números del uno al cien, y cuando llegues a un número que seamúltiplo de 3 (el 6 por ejemplo), escribir en la consola "Fizz", cuando llegues a un número que seamúltiplo de 5 (el 20 por ejemplo) escribir en la consola "Buzz", cuando llegues a un número que seamúltiplo de 3 y 5 (el 30 por ejemplo) escribir FizzBuzz en la consola.

 13) Escribir un método que acepte una lista con números y devuelva dicha lista en orden invertido.Ejemplo: Si ingresamos la lista {4,6,49}, entonces el método debe devolver la lista {49,6,4}

 14) Escribir un método que acepte una lista de números y devuelva una lista con los mismos númerosordenados de menor a mayor.Ejemplo: Si ingresamos la lista {5,2,9,4}, entonces el método debe devolver la lista {2,4,5,9}

 15) Escribir un método que acepte una lista de números y devuelva una lista con los mismos númerosordenados de mayor a menor.Ejemplo: Si ingresamos la lista {5,2,9,4}, entonces el método debe devolver la lista {9,5,4,2}

 16) Escribir un método que acepte una lista de strings y escriba en la consola el primer caracter de cadauno de los strings.

 17) Escribir un método que acepte una lista de strings y escriba en la consola el último caracter de cadauno de los strings.

 18) Escribir un método que acepte un string y devuelva true si dicho string es un palíndromo, si no lo esdevuelve false. Un palíndromo es un texto que es igual al derecho y al revés. Ejemplos: "ana" es unpalíndromo, pero "Pirata" no es palíndromo.Para iterar un string caracter por caracter, utilizamos el indexador []. Ejemplo:

string nombre ="Felipe";for (int i = 0; i < nombre.Length; i++){Console.WriteLine(nombre[i]);}