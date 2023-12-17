
# Labels
```HTML
 <main>
        <form action="">
            <label for="name">
                <span>Cual es tu nombre?</span>
                <input type="text" id="name">
            </label>
            <label for="started-studying">
                <span>Que dia comenzaste en platzi?</span>
                <input type="date" id="started-studying">
            </label>
            <label for="time-to-study">
                <span>En que horario estudias?</span>
                <input type="time" id="time-to-study">
            </label>
        </form>
 </main>
```

El uso del **`Label`** en HTML es que permite cierta accesibilidad a programas que ayudan con discapacidades, el `label` permite que no solo tengamos que ir a darle `click` a cierta caja de ingreso de información, sino que permite que sí le damos `click` a la pregunta este nos dará el puntero para escribir directamente en la caja del `input`.

# Alt
```HTML
<section>
   <img src="image.ext" alt="Descripcion de la imagen">
</section>
```

El uso de `alt` permite que programas de ayuda a discapacitados describa la imagen cuando se esté leyendo lo que hay en la imagen, esto siempre es esencial para el empleo de usuario con estas limitaciones.

# Titles

```HTML
<section>
	<img src="image.ext" alt="Descripcion de la imagen" title="Descripcion     corta de          la imagen">
 </section>
```
La utilización de `title` permite que al hacer un  pequeño movimiento del ratón sobre la imagen (`hover`) describa la imagen sin dar ningún `click`.

