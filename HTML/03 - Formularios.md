# Formularios

Los formularios nos permiten recolectar información del usuario hacia nuestra pagina web, esto puede ser desde tener un perfil en la pagina o simplemente mantener un contacto de correo con el usuario, en fin , los formularios son necesarios en nuestra pagina en todo momento, para ello tendremos que tener una idea clara de como se hace en HTML.

```html
<section>
	<form action="">
		<label for="nombre">
			<span>Cual es tu nombre?</span>
			<input type="text" id="nombre">
		 </label>
		 <input type="submit" value="Enviar">
	</form>
</section>
```

- **El elemento `form`** define el formulario en sí. El atributo `action` de este elemento indica dónde se enviarán los datos del formulario cuando el usuario haga clic en el botón de envío. En este caso, el atributo `action` está vacío, lo que significa que los datos del formulario se enviarán a la misma página que contiene el formulario.
- **El elemento `label`** proporciona un texto descriptivo para el elemento de entrada. El atributo `for` de este elemento se utiliza para vincular el elemento `label` con un elemento de entrada específico. En este caso, el atributo `for` está vinculado al elemento de entrada con el ID `nombre`.
- **El elemento `input`** es el elemento de entrada real. El atributo `type` de este elemento indica el tipo de entrada. En este caso, el atributo `type` está establecido en `text`, lo que indica que el usuario puede ingresar texto en el elemento de entrada.

## Otros ejemplos de inputs semánticos

Formulario simple:

```html
	  	<section>
            <form action="">
                <label for="nombre">
                    <span>Cual es tu nombre?</span>
                    <input type="text" id="nombre" placeholder="Tu nombre">
                </label>
                <label for="inicio-platzi">
                    <span>Que dia iniciaste en platzi?</span>
                    <input type="date" id="inicio-platzi">
                </label>
                <label for="horario">
                    <span>En que horario estudias?</span>
                    <input type="time" id="horario">
                </label>
            </form>
        </section>
```

Formulario de fechas exactas:

```html
<section>
            <form action="">
                <label for="hora">
                    <span>Hora:</span>
                    <input type="time" id="hora" name="hora">
                </label>
                <label for="dia">
                    <span>Dia:</span>
                    <input type="date" id="dia" name="dia">
                </label>
                <label for="semana">
                    <span>Semana:</span>
                    <input type="week" id="semana" name="semana">
                </label>
                <label for="mes">
                    <span>Mes:</span>
                    <input type="month" id="mes" name="mes">
                </label>
                <input type="submit" value="Enviar">
            </form>
        </section>
```

Formulario de un solo calendario con hora:

```html
<section>
            <form action="">
                <label for="calendario">
                    <span>Calendario</span>
                    <input type="datetime-local" id="calendario" name="calendario">
                    <input type="submit" value="Enviar">
                </label>
            </form>
</section>
```

## Select

```html
<select name="cursos" id="">
            <option value="JavaScript">JavaScript</option>
            <option value="Html5">Html5</option>
            <option value="CSS3">CSS3</option>
            <option value="WebStandars">Web Standars</option>
        </select>
```

El select es un elemento en el cual te permite seleccionar opciones predeterminadas para que el usuario pueda encontrar la opción deseada , pero para ello tendrías que evaluar que por lo general el usuario en móvil tiende a tener problemas con esto si es una lista mas larga, por lo que en cuestión de seleccionar un elemento para un formulario existe una forma mas amigable con el usuario de hacerlo:

```html
<input list="cursos">
        <datalist id="cursos">
            <option value="JavaScript"></option>
            <option value="Html5"></option>
            <option value="CSS3"></option>
            <option value="Web Standars"></option>
        </datalist>
```

El código anterior describe una forma de enviar información de opciones de elementos pero de una manera mas amigable, el único inconveniente con esto, es que si no validas el input antes de enviar información el usuario podrá enviar información que el haya escrito manualmente a tu formulario.

## Input type submit vs Button Tag

El **input type="submit"** es la mejor opción para enviar formularios. El **button tag** es la mejor opción para realizar acciones personalizadas.