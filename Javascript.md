# Cheat Sheet: JavaScript Moderno (ES6+)

Guía rápida de las novedades y usos más comunes de JavaScript en 2024/2025.

## 📦 Variables y Constantes
¡Olvida `var`!

| Tipo | Uso | Scope |
| :--- | :--- | :--- |
| `const` | **Por defecto**. No reasignable. | Bloque `{}` |
| `let` | Si necesitas cambiar el valor. | Bloque `{}` |
| `var` | ❌ Evitar. Hoisting problemático. | Función |

## 🏹 Arrow Functions
Sintaxis más limpia y `this` léxico (no cambia el contexto).

```javascript
// Tradicional
function sumar(a, b) {
  return a + b;
}

// Arrow Function
const sumar = (a, b) => a + b; // Return implícito
const cuadrado = x => x * x;   // Sin paréntesis si es un solo arg
```

## 🪄 Desestructuración y Operadores

### Objetos y Arreglos
Extrae valores fácilmente.
```javascript
const usuario = { nombre: 'Maykol', edad: 25, rol: 'Dev' };
const { nombre, rol } = usuario; // Crea variables 'nombre' y 'rol'

const colores = ['rojo', 'verde', 'azul'];
const [primero, ...resto] = colores; 
// primero = 'rojo', resto = ['verde', 'azul']
```

### Spread (...) y Rest (...)
```javascript
// Copiar/Fusionar Objetos (Inmutabilidad)
const nuevoUsuario = { ...usuario, activo: true };

// Arrays
const numeros = [1, 2, 3];
const masNumeros = [...numeros, 4, 5]; // [1, 2, 3, 4, 5]
```

## 🛡️ Seguridad de Tipos "Lite"

### Optional Chaining (`?.`)
Accede a propiedades anidadas sin romper el código si algo no existe.
```javascript
const calle = usuario?.direccion?.calle; 
// Devuelve undefined si usuario o direccion no existen, no crashea.
```

### Nullish Coalescing (`??`)
Valor por defecto SOLO si es `null` o `undefined` (no para 0 o false).
```javascript
const cantidad = input ?? 10;
```

## ⚡ Asincronía Moderno (Async/Await)
La forma estándar de manejar promesas.

```javascript
// Mucho más legible que .then().catch()
async function obtenerDatos() {
  try {
    const respuesta = await fetch('https://api.ejemplo.com/data');
    const datos = await respuesta.json();
    console.log(datos);
  } catch (error) {
    console.error('Error:', error);
  }
}
```

## 🔄 Manipulación de Arrays

### Métodos Esenciales
| Método | Descripción |
| :--- | :--- |
| `.map()` | Transforma cada elemento y retorna un **nuevo array**. |
| `.filter()` | Retorna un **nuevo array** con elementos que cumplan la condición. |
| `.find()` | Retorna el **primer elemento** que cumpla la condición. |
| `.reduce()` | Reduce el array a un único valor (acumulador). |
| `.includes()` | `true` si el elemento existe. |

### Lo Nuevo (ES2023/2024)
Métodos que no mutan el original (retornan copia).
```javascript
const ordenados = numeros.toSorted();   // vs .sort() (que muta)
const invertidos = numeros.toReversed(); // vs .reverse()
const empalmados = numeros.toSpliced(0, 1); // vs .splice()

// Agrupamiento (ES2024 - Verificar soporte)
// const porRol = Object.groupBy(usuarios, ({ rol }) => rol);
```

## 📦 Módulos
Importar y exportar código entre archivos.

```javascript
// archivo.js
export const sumar = (a, b) => a + b;
export default function principal() { ... }

// main.js
import principal, { sumar } from './archivo.js';
```

## 🌐 DOM y APIs del Navegador

### Selección de Elementos
Lo moderno es usar `querySelector` (CSS selectors).

| Método | Descripción | Retorna |
| :--- | :--- | :--- |
| `document.querySelector('.clase')` | Primer elemento que coincide. | Elemento / null |
| `document.querySelectorAll('div')` | Todos los que coinciden. | NodeList (parecido a Array) |
| `el.closest('.contenedor')` | Busca el ancestro más cercano. | Elemento / null |

### Manipulación
```javascript
const el = document.querySelector('#mi-id');

// Contenido
el.textContent = 'Nuevo texto'; // Seguro (escapa HTML)
el.innerHTML = '<span>Peligro</span>'; // Renderea HTML (cuidado XSS)

// Clases
el.classList.add('activo');
el.classList.remove('oculto');
el.classList.toggle('dark-mode');

// Atributos
el.setAttribute('data-id', '123');
el.getAttribute('src');
el.remove(); // Eliminar elemento
```

### Eventos
```javascript
const btn = document.querySelector('button');

// Escuchar evento
btn.addEventListener('click', (event) => {
  event.preventDefault(); // Evita recarga en forms
  event.stopPropagation(); // Evita burbujeo hasta el padre
  console.log('Click en:', event.target);
});

// Event Delegation (Mejor rendimiento para listas)
document.body.addEventListener('click', (e) => {
  if (e.target.matches('.btn-borrar')) {
    eliminarItem(e.target);
  }
});
```

### Storage y Timers
```javascript
// LocalStorage (Persiste al cerrar)
localStorage.setItem('usuario', 'Maykol');
const user = localStorage.getItem('usuario');
localStorage.removeItem('usuario');

// SessionStorage (Se borra al cerrar pestaña)
sessionStorage.setItem('token', '123');

// Timers
setTimeout(() => console.log('1 segundo después'), 1000);
setInterval(() => console.log('Cada 2 segundos'), 2000);
```

## 🐞 Debugging Pro
Dejando atrás el simple `console.log`.

```javascript
console.table(usuarios); // Muestra arrays/objetos en una tabla bonita
console.group('Detalles'); // Agrupa logs
console.log('Info 1');
console.groupEnd();
console.time('Loop'); // Inicia cronómetro
// ... código ...
console.timeEnd('Loop'); // Muestra tiempo transcurrido
```
