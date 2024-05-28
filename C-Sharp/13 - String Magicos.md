Igual que los números mágicos, los string mágicos son string que no tiene un contexto, que son "**Hard-Codeado**" en nuestro código.
```cs
string estatusOperacion = "K15";
if (estatusOperacion == "k120"){
// ....
}
else if (estatusOperacion == "P4"){
// ....
}
else if (estatusOperacion == "K15"){
// ....
}
Console.Read();
```
Estamos tratando de hacer una determinada acción, según el estatus de la operación, pero el contexto de cada uno de ellos solo lo conoce el programador.

Formas de arreglarlo
```cs
private const string _exitoso = "K120"
private const string _clienteNoEncontrado = "P4"
private const string _errorDelSistema = "K15"
```
El integrar variable global, o la creación de variables, permite de mejor manera tener un contexto del `string`.

En el código sería más legible:
```cs
string estatusOperacion = "K15";
if (estatusOperacion == _exitoso_){
// ....
}
else if (estatusOperacion == _clienteNoEncontrado){
// ....
}
else if (estatusOperacion == _errorDelSistema){
// ....
}
Console.Read();
```

Si deseas utilizar de muchos puntos dichas variables tendrías que: 

```cs
public static class EstatusOperaciones {
public const string _exitoso = "K120"
public const string _clienteNoEncontrado = "P4"
public const string _errorDelSistema = "K15"
}
```

Y al utilizarlo tendríamos que: 
```cs
if (estatusOperacion == EstatusOperaciones._exitoso_){
// ....
}
else if (estatusOperacion == EstatusOperaciones._clienteNoEncontrado){
// ....
}
else if (estatusOperacion == EstatusOperaciones._errorDelSistema){
// ....
}
Console.Read();
```

Al final la recomendación no utilizar `string's` o números mágicos

---
