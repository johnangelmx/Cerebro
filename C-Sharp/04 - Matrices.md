# Matrices de una dimensión
La creación se efectúa en 2 etapas. Primero declaramos la variable tipo matriz y luego reservamos la memoria para almacenar el contenido de la matriz.

```cs
//Si queremos guardar la facturación de 12 meses en una matriz
int[] facturación;
facturación = new int[12];
facturación[0]=1500;
facturación[1]=2500;

//Matriz inicializada y donde no es necesario precisar el tamaño de la matriz
double[] tasaIva ={0,4,10,21};
```
# Matrices de varias dimensiones
La sintaxis es similar
```cs
int[,,] Cubo;
Cubo = new int[4,4,4];
Cubo[0,1,1] = 52;

//Matriz inicializada
int[,] rejilla2D = {{1,2},{3,4}};
//Obtendremos ahora el tamaño de la matriz, es decir, número de casillas
Console.WriteLine(rejilla2D.Lenght);

int[,] matriz ={{1,2},{3,4},{5,6}};
Console.WriteLine ("Tamaño de la primera dimensión {0}", matriz.GetLenght(0));
Console.WriteLine ("Tamaño de la segunda dimensión {0}", matriz.GetLenght(1));
//Dará 3 y 2 respectivamente

//Si queremos saber las dimensiones de la matriz (2 en nuestro ejemplo)
Console.WriteLine("La dimesión es: {0}", matriz.Rank);
```

# Buscar un elemento y ordenar en una matriz
```cs
string[] merienda={"pan","nocilla","mermelada","mantequilla","pate"}
//Buscando un elemento
Console.WriteLine(Array.IndexOf(merienda,"mantequilla"));

//Ordena alfabéticamente
Array.Sort(merienda);
foreach (string plato in merienda) {
    Console.WriteLine(plato); }
```