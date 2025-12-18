# Cheat Sheet: HTML Moderno (HTML5)

Guía rápida de etiquetas, estructura semántica y atributos modernos para desarrollo web.

## Estructura Básica

**Plantilla Inicial (Boilerplate)**
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Descripción breve del sitio para SEO">
    <title>Título de la Página</title>
    <link rel="stylesheet" href="styles.css">
    <script src="script.js" defer></script>
</head>
<body>
    <!-- Contenido aquí -->
</body>
</html>
```

## Semántica y Layout

Usa estas etiquetas para definir la estructura significativa del documento, no solo para estilos.

**Estructura Principal**
```html
<header>    <!-- Encabezado del sitio o sección -->
<nav>       <!-- Enlaces de navegación principales -->
<main>      <!-- Contenido principal único de la página -->
<section>   <!-- Sección temática agrupadora -->
<article>   <!-- Contenido independiente (post, noticia) -->
<aside>     <!-- Contenido relacionado indirectamente (sidebar) -->
<footer>    <!-- Pie de página -->
```

**Contenido Gráfico**
```html
<figure>
    <img src="imagen.jpg" alt="Descripción de la imagen">
    <figcaption>Pie de foto descriptivo</figcaption>
</figure>
```

## Formularios Modernos

**Inputs Especializados**
Teclados móviles y validación automática.
```html
<input type="email" name="email" required>
<input type="tel" pattern="[0-9]{9}"> <!-- RegEx pattern -->
<input type="url">
<input type="number" min="0" max="100" step="5">
<input type="date"> <!-- Selector de fecha nativo -->
<input type="color"> <!-- Selector de color -->
<input type="search">
<input type="password">
```

**Select y Datalist (Autocompletado)**
```html
<!-- Select Clásico -->
<select name="opcion">
    <option value="1">Opción 1</option>
    <option value="2" selected>Opción 2</option>
</select>

<!-- Datalist (Input con sugerencias) -->
<input list="navegadores" name="browser">
<datalist id="navegadores">
    <option value="Chrome">
    <option value="Firefox">
    <option value="Safari">
</datalist>
```

**Agrupación y Etiquetas**
```html
<form action="/submit" method="POST">
    <fieldset>
        <legend>Datos Personales</legend>
        
        <label for="nombre">Nombre:</label>
        <input type="text" id="nombre" name="nombre">
    </fieldset>
</form>
```

## Multimedia Avanzada

**Imágenes Responsivas y Lazy Loading**
```html
<!-- Carga perezosa nativa para optimizar rendimiento -->
<img src="foto.jpg" alt="Foto" loading="lazy" width="800" height="600">

<!-- Picture: Distintas imágenes según dispositivo (Art Direction) -->
<picture>
    <source media="(min-width: 800px)" srcset="grande.webp">
    <source media="(min-width: 400px)" srcset="mediana.webp">
    <img src="pequena.jpg" alt="Descripción">
</picture>
```

**Video y Audio**
```html
<video controls poster="miniatura.jpg" width="600">
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    Tu navegador no soporta video.
</video>

<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
</audio>
```

## Interactividad Nativa (Sin JS)

**Detalles (Acordeón)**
```html
<details>
    <summary>Más información (Click para abrir)</summary>
    <p>Contenido oculto que se despliega.</p>
</details>
```

**Diálogo (Modal)**
```html
<dialog id="miModal">
    <p>¡Hola! Soy un modal nativo.</p>
    <form method="dialog">
        <button>Cerrar</button>
    </form>
</dialog>
<!-- Requiere JS simple para abrir: document.getElementById('miModal').showModal() -->
```

## Metadatos Vitales (SEO y Social)

**Meta Tags Esenciales**
```html
<!-- Control de Viewport para Responsividad -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- SEO -->
<meta name="description" content="Resumen de 150 caracteres">
<meta name="robots" content="index, follow">
```

**Open Graph (Redes Sociales)**
```html
<meta property="og:title" content="Título para Facebook/LinkedIn">
<meta property="og:description" content="Descripción para redes">
<meta property="og:image" content="https://misitio.com/imagen.jpg">
<meta property="og:url" content="https://misitio.com/pagina">
```

## Accesibilidad (A11y)

**Reglas de Oro**
- Siempre usa `alt` en imágenes.
- Usa `label` conectado a inputs mediante `for` e `id`.
- Respeta la jerarquía de encabezados (`h1` -> `h2` -> `h3`).

**Atributos ARIA (Cuando la semántica no basta)**
```html
<!-- Elementos no semánticos que actúan como botones -->
<div role="button" tabindex="0" aria-pressed="false">Botón Falso</div>

<!-- Etiquetas para lectores de pantalla -->
<button aria-label="Cerrar menú">X</button>

<!-- Estado dinámico -->
<nav aria-expanded="true">...</nav>
```

## Atributos Globales Útiles

- `id="unico"`: Identificador único.
- `class="multiple"`: Clases CSS.
- `data-*="valor"`: Datos personalizados (ej. `data-user-id="123"`).
- `contenteditable="true"`: Hace el elemento editable por el usuario.
- `hidden`: Oculta el elemento (equivalente a `display: none`).
- `tabindex="0"`: Hace el elemento focuseable (navegación por teclado).

## Scripts

```html
<!-- Async: Carga paralela, ejecuta en cuanto descarga (orden no garantizado) -->
<script src="analytics.js" async></script>

<!-- Defer: Carga paralela, espera a que el HTML termine de parsear (recomendado) -->
<script src="app.js" defer></script>

<!-- Módulos ES6 -->
<script type="module" src="main.js"></script>
```
