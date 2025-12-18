# Cheat Sheet: CSS Moderno

Guía de referencia para diseño web moderno, incluyendo Grid, Flexbox, nuevas features (2024+) y arquitectura escalable.

## Reset & Defaults

Un reset moderno y minimalista es esencial para comenzar.

```css
*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html {
  color-scheme: dark light; /* Soporte nativo modo oscuro */
  font-family: system-ui, sans-serif;
  line-height: 1.5;
}

img, video, svg {
  max-width: 100%;
  display: block;
}
```

## Layout Moderno

### Flexbox (Unidimensional)
Para alinear elementos en una fila o columna.
```css
.container {
  display: flex;
  justify-content: center; /* Eje principal: center, space-between */
  align-items: center;     /* Eje cruzado: center, stretch */
  gap: 1rem;               /* Espacio entre elementos */
  flex-wrap: wrap;         /* Permitir múltiples líneas */
}
```

### CSS Grid (Bidimensional)
Para crear grillas complejas.
```css
.grid {
  display: grid;
  /* 3 columnas automáticas pero con mínimo de 300px */
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

.item {
  grid-column: span 2; /* Ocupar 2 columnas */
}
```

### Container Queries (Lo Nuevo)
Estilos basados en el tamaño del **contenedor**, no de la pantalla. Vital para componentes reutilizables.
```css
.card-container {
  container-type: inline-size;
  container-name: card;
}

@container card (min-width: 500px) {
  .card-content {
    flex-direction: row; /* Cambia layout si el contenedor es ancho */
    font-size: 1.2rem;
  }
}
```

## Selectores de Nueva Generación

### :has() (El Selector Padre)
Selecciona un elemento si contiene cierto hijo o estado. "Si el padre tiene X...".
```css
/* Estila la tarjeta SOLO si tiene una imagen dentro */
.card:has(img) {
  padding: 0;
}

/* Estilar label si el input siguiente está validado */
label:has(+ input:valid) {
  color: green;
}
```

### :is() y :where()
Hacen el código más limpio.
```css
/* Antes */
header h1, header h2, .hero h1, .hero h2 { ... }

/* Ahora */
:is(header, .hero) :is(h1, h2) {
  color: navy;
}
```
*Nota: `:where()` es igual pero su especificidad es siempre 0 (fácil de sobrescribir).*

### Nesting (Anidamiento Nativo)
Ya no necesitas SASS para esto (soportado en navegadores modernos).
```css
.card {
  background: white;
  
  & .title {
    font-weight: bold;
  }

  &:hover {
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
  }
  
  @media (min-width: 768px) {
    font-size: 1.2rem;
  }
}
```

## Variables y Funciones Útiles

### Custom Properties (Variables)
```css
:root {
  --primary: #3b82f6;
  --spacing-md: 1rem;
}

.btn {
  background: var(--primary);
  padding: var(--spacing-md);
}
```

### clamp(), min(), max()
Tipografía y espaciado fluido sin media queries.
```css
h1 {
  /* Mínimo 2rem, ideal 5vw, máximo 4rem */
  font-size: clamp(2rem, 5vw + 1rem, 4rem); 
  
  /* Ancho: 100% pero nunca más de 600px */
  width: min(100%, 600px); 
}
```

## Colores Modernos (Espacio P3/OKLCH)

Accede a colores más vibrantes y predecibles.
```css
.vibrant {
  /* color(display-p3 r g b) para monitores Apple/Alta gama */
  color: oklch(60% 0.2 250); /* Lightness, Chroma, Hue */
}
```

## Arquitectura y Mantenimiento

### Capas (Cascade Layers)
Organiza la precedencia de tus estilos sin pelear con `!important` o especificidad.
```css
@layer reset, base, components, utilities;

@layer reset {
  /* Estilos de reset */
}

@layer components {
  .btn { background: red; } /* Gana a 'base' aunque tenga menos selectores */
}
```

## Pseudo-clases Clásicas pero Vitales
- `:nth-child(2)`: Segundo elemento.
- `:not(.active)`: Todo lo que no tenga la clase.
- `:focus-visible`: Foco solo cuando se usa teclado (mejor UX).
- `::before / ::after`: Elementos decorativos sin ensuciar HTML.

## Centrado Absoluto (El Clásico)
```css
.center {
  display: grid;
  place-items: center;
  /* O también */
  /* display: flex; justify-content: center; align-items: center; */
  min-height: 100vh;
}
```
