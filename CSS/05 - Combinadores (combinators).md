Los combinadores nos permiten combinar múltiples selectores y crear una mayor especificidad.

> Los combinadores nos permitirán tener una especificidad más alta que nos va a ayudar tener menos id's

![[Pasted image 20231016070022.png]]

## Hermano adyacente o cercano 
Este combinador permite agregar estilos a una etiqueta que este después de otra, es decir, la etiqueta que seleccione primero tiene cerca a una etiqueta que seleccionar segundo, y a esa segunda etiqueta le pondrás estos estilos: 

Ejemplo:
```HTML
<div>

        <h2>soy un h2</h2>

        <p>Soy un p </p>

        <h2>soy un h2</h2>

        <h3>Soy un h3</h3>

        <p>Soy un p </p>

        <h2>Soy un h2</h2>

        <p>Soy un p </p>

</div>
```

Tengo el siguiente HTML

```CSS
h2+p {

    color: red;

}
```

Y el resultado es:

![[Pasted image 20231016070941.png]]

---
## Hermano General
Los combinadores de hermano general, permite la propagación del estilo solo si después de cierto selector está seleccionado, es decir, seleccionamos el primer selector que ese tiene que coincidir con el código, y después ingresamos el símbolo **`~`** y seleccionamos el selector al cual recibirá los estilos solo si el primer selector está presente en el código, se propagará los estilos.

¿En qué se diferencia a la herencia? 
Que en este caso tendría que existir el primer selector para que el segundo pueda tener estilos.

Ejemplo 
```HTML
<div>

        <h2>Soy un H2</h2>

        <p>Soy una etiqueta P</p>

        <h2>Soy un H2</h2>

        <h3>Soy un H3</h3>

        <p>Soy una etiqueta P</p>

        <p>Soy una etiqueta P</p>

    </div>
```

```CSS
h2~p {

    color: red;

}
```
Resultado:

![[Pasted image 20231016071833.png]]

---
## Hijo

Los combinadores de hijo, permiten seleccionar el elemento que este exactamente después del otro elemento seleccionado, es decir, El primer selector que ingresemos será el padre y el segundo será el hijo, estos únicamente serán válidos si están exactamente después del padre 

Ejemplo 
```HTML
<div>

        <article>

            <p>Soy un texto</p>

        </article>

        <article>

            <p>Soy un texto</p>

        </article>

        <section>

            <div>

                <p>Soy un texto</p>

            </div>

        </section>

        <p>Soy un texto</p>

    </div>
```

```CSS
div>p {

    color: red;

}
```

Como resultado: 

![[Pasted image 20231016091241.png]]


--- 
## Descendiente

El combinador descendiente es la búsqueda del elemento en un contenedor, no importa, sino está después del seleccionador, este buscará si está en el contenedor, es decir todos los descendientes que están después del contenedor seleccionado

Ejemplo 
```HTML
<div>

        <article>

            <p>Soy un texto</p>

        </article>

        <article>

            <p>Soy un texto</p>

        </article>

        <section>

            <div>

                <p>Soy un texto</p>

            </div>

        </section>

        <p>Soy un texto</p>

    </div>
```

```CSS
div p {

    color: red;

}
```

Como resultado:

![[Pasted image 20231016091645.png]]
