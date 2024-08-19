En C#, los `setters` y `getters` son métodos especiales que se utilizan para establecer (`set`) y obtener (`get`) los valores de los campos (`fields`) de una clase de manera controlada.


# `Set` & `Get`
Estos métodos permiten encapsular el acceso a los campos, lo que significa que puedes controlar cómo se accede y modifica la información almacenada en ellos.

```cs
public class Persona
{
    private int _edad; // Campo privado

    // Setter para establecer el valor del campo '_edad'
    public void SetEdad(int nuevaEdad)
    {
        _edad = nuevaEdad;
    }

    // Getter para obtener el valor del campo '_edad'
    public int GetEdad()
    {
        return _edad;
    }
}
```

# `get` y `set` En propiedades

En C#, las propiedades son una forma más elegante y conveniente de implementar `getters` y `setters`. Las propiedades permiten definir un comportamiento personalizado para obtener y establecer los valores de un campo, todo ello con una sintaxis más compacta y fácil de leer.

```cs
public class Persona
{
    private int _edad; // Campo privado
    
    // Propiedad para el campo '_edad'
    public int Edad
    {
        get
        {
            return _edad; // Retorna el valor del campo '_edad'
        }
        set
        {
            if (value >= 0) // Validación: asegura que la edad no sea negativa
            {
                _edad = value; // Establece el valor del campo '_edad'
            }
            else
            {
                Console.WriteLine("La edad no puede ser negativa");
            }
        }
    }
}

```