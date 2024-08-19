Los constructores en c-sharp son los creadores que tendrán las bases al instanciar una clase, es decir, construirán un objeto a base de propiedades o campos que sean compatibles con él:

# Constructores

Los constructores son métodos especiales que se llaman automáticamente cuando sé instancia una clase. Tienen el mismo nombre que la clase y no tienen tipo de retorno.

### Constructor sin parámetros
```cs
public class MiClase
{
    // Constructor sin parámetros
    public MiClase()
    {
        // Código del constructor
    }
}
```

### Constructor con parametros
```cs
public class MiClase
{
    // Constructor con parámetros
    public MiClase(int parametro1, string parametro2)
    {
        // Código del constructor
    }
}

```

### Constructor con copia (ejemplo)
```cs
public class MiClase
{
    public int Propiedad { get; set; }

    // Constructor de copia
    public MiClase(MiClase otraInstancia)
    {
        Propiedad = otraInstancia.Propiedad;
    }
}
```

### Constructor por defecto y constructor personalizado
```cs
public class MiClase
{
    public int Propiedad { get; set; }

    // Constructor por defecto
    public MiClase()
    {
        Propiedad = 0;
    }

    // Constructor personalizado
    public MiClase(int valorInicial)
    {
        Propiedad = valorInicial;
    }
}
```

### Uso de constructores
```cs
// Creación de instancia utilizando el constructor sin parámetros
MiClase objeto1 = new MiClase();

// Creación de instancia utilizando el constructor con parámetros
MiClase objeto2 = new MiClase(10, "ejemplo");

// Uso de constructor de copia
MiClase objeto3 = new MiClase(objeto2);

// Uso de constructor personalizado
MiClase objeto4 = new MiClase(5);

```

