Para entender que es nullable, hay que entender que en los tipos de datos de una variable en lenguajes de programacion de tipado debil, permite una interaccion de asignacion `null` esto quiere decir que no hay ningun valor en la variable, pero la variable si existe en la memoria.

Una vez entendido esto , la asignacion nullable en c-sharp , permite que un dato sea nulo, esto puede servir en muchos ambitos, pero asiganarlo tiene 2 metodos:

Estructuralmente en el codigo diciendole que es nulo:
```cs
 Nullable<int> numero = 45;
 numero = null;
```

Con signo `?` al crear la variable:
```cs
 DateTime? FechaDeNacimiento = null;
 FechaDeNacimiento = new DateTime(2015, 1, 1);
```

---
En otros lenguajes de programación tenemos algunas sentencias para verificar si es nulo el dato, por ello en c-sharp no tenemos alguna sentencia directa de `isNull` para ello tenemos la sentencia:
```cs
.HasValue
```
![[Pasted image 20240527124837.png]]

`HasValue` Permite ver si un dato no es nulo, retornará  la `false` si el tipo de dato es `null`, y `true` si el tipo de dato no es un `null`.

Ejemplo:
```cs
Nullable<int> numero = 45;
numero = null;
 
DateTime? FechaDeNacimiento = null;
FechaDeNacimiento = new DateTime(2015, 1, 1);
// HasValue tiene valor que permite reconocer si un valor no es nulo
if (numero.HasValue)
{
    Console.WriteLine("Numero Tiene valor");
}

if (FechaDeNacimiento.HasValue)
{
    Console.WriteLine("La fecha tiene valor");
}
```

Al ejecutar:
![[Pasted image 20240527125940.png]]

---

Si queremos seguir utilizando un tipo de dato `null` en alguna función,  o interactuando información entre ellos, tendremos que usar su valor, es decir, no tenemos que pasar por referencia el valor, sino con valor.

Tenemos que usar directamente el valor de `null`

```cs
    if (FechaDeNacimiento.HasValue)
    {

        Console.WriteLine(CalcularEdad(FechaDeNacimiento.Value));
        Console.WriteLine("La fecha tiene valor");

    }
public static int CalcularEdad(DateTime fechaNacimiento)
{
    return -1;
}
```



