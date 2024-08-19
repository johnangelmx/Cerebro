Imagina la siguiente problemática:

```cs
 static void Main(string[] args)
 {
     var v2 = new Vector(new List<int> { 1, 2, 3, 4, 5, 6 });
     Console.Read();

 }

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

Si nosotros queremos ingresar datos a de tal manera que:

```cs
	 static void Main(string[] args){
		 v2[0] = 5;
		 Console.WriteLine(v2[0]);
	 }
```

No podremos dado que en nuestra clase la propiedad
```cs
private List<int> _componentes;
```
Esta en privado, para acceder a esa propiedad tenemos: 

```cs
   public List<int> Componentes
   {
       get
       {
           return _componentes;
       }
   }
```

Pero solo de manera de lectura, y para implementar un cambio en `_componentes` tendremos que crear un indexador:

```cs
// Indexador
public int this[int i]
{
    get { return _componentes[i]; }
    set { _componentes[i] = value; }
}
```

El indexador nos permite regresar un elemento de la lista de una propiedad privada, véase como un método que permite recibir un elemento de la lista y regresar dicho elemento.

Pero el `set` que tenemos es una situación diferente, en c-sharp nos permite la facilidad que al asignar un valor nuevo al elemento dentro del arreglo,  al ingresar `value` automáticamente identifica que quieres asignar un elemento dentro de tu propiedad privada, es decir, al hacer: 

```cs
v2[0] = 5;
Console.WriteLine(v2[0]);
```
Es donde la instrucción:
```cs
set { _componentes[i] = value; }
```

Al final, como resultado del indexador tenemos:
![[Pasted image 20240529101104.png]]

