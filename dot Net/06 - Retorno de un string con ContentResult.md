
```cs
  public ActionResult Index()
  {
      return Content("<b>Angel</b>");
  }
```

Como resultado:
![[Pasted image 20240604160207.png]]

Recomendacion, el reterno de este tipo de contenido puede ser informacion corta que podria ser ingresada o incrustada en nuestro HTML

```cs
    public ActionResult Index()
    {
        return Content("<b> Angel</b>");
        
    }
```