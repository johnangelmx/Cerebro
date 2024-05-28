Las enumeraciones nos permiten conocer un conjunto de valores que permiten tener un conjunto de valores acumulados.

Es decir, a una problemática como la siguiente:
```cs
static void Main(string[] args)
        {
            int estatusOperacion = 5;

            if (estatusOperacion == 1) {
                // ... 
            }
            else if (estatusOperacion == 2)
            {
                // ... 
            }
            else if (estatusOperacion == 5)
            {
                // ...
            }
            Console.Read();
        }
```

La problemática es que si, por algún motivo, la asignación de estatus de operación solo se acuerde para qué funciona cada uno de ellos un único programador, entonces la información se pierde. Es decir:
- El número 1 significa **Exitoso**
- El número 2 significa **Cliente No Encontrado**
- El número 5 significa **Error De Sistema**

Para ello existen los `enums`
```cs
  enum EstatusOperacion
        {
            Exitoso = 1, 
            ClienteNoEncontrado = 2,
            ErrorDeSistema = 5
        }
```

Esto permite la manipulación de datos de la misma forma, con números, pero con un contexto, o nombre de variable con mucha más información relacionada.
```cs
static void Main(string[] args)
        {
            int estatusOperacion = 5;

            if (estatusOperacion == (int)EstatusOperacion.Exitoso) {
                // ... 
            }
            else if (estatusOperacion == (int)EstatusOperacion.ClienteNoEncontrado)
            {
                // ... 
            }
            else if (estatusOperacion == (int)EstatusOperacion.ErrorDeSistema)
            {
                // ...
            }
            Console.Read();
        }
```

Al integrar `enums`, es como si estuviéramos trabajando con objetos literales, es decir, para acceder al valor tendríamos que acceder primero a la propiedad, esto al final permite una mejor manipulación de datos.

--- 

# Números mágicos 

Solo son números que no tienen contexto, ¿porque se le llama asi ? Porque mágicamente te lo puedes encontrar porque no tiene información de donde vienen 

```cs 
static void Main(string[] args)
        {
            int estatusOperacion = 5;

            if (estatusOperacion == 1) {
                // ... 
            }
            else if (estatusOperacion == 2)
            {
                // ... 
            }
            else if (estatusOperacion == 5)
            {
                // ...
            }
            Console.Read();
        }
```

La importancia de verificar este tipo de información, es importante en el mundo de la programación , porque esto permite que pierdas el hilo de que se está haciendo en el código, el porqué y como trabaja y como esto puede afectar el día de mañana si alguien más toca tu código.




