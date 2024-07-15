En ASP.NET MVC, las acciones de los controladores pueden recibir parámetros de dos maneras principales: a través de los parámetros de la acción y a través de la cadena de consulta (Query String).

**Parámetros de una acción**:
Los parámetros de una acción son parámetros que se definen en el método de la acción del controlador. Estos parámetros se asocian con los valores enviados en la URL o en el cuerpo de la solicitud HTTP.

Ejemplo:

```csharp
public class ProductsController : Controller
{
    public ActionResult Details(int id)
    {
        // Lógica para obtener el producto con el id especificado
        var product = GetProductById(id);
        return View(product);
    }
}
```

En este ejemplo, la acción `Details` recibe un parámetro `id` de tipo `int`. Cuando se realiza una solicitud a la ruta `/Products/Details/123`, el valor `123` se asigna automáticamente al parámetro `id` de la acción.

**Cadena de consulta (Query String)**:
La cadena de consulta es una parte de la URL que contiene pares clave-valor separados por `&`. Estos valores se pueden leer en las acciones del controlador a través de la propiedad `Request.QueryString`.

Ejemplo:

```csharp
public class ProductsController : Controller
{
    public ActionResult Search()
    {
        string name = Request.QueryString["name"];
        int? category = Request.QueryString["category"] != null
            ? int.Parse(Request.QueryString["category"])
            : (int?)null;

        // Lógica para buscar productos con los parámetros especificados
        var products = SearchProducts(name, category);
        return View(products);
    }
}
```

En este ejemplo, la acción `Search` no tiene parámetros definidos en su firma. En su lugar, lee los valores de la cadena de consulta a través de `Request.QueryString`. Por ejemplo, si se realiza una solicitud a la ruta `/Products/Search?name=laptop&category=2`, se asignarán los valores `"laptop"` a `name` y `2` a `category`.

**Diferencias y cuándo usar cada uno**:

- Los parámetros de acción son más adecuados cuando se conocen de antemano los parámetros que se necesitan y su tipo. Son más fáciles de mantener y refactorizar.
- La cadena de consulta es útil cuando se necesita pasar un número variable de parámetros o cuando los parámetros son opcionales.
- Es posible combinar ambos enfoques en una sola acción.
- Desde el punto de vista de la URL, los parámetros de acción forman parte de la propia ruta (por ejemplo, `/Products/Details/123`), mientras que la cadena de consulta aparece después del símbolo `?` (por ejemplo, `/Products/Search?name=laptop&category=2`).

En general, se recomienda utilizar los parámetros de acción siempre que sea posible, ya que son más fáciles de leer, mantener y refactorizar. Sin embargo, la cadena de consulta puede ser más adecuada en ciertos escenarios, como cuando se necesita pasar un número variable de parámetros o cuando los parámetros son opcionales.