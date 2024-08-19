# Presentación: Introducción a Web Components


---
## ¿Qué son los Web Components?

Los Web Components son un conjunto de tecnologías que permiten crear elementos HTML personalizados, reutilizables y encapsulados, que se pueden utilizar en aplicaciones web. Estas tecnologías permiten a los desarrolladores construir elementos con su propio marcado, estilo y comportamiento, que pueden ser utilizados en cualquier parte de una página web.

  

---
### Principales tecnologías que componen los Web Components:

1. **Custom Elements**: Permiten definir nuevos elementos HTML y su comportamiento.
2. **Shadow DOM**: Proporciona un árbol DOM encapsulado y aislado para el componente, asegurando que su estructura, estilo y comportamiento no afecten al resto del documento.
3. **HTML Templates**: Permiten definir el contenido HTML que se puede reutilizar en el componente.
---

  

## Ejemplo de un Web Component

```html
<template id="my-component-template">
  <style>
    :host {
      display: block;
      font-family: Arial, sans-serif;
      border: 1px solid #ccc;
      padding: 10px;
    }
  </style>
  <div>
    <p>¡Hola, soy un Web Component!</p>
  </div>
</template>
<script>
  class MyComponent extends HTMLElement {
    constructor() {
      super();
      const template = document.getElementById('my-component-template').content;
      const shadowRoot = this.attachShadow({mode: 'open'});
      shadowRoot.appendChild(template.cloneNode(true));
    }
  
  customElements.define('my-component', MyComponent);
</script>
<my-component></my-component>
```

  

---

  

### Resultado del ejemplo:

Este componente crea un bloque con un borde, que contiene un párrafo de texto "¡Hola, soy un Web Component!". El estilo y la estructura del componente están completamente encapsulados.

  

---

  

## Ejemplo 2: Componente de botón personalizado

```html
<template id="custom-button-template">
  <style>
    button {
      background-color: #4CAF50;
      color: white;
      padding: 15px 32px;
      text-align: center;
      font-size: 16px;
      border: none;
      cursor: pointer;
    }
    button:hover {
      background-color: #45a049;
    }
  </style>
  <button><slot></slot></button>
</template>
<script>
  class CustomButton extends HTMLElement {
    constructor() {
      super();
      const template = document.getElementById('custom-button-template').content;
      const shadowRoot = this.attachShadow({mode: 'open'});
      shadowRoot.appendChild(template.cloneNode(true));
    }
  }
  customElements.define('custom-button', CustomButton);
</script>
<custom-button>Click Me!</custom-button>
```

  

---

  

### Resultado del ejemplo:

Este componente crea un botón estilizado con color de fondo verde y texto blanco. Al pasar el ratón sobre el botón, el color de fondo cambia a un tono más oscuro de verde. El contenido del botón se puede definir usando un `<slot>`, lo que permite flexibilidad al reutilizar el componente.

  

---

  

## Ejemplo 3: Componente de tarjeta con Shadow DOM

```html
<template id="card-component-template">
  <style>
    .card {
      box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
      padding: 16px;
      text-align: center;
      background-color: #f1f1f1;
    }
  </style>
  <div class="card">
    <h2><slot name="title"></slot></h2>
    <p><slot name="content"></slot></p>
  </div>
</template>
<script>
  class CardComponent extends HTMLElement {
    constructor() {
      super();
      const template = document.getElementById('card-component-template').content;
      const shadowRoot = this.attachShadow({mode: 'open'});
      shadowRoot.appendChild(template.cloneNode(true));
    }
  }
  customElements.define('card-component', CardComponent);
</script>
  
<card-component>
  <span slot="title">Tarjeta de Ejemplo</span>
  <span slot="content">Este es el contenido de la tarjeta.</span>
</card-component>

```

  

---

  

### Resultado del ejemplo:

Este componente crea una tarjeta estilizada con sombra, que contiene un título y un contenido. Los elementos de la tarjeta se pueden personalizar usando slots nombrados (`title` y `content`), lo que permite reutilizar este componente en diferentes contextos.

  

---

  

## Organización de carpetas en proyectos Vanilla JS con Web Components

Al trabajar con Web Components en proyectos Vanilla JS, es útil mantener una estructura de carpetas organizada. Aquí hay un ejemplo básico de cómo podría organizarse:


```powershell
project-root/
│
├── components/
│   ├── my-component/
│   │   ├── my-component.js
│   │   └── my-component.css
│   └── another-component/
│       ├── another-component.js
│       └── another-component.css
│
├── assets/
│   ├── images/
│   └── styles/
│
├── index.html
└── main.js

```

---

  

### Explicación:
- **components/**: Contiene todas las definiciones de Web Components. Cada componente tiene su propia carpeta con su lógica y estilos.
- **assets/**: Para archivos como imágenes y estilos globales.
- **index.html**: El archivo principal que carga los componentes.
- **main.js**: El archivo que importa y utiliza los componentes en la aplicación.

  

---

  

## Ventajas de los Web Components en comparación con Razor 4.8.1

- **Reutilización de código**: Los Web Components permiten crear elementos reutilizables que pueden ser compartidos entre diferentes proyectos o equipos, sin depender de un framework específico.

- **Encapsulación**: El uso del Shadow DOM asegura que los estilos y scripts de un componente no afecten ni sean afectados por el resto de la página, lo que facilita la creación de componentes verdaderamente modulares.

- **Interoperabilidad**: Los Web Components son compatibles con todos los frameworks y bibliotecas modernas, lo que permite su uso en cualquier entorno.

- **Estandarización**: A diferencia de Razor, que es específico de ASP.NET, los Web Components son una tecnología estándar soportada por todos los navegadores modernos.

  

---

## Conclusión

Los Web Components representan una herramienta poderosa para el desarrollo frontend, permitiendo la creación de componentes reutilizables, encapsulados y compatibles con cualquier tecnología. A medida que las aplicaciones web se vuelven más complejas, el uso de Web Components ofrece una solución eficiente y escalable, especialmente en comparación con tecnologías específicas como Razor.