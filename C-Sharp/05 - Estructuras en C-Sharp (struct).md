# Las estructuras
Posibilidad de crear un nuevo tipo a partir de la combinación de diferentes tipos.

### Declaración
```cs
struct Direccion {
    public int codPostal;
    public string calle;
    public string ciudad; 
    public string getDireccion(){
        return calle + "\r\n " + codigoPostal + "\t"+ ciudad.ToUpper(); 
    }
}

// fijarse en el tipo de dato del campo correoPostal
struct Cliente {
    public int codigo;
    public string apellido;
    public string nombre;
    public string email; 
    public Direccion correoPostal}
```

### Utilización
```cs
Cliente UnCliente;
UnCliente.codigo = 9999;
UnCliente.apellido = "Pedraza";
UnCliente.nombre = "Juanjo";
UnCliente.correoPostal.codPostal=3740;
UnCliente.correoPostal.calle="C/ Perico Palotes, 33";
UnCliente.correoPostal.ciudad="Gata de Gorgos City";

Console.WriteLine(UnCliente.correoPostal.getDireccion());
```