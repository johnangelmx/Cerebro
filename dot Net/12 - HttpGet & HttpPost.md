En ASP.NET MVC, los atributos `HttpGet` y `HttpPost` son decoradores (atributos) que se utilizan para definir el tipo de solicitud HTTP que una acción de controlador puede manejar.

**HttpGet**:
- El atributo `HttpGet` se aplica a las acciones de controlador que deben responder a solicitudes HTTP GET.
- Las solicitudes GET se utilizan generalmente para recuperar datos del servidor, como cargar una página web o mostrar detalles de un recurso.
- Las acciones marcadas con `HttpGet` no deben realizar cambios en el estado de la aplicación ni en la base de datos.
- Ejemplo:

```csharp
public class ProductsController : Controller
{
    [HttpGet]
    public ActionResult Details(int id)
    {
        // Lógica para obtener los detalles del producto
        var product = GetProductById(id);
        return View(product);
    }
}
```

**HttpPost**:
- El atributo `HttpPost` se aplica a las acciones de controlador que deben responder a solicitudes HTTP POST.
- Las solicitudes POST se utilizan generalmente para enviar datos al servidor, como formularios web, actualizaciones de datos o creación de nuevos recursos.
- Las acciones marcadas con `HttpPost` pueden realizar cambios en el estado de la aplicación o en la base de datos.
- Ejemplo:

```csharp
public class ProductsController : Controller
{
    [HttpPost]
    [ValidateAntiForgeryToken]
    public ActionResult Create(ProductViewModel model)
    {
        if (ModelState.IsValid)
        {
            // Lógica para crear un nuevo producto
            CreateProduct(model);
            return RedirectToAction("Index");
        }

        // Si hay errores de validación, volver a mostrar la vista
        return View(model);
    }
}
```

Estos atributos permiten separar claramente las acciones de controlador que manejan solicitudes GET de las que manejan solicitudes POST, lo que facilita el seguimiento de los flujos de solicitud y respuesta en la aplicación.

Además, es una buena práctica utilizar el atributo `ValidateAntiForgeryToken` junto con `HttpPost` para proteger la aplicación contra ataques CSRF (Cross-Site Request Forgery).

Si no se especifica ningún atributo `HttpGet` o `HttpPost`, ASP.NET MVC asumirá que la acción puede manejar cualquier tipo de solicitud HTTP. Sin embargo, se recomienda usar estos atributos para aumentar la claridad y la seguridad de la aplicación.

---

Un ejemplo mas claro del POST:

```cs
   [HttpPost]
   public ActionResult Contact(int edad)
   {
       ViewBag.Message = "Your contact page." + edad;
       return View();

   }
```
Podremos enviar un json:
![[Pasted image 20240607154201.png]]

O un `key:value` de forma normal

![[Pasted image 20240607154236.png]]