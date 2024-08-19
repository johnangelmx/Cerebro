En ASP.NET MVC, las vistas se crean utilizando el motor de vistas Razor, que combina código HTML y código basado en C# en un mismo archivo. Esto permite escribir lógica y generar contenido dinámico en las vistas de una manera más fluida y legible.

A continuación, te explicaré cómo escribir código en una vista Razor:

**1. Bloques de código Razor**:
Puedes incrustar código C# en tus vistas utilizando los bloques de código Razor, que comienzan con `@` y se encierran entre llaves `{ }`. Por ejemplo:

```html
@{
    // Código C#
    var mensaje = "¡Hola, mundo!";
}

<h1>@mensaje</h1>
```

**2. Expresiones Razor**:
Las expresiones Razor te permiten renderizar el resultado de una expresión de código C# directamente en la salida HTML. Se escriben con `@` seguido de la expresión. Por ejemplo:

```html
<p>La fecha actual es: @DateTime.Now.ToString("dd/MM/yyyy")</p>
```

**3. Bucles y condicionales**:
Puedes utilizar construcciones de control de flujo como bucles y condicionales en tus vistas. Por ejemplo:

```html
@if (ViewBag.MostrarMensaje)
{
    <p>Este es un mensaje importante.</p>
}
else
{
    <p>No hay mensajes.</p>
}

<ul>
    @foreach (var item in Model.ListaItems)
    {
        <li>@item.Nombre</li>
    }
</ul>
```

**4. Layouts y secciones**:
Las vistas Razor pueden aprovechar la funcionalidad de Layouts y secciones para estructurar y organizar el contenido. Por ejemplo:

```html
@{
    Layout = "~/Views/Shared/_Layout.cshtml";
}

@section Scripts {
    <script src="~/js/miScript.js"></script>
}

<h2>Contenido de la vista</h2>
```

**5. Métodos de ayuda HTML**:
ASP.NET MVC proporciona métodos de ayuda HTML que facilitan la generación de elementos HTML. Por ejemplo:

```html
@Html.TextBoxFor(m => m.Nombre)
@Html.ValidationMessageFor(m => m.Nombre)
```

**6. Vistas parciales y componentes de vista**:
Puedes incrustar vistas parciales y componentes de vista en tus vistas utilizando métodos como `Html.Partial` y `@await Component.InvokeAsync`. Esto promueve la reutilización de código y la modularidad.

Estos son solo algunos ejemplos de cómo escribir código en una vista Razor. El motor de vistas Razor ofrece muchas más características y funcionalidades para facilitar el desarrollo de vistas dinámicas y potentes en ASP.NET MVC.