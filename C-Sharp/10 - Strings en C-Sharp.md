```cs
    string nombre = "Felipe";
            string frase = "juan Y Jose son amigos";
            // Length

            Console.WriteLine(nombre.Length);
            Console.WriteLine(frase.Length);

            // substring 
            //elimina el numero de caracteres de izquierda a derecha
            Console.WriteLine(nombre.Substring(3));
            
            // subtrae el numero de caracteres entre 2 y 7
            Console.WriteLine(frase.Substring(2,7));

            // startswith - Verifica que si la cadena de caracteres inicia con un valor a pasar, es case sensitive
            Console.WriteLine(frase.StartsWith("juan"));
            Console.WriteLine(frase.StartsWith("Jose"));

            // endswith - Verifica que si la cadena de caracteres finaliza con un valor a pasar , es case sensitive
            Console.WriteLine(frase.EndsWith("amigos"));
            Console.WriteLine(frase.EndsWith("enemigos"));

            // contains
            Console.WriteLine(frase.Contains("Jose"));
            Console.WriteLine(frase.Contains("Pedro"));

            // indexOf - regresa el indice de donde empieza la primera letra del valor que le pasemos
            var indiceDeJose = frase.IndexOf("Jose");
            var indiceDePedro = frase.IndexOf("Pedro");

            Console.WriteLine(indiceDeJose);
            Console.WriteLine(indiceDePedro);

            // operador ++
            Console.WriteLine(nombre + ", " + frase);

            // toLower
            Console.WriteLine(frase.ToLower());
            //toUpper
            Console.WriteLine(frase.ToUpper());

            // trim - permite quitar espacios al inicio o al final de los strings
            string ejemploTrim = "  Felipe  ";
            Console.WriteLine(ejemploTrim.Trim());

            // Format
            string ejemploFormat = "Felicidades {0} en tu cumpleanos numero {1}! {0}";
            var resultadoFormat = string.Format(ejemploFormat, nombre, 50 );
            Console.WriteLine(resultadoFormat);

            // replace 
            string ejemploReplace = "Felicidades @nombre en tu cumpleanos numero @edad";
            var resultadoReplace = ejemploReplace.Replace("@nombre", "pedro");
            resultadoReplace = ejemploReplace.Replace("@edad", "50");
            Console.WriteLine(resultadoReplace);

            // IsNullOrWhiteSpace
            string strinEspaciosEnBlanco = "     ";
            string stringNulo = null;
            Console.WriteLine(string.IsNullOrWhiteSpace(strinEspaciosEnBlanco));
            Console.WriteLine(string.IsNullOrWhiteSpace(stringNulo));
            Console.WriteLine(string.IsNullOrWhiteSpace(nombre));

            Console.WriteLine();

            Console.Read();
```