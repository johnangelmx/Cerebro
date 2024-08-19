```cs
static void Main(string[] args)
{
    var e1 = new Empresa();
    e1._NombreLegal = "Primera Empresa";
    e1._Direccion = "Primera Direccion";

    var e2 = new Empresa();
    e2._NombreLegal = "Segunda Empresa";
    e2._Direccion = "Segunda Direccion";

    e1.metodo1(e2);
    e2.metodo1(e1);
    e1.metodo1(e1);

    Console.Read();

}

class Empresa
{
    public string _NombreLegal;
    public string _Direccion;

    public void metodo1(Empresa empresa2)
    {
        var this_nombreLegal = this._NombreLegal;
        var this_direccion = this._Direccion;
        var miDireccion = _Direccion;
        var miNombreLegal = _NombreLegal;
        var empresa2_nombreLegal = empresa2._NombreLegal;
        var empresa2_direccion = empresa2._Direccion;

    }
}
```