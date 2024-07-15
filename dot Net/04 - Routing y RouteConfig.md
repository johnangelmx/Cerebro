En ASP.NET MVC, el enrutamiento (routing) es el proceso de mapear las solicitudes HTTP entrantes a las acciones correspondientes en los controladores de la aplicación. El enrutamiento se configura en el archivo `RouteConfig.cs` que se encuentra dentro de la carpeta `App_Start` del proyecto.

**Routing**: El enrutamiento en ASP.NET MVC permite definir patrones de URL que se mapean a las acciones de los controladores. Esto permite crear URLs amigables y semánticas, en lugar de utilizar cadenas de consulta complejas o identificadores numéricos.

Ejemplo de una definición de ruta en `RouteConfig.cs`:
```cs
routes.MapRoute(
    name: "Default",
    url: "{controller}/{action}/{id}",
    defaults: new { controller = "Home", action = "Index", id = UrlParameter.Optional }
);
```

Esta definición de ruta establece que una URL como `/Home/Index/123` se mapeará al método `Index` del controlador `HomeController`, pasando `123` como el valor del parámetro `id`.

---

**RouteConfig**: El archivo `RouteConfig.cs` contiene la configuración de enrutamiento para la aplicación ASP.NET MVC. Aquí se definen las reglas de enrutamiento que determinan cómo se mapean las solicitudes HTTP a los controladores y acciones correspondientes.

Dentro de `RouteConfig.cs`, se encuentra el método `RegisterRoutes`, donde se configuran las rutas de la aplicación utilizando el objeto `RouteCollection`.

Ejemplo de `RegisterRoutes` en `RouteConfig.cs`:
```cs
public static void RegisterRoutes(RouteCollection routes)
{
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

    routes.MapRoute(
        name: "Default",
        url: "{controller}/{action}/{id}",
        defaults: new { controller = "Home", action = "Index", id = UrlParameter.Optional }
    );
}
```
En este ejemplo, se define una ruta predeterminada que mapea las URLs con el formato `{controller}/{action}/{id}` a los controladores y acciones correspondientes. Si no se proporciona un valor para `controller` o `action`, se utilizan los valores predeterminados `Home` y 
`Index`, respectivamente.

Ejemplo de ruta:
```cs
routes.MapRoute(
    name: "Ejemplo",
    url: "Ejemplo",
    defaults: new { 
	    controller = "Home", 
	    action = "Contact" 
	}
);
```

