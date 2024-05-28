```cs
			DateTime fecha = new DateTime(2014, 10, 23);
            DateTime fechaConHora = new DateTime(2005, 4, 23, 9, 30, 45);

            Console.WriteLine(fecha.ToString());
            // Cambiar formato de fecha
            Console.WriteLine(fecha.ToString("yyyy-MM-dd"));
            Console.WriteLine(fecha.ToString("dd/MM/yyyy"));
            // Cambiar formato de fecha con hora
            Console.WriteLine(fechaConHora.ToString("dd/MM/yyyy hh:mm:ss"));

			// Agregar dias a una fecha
            Console.WriteLine(fecha.AddDays(45).ToString("yyyy-MM-dd"));
			
			// Metodos de ayuda
            Console.WriteLine(fechaConHora.DayOfWeek);
            Console.WriteLine(fechaConHora.Date);

            // Sacar cantidad de dias entre fecha y fechaConHora
            Console.WriteLine(fecha.Subtract(fechaConHora).Days);

            Console.Read();

```

