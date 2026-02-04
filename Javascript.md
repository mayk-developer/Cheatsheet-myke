# ⚡ Guía Completa de JavaScript

El lenguaje de la web - Desde cero hasta avanzado

---

## 💡 ¿Qué es JavaScript?

JavaScript es el lenguaje de programación de la web. Permite hacer páginas interactivas, aplicaciones web, servidores, apps móviles y más.

> [!INFO] ℹ️ ¿Dónde se usa JavaScript?
> *   **Frontend** - Interactividad en páginas web
> *   **Backend** - Servidores con Node.js
> *   **Mobile** - Apps con React Native
> *   **Desktop** - Apps con Electron

**Tu primer código:**
```javascript
// Mostrar mensaje en consola
console.log("¡Hola, JavaScript!");

// Mostrar alerta en el navegador
alert("¡Bienvenido!");
```

> [!TIP] 💡 Para practicar:
> *   Abre tu navegador → Clic derecho → "Inspeccionar" → Pestaña "Console"
> *   O usa **codepen.io**, **jsfiddle.net**, o VS Code

---

## 1. Variables

Las variables guardan datos que puedes usar después.

```javascript
// Tres formas de declarar variables

let nombre = "Juan";       // Puede cambiar
const PI = 3.14159;         // Constante, NO puede cambiar
var edad = 25;              // Antigua forma (evitar)

// Cambiar valor
nombre = "María";           // ✅ OK con let
PI = 3;                     // ❌ Error! const no puede cambiar
```

<table style="width: 100%; border-collapse: collapse; margin: 15px 0; font-size: 14px;">
  <thead style="background: #f7df1e; color: #323330;">
    <tr>
      <th style="border: 1px solid #ddd; padding: 10px;">Palabra</th>
      <th style="border: 1px solid #ddd; padding: 10px;">¿Puede cambiar?</th>
      <th style="border: 1px solid #ddd; padding: 10px;">¿Cuándo usar?</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>let</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">✅ Sí</td>
      <td style="border: 1px solid #ddd; padding: 10px;">Valores que cambian</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;"><code>const</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">❌ No</td>
      <td style="border: 1px solid #ddd; padding: 10px;">Valores fijos (preferir siempre)</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>var</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">✅ Sí</td>
      <td style="border: 1px solid #ddd; padding: 10px;">⚠️ Evitar (código antiguo)</td>
    </tr>
  </tbody>
</table>

> [!TIP] 💡 Regla:
> Usa `const` por defecto. Solo usa `let` si necesitas cambiar el valor.

---

## 2. Tipos de datos

```javascript
// String (texto)
const nombre = "Juan";
const saludo = 'Hola';
const mensaje = `Hola, ${nombre}`;  // Template literal

// Number (número)
const edad = 25;
const precio = 19.99;
const negativo = -10;

// Boolean (verdadero/falso)
const activo = true;
const eliminado = false;

// Undefined (sin valor asignado)
let sinValor;
console.log(sinValor);  // undefined

// Null (valor vacío intencional)
const vacio = null;

// Array (lista)
const frutas = ["manzana", "banana", "naranja"];

// Object (objeto)
const persona = {
    nombre: "Juan",
    edad: 25,
    ciudad: "Lima"
};

// Verificar tipo
typeof nombre;   // "string"
typeof edad;     // "number"
typeof activo;   // "boolean"
```

---

## 3. Operadores

```javascript
// Aritméticos
5 + 3    // 8  Suma
5 - 3    // 2  Resta
5 * 3    // 15 Multiplicación
5 / 3    // 1.666... División
5 % 3    // 2  Módulo (resto)
5 ** 3   // 125 Potencia

// Asignación
let x = 10;
x += 5;   // x = x + 5  → 15
x -= 3;   // x = x - 3  → 12
x++;      // x = x + 1  → 13
x--;      // x = x - 1  → 12

// Comparación
5 == "5"   // true  (compara valor, NO tipo)
5 === "5"  // false (compara valor Y tipo) ✅ USAR ESTE
5 !== "5"  // true  (diferente valor O tipo)
5 > 3      // true
5 >= 5     // true
5 < 3      // false

// Lógicos
true && true    // true  (AND - ambos verdaderos)
true || false   // true  (OR - al menos uno verdadero)
!true           // false (NOT - niega)
```

> [!WARNING] ⚠️ Siempre usa `===` en lugar de `==`
> `==` puede dar resultados inesperados al comparar tipos diferentes.

---

## 4. Strings (cadenas de texto)

```javascript
const texto = "Hola Mundo";

// Propiedades y métodos
texto.length;              // 10 (longitud)
texto.toUpperCase();       // "HOLA MUNDO"
texto.toLowerCase();       // "hola mundo"
texto.includes("Mundo");  // true
texto.startsWith("Hola"); // true
texto.endsWith("do");     // true
texto.indexOf("Mundo");   // 5 (posición)
texto.slice(0, 4);        // "Hola" (extraer)
texto.replace("Mundo", "JS");  // "Hola JS"
texto.split(" ");         // ["Hola", "Mundo"]
texto.trim();             // Quita espacios al inicio/final

// Acceder a caracteres
texto[0];                  // "H"
texto.charAt(0);          // "H"

// Template literals (interpolación)
const nombre = "Juan";
const edad = 25;
const mensaje = `Hola, soy ${nombre} y tengo ${edad} años`;
// "Hola, soy Juan y tengo 25 años"

// Concatenación
const saludo = "Hola, " + nombre + "!";
```

---

## 5. Condicionales

```javascript
// if - else if - else
const edad = 18;

if (edad >= 18) {
    console.log("Eres mayor de edad");
} else if (edad >= 13) {
    console.log("Eres adolescente");
} else {
    console.log("Eres niño");
}

// Operador ternario (if corto)
const mensaje = edad >= 18 ? "Mayor" : "Menor";

// Switch
const dia = "lunes";

switch (dia) {
    case "lunes":
        console.log("Inicio de semana");
        break;
    case "viernes":
        console.log("¡Por fin viernes!");
        break;
    case "sábado":
    case "domingo":
        console.log("Fin de semana");
        break;
    default:
        console.log("Día normal");
}
```

> [!INFO] ℹ️ Valores "falsy" en JavaScript:
> `false`, `0`, `""`, `null`, `undefined`, `NaN`
> Todo lo demás es "truthy" (se evalúa como verdadero).

---

## 6. Arrays (listas)

```javascript
// Crear array
const frutas = ["manzana", "banana", "naranja"];
const numeros = [1, 2, 3, 4, 5];
const mixto = [1, "hola", true, null];

// Acceder a elementos (índice empieza en 0)
frutas[0];      // "manzana"
frutas[1];      // "banana"
frutas.length;  // 3

// Modificar
frutas[0] = "pera";  // Cambiar elemento

// Métodos básicos
frutas.push("uva");      // Agregar al final
frutas.pop();            // Quitar del final
frutas.unshift("kiwi");  // Agregar al inicio
frutas.shift();          // Quitar del inicio

// Buscar
frutas.includes("banana");  // true
frutas.indexOf("banana");   // 1 (posición)
frutas.find(f => f === "banana");  // "banana"

// Otros métodos útiles
frutas.slice(1, 3);       // Extraer parte ["banana", "naranja"]
frutas.concat(["mango"]); // Unir arrays
frutas.join(", ");        // "manzana, banana, naranja"
frutas.reverse();         // Invertir orden
frutas.sort();            // Ordenar alfabéticamente
```

**Métodos de iteración (muy importantes):**
```javascript
const numeros = [1, 2, 3, 4, 5];

// forEach - ejecutar acción por cada elemento
numeros.forEach(num => console.log(num));

// map - transformar cada elemento (devuelve nuevo array)
const dobles = numeros.map(num => num * 2);
// [2, 4, 6, 8, 10]

// filter - filtrar elementos (devuelve nuevo array)
const mayores = numeros.filter(num => num > 2);
// [3, 4, 5]

// find - encontrar primer elemento que cumple condición
const encontrado = numeros.find(num => num > 3);
// 4

// reduce - reducir a un solo valor
const suma = numeros.reduce((total, num) => total + num, 0);
// 15

// some - ¿alguno cumple?
numeros.some(num => num > 4);   // true

// every - ¿todos cumplen?
numeros.every(num => num > 0);  // true
```

---

## 7. Bucles (loops)

```javascript
// for clásico
for (let i = 0; i < 5; i++) {
    console.log(i);  // 0, 1, 2, 3, 4
}

// for...of (para arrays) ✅ Recomendado
const frutas = ["manzana", "banana", "naranja"];
for (const fruta of frutas) {
    console.log(fruta);
}

// for...in (para objetos)
const persona = { nombre: "Juan", edad: 25 };
for (const key in persona) {
    console.log(key, persona[key]);
}

// while
let contador = 0;
while (contador < 5) {
    console.log(contador);
    contador++;
}

// do...while (ejecuta al menos una vez)
do {
    console.log(contador);
    contador++;
} while (contador < 10);

// break y continue
for (let i = 0; i < 10; i++) {
    if (i === 3) continue;  // Salta a la siguiente iteración
    if (i === 7) break;     // Sale del bucle
    console.log(i);
}
```

---

## 8. Objetos

```javascript
// Crear objeto
const persona = {
    nombre: "Juan",
    edad: 25,
    ciudad: "Lima",
    hobbies: ["leer", "programar"],
    direccion: {
        calle: "Av. Principal",
        numero: 123
    },
    // Método (función dentro del objeto)
    saludar() {
        return `Hola, soy ${this.nombre}`;
    }
};

// Acceder a propiedades
persona.nombre;           // "Juan"
persona["nombre"];        // "Juan"
persona.direccion.calle;  // "Av. Principal"
persona.saludar();        // "Hola, soy Juan"

// Modificar propiedades
persona.edad = 26;
persona.trabajo = "Developer";  // Agregar nueva propiedad
delete persona.ciudad;         // Eliminar propiedad

// Métodos útiles
Object.keys(persona);    // ["nombre", "edad", ...]
Object.values(persona);  // ["Juan", 25, ...]
Object.entries(persona); // [["nombre","Juan"], ...]

// Verificar si existe propiedad
"nombre" in persona;      // true
persona.hasOwnProperty("nombre");  // true
```

**Destructuring (desestructuración):**
```javascript
// Extraer propiedades en variables
const { nombre, edad } = persona;
console.log(nombre);  // "Juan"

// Con alias
const { nombre: nombrePersona } = persona;

// Valor por defecto
const { pais = "Perú" } = persona;

// Destructuring de arrays
const [primero, segundo] = [1, 2, 3];
console.log(primero);  // 1
```

**Spread operator (...):**
```javascript
// Copiar objeto
const copia = { ...persona };

// Combinar objetos
const completo = { ...persona, pais: "Perú" };

// Copiar array
const copiaFrutas = [...frutas];

// Combinar arrays
const todos = [...frutas, ...verduras];
```

---

## 9. Funciones

```javascript
// Función declarada
function saludar(nombre) {
    return `Hola, ${nombre}!`;
}
saludar("Juan");  // "Hola, Juan!"

// Función expresada
const sumar = function(a, b) {
    return a + b;
};

// Arrow function (función flecha) ✅ Moderna
const multiplicar = (a, b) => {
    return a * b;
};

// Arrow function corta (return implícito)
const doble = n => n * 2;
const suma = (a, b) => a + b;

// Parámetros por defecto
const saludar = (nombre = "Invitado") => `Hola, ${nombre}`;
saludar();        // "Hola, Invitado"
saludar("Ana");  // "Hola, Ana"

// Rest parameters (...)
const sumarTodos = (...numeros) => {
    return numeros.reduce((a, b) => a + b, 0);
};
sumarTodos(1, 2, 3, 4);  // 10
```

> [!TIP] 💡 ¿Cuándo usar cada tipo?
> *   **Arrow functions**: Para la mayoría de casos ✅
> *   **function**: Cuando necesitas `this` propio o hoisting

---

## 10. Asincronía: Promises y Async/Await

JavaScript puede ejecutar código sin bloquear el programa (ej: peticiones HTTP).

```javascript
// Promise
const promesa = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("¡Éxito!");
        // reject("Error");
    }, 1000);
});

// Usar Promise con .then()
promesa
    .then(resultado => console.log(resultado))
    .catch(error => console.log(error));

// Async/Await (más limpio) ✅
async function obtenerDatos() {
    try {
        const resultado = await promesa;
        console.log(resultado);
    } catch (error) {
        console.log("Error:", error);
    }
}
```

**Fetch API (peticiones HTTP):**
```javascript
// GET - Obtener datos
async function obtenerUsuarios() {
    try {
        const response = await fetch('https://api.ejemplo.com/usuarios');
        const datos = await response.json();
        console.log(datos);
    } catch (error) {
        console.log("Error:", error);
    }
}

// POST - Enviar datos
async function crearUsuario(usuario) {
    const response = await fetch('https://api.ejemplo.com/usuarios', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(usuario)
    });
    return response.json();
}
```

---

## 11. DOM - Manipular HTML

```javascript
// Seleccionar elementos
const elemento = document.getElementById("miId");
const elemento = document.querySelector(".miClase");      // Primero
const elementos = document.querySelectorAll(".miClase");  // Todos

// Modificar contenido
elemento.textContent = "Nuevo texto";
elemento.innerHTML = "<strong>HTML</strong>";

// Modificar estilos
elemento.style.color = "red";
elemento.style.backgroundColor = "#f0f0f0";

// Clases
elemento.classList.add("nueva-clase");
elemento.classList.remove("vieja-clase");
elemento.classList.toggle("activo");
elemento.classList.contains("activo");  // true/false

// Atributos
elemento.getAttribute("href");
elemento.setAttribute("href", "https://...");

// Crear elementos
const nuevoDiv = document.createElement("div");
nuevoDiv.textContent = "Soy nuevo";
document.body.appendChild(nuevoDiv);

// Eliminar elemento
elemento.remove();
```

**Eventos:**
```javascript
// Agregar evento
const boton = document.querySelector("#miBoton");

boton.addEventListener("click", () => {
    console.log("¡Clic!");
});

// Con parámetro event
boton.addEventListener("click", (event) => {
    event.preventDefault();  // Prevenir acción por defecto
    console.log(event.target);  // Elemento clickeado
});

// Eventos comunes
// click, dblclick, mouseenter, mouseleave
// keydown, keyup, keypress
// submit, change, input, focus, blur
// load, DOMContentLoaded, scroll, resize

// Esperar a que cargue el DOM
document.addEventListener("DOMContentLoaded", () => {
    // Tu código aquí
});
```

---

## 12. Clases (POO)

```javascript
class Persona {
    // Constructor
    constructor(nombre, edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    // Método
    saludar() {
        return `Hola, soy ${this.nombre}`;
    }

    // Getter
    get info() {
        return `${this.nombre} (${this.edad})`;
    }

    // Setter
    set nuevaEdad(edad) {
        if (edad > 0) this.edad = edad;
    }

    // Método estático
    static especie() {
        return "Homo Sapiens";
    }
}

// Crear instancia
const juan = new Persona("Juan", 25);
juan.saludar();    // "Hola, soy Juan"
juan.info;         // "Juan (25)"
Persona.especie(); // "Homo Sapiens"

// Herencia
class Estudiante extends Persona {
    constructor(nombre, edad, carrera) {
        super(nombre, edad);  // Llama al constructor padre
        this.carrera = carrera;
    }

    estudiar() {
        return `${this.nombre} estudia ${this.carrera}`;
    }
}

const ana = new Estudiante("Ana", 20, "Ingeniería");
ana.saludar();   // "Hola, soy Ana" (heredado)
ana.estudiar();  // "Ana estudia Ingeniería"
```

---

## 13. Módulos (import/export)

```javascript
// archivo: utils.js

// Exportar función
export const sumar = (a, b) => a + b;

// Exportar clase
export class Calculadora { ... }

// Exportar por defecto (solo uno por archivo)
export default function principal() { ... }

// ─────────────────────────────────
// archivo: app.js

// Importar específicos
import { sumar, Calculadora } from './utils.js';

// Importar default
import principal from './utils.js';

// Importar todo
import * as utils from './utils.js';
utils.sumar(2, 3);

// Importar con alias
import { sumar as add } from './utils.js';
```

> [!INFO] ℹ️ Para usar módulos en HTML:
> ```html
> <script type="module" src="app.js"></script>
> ```

---

## 14. Manejo de errores

```javascript
try {
    // Código que puede fallar
    const resultado = operacionRiesgosa();
} catch (error) {
    // Si hay error, se ejecuta esto
    console.error("Error:", error.message);
} finally {
    // Siempre se ejecuta (opcional)
    console.log("Finalizado");
}

// Lanzar error personalizado
function dividir(a, b) {
    if (b === 0) {
        throw new Error("No se puede dividir por cero");
    }
    return a / b;
}
```

---

## 15. LocalStorage

```javascript
// Guardar dato
localStorage.setItem("nombre", "Juan");

// Obtener dato
const nombre = localStorage.getItem("nombre");

// Eliminar dato
localStorage.removeItem("nombre");

// Limpiar todo
localStorage.clear();

// Guardar objeto (convertir a JSON)
const usuario = { nombre: "Juan", edad: 25 };
localStorage.setItem("usuario", JSON.stringify(usuario));

// Recuperar objeto
const recuperado = JSON.parse(localStorage.getItem("usuario"));
```

> [!TIP] 💡 localStorage vs sessionStorage:
> *   **localStorage** - Persiste incluso al cerrar el navegador
> *   **sessionStorage** - Se borra al cerrar la pestaña

---

## 📋 Referencia rápida

<table style="width: 100%; border-collapse: collapse; margin: 15px 0; font-size: 14px;">
  <thead style="background: #f7df1e; color: #323330;">
    <tr>
      <th style="border: 1px solid #ddd; padding: 10px;">Categoría</th>
      <th style="border: 1px solid #ddd; padding: 10px;">Métodos/Operadores</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;"><strong>Strings</strong></td>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>length, toUpperCase(), toLowerCase(), includes(), indexOf(), slice(), split(), trim(), replace()</code></td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;"><strong>Arrays</strong></td>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>length, push(), pop(), shift(), unshift(), map(), filter(), find(), reduce(), forEach(), includes(), indexOf(), slice(), sort(), reverse()</code></td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;"><strong>Objetos</strong></td>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>Object.keys(), Object.values(), Object.entries(), hasOwnProperty()</code></td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;"><strong>Math</strong></td>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>Math.random(), Math.floor(), Math.ceil(), Math.round(), Math.max(), Math.min(), Math.abs(), Math.pow()</code></td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;"><strong>Date</strong></td>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>new Date(), getFullYear(), getMonth(), getDate(), getHours(), getMinutes(), toLocaleDateString()</code></td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;"><strong>JSON</strong></td>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>JSON.stringify(), JSON.parse()</code></td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;"><strong>Console</strong></td>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>console.log(), console.error(), console.warn(), console.table(), console.time()</code></td>
    </tr>
  </tbody>
</table>

---

## ✓ Checklist de aprendizaje

- [ ] Entiendo variables (let, const) y tipos de datos
- [ ] Sé usar operadores aritméticos y de comparación
- [ ] Puedo trabajar con strings y sus métodos
- [ ] Domino condicionales (if, else, switch, ternario)
- [ ] Sé crear y manipular arrays con sus métodos
- [ ] Entiendo bucles (for, while, for...of)
- [ ] Puedo crear y usar objetos
- [ ] Sé escribir funciones (normales y arrow)
- [ ] Entiendo async/await y Promises
- [ ] Puedo manipular el DOM (seleccionar, modificar, eventos)
- [ ] Sé usar clases y herencia
- [ ] Entiendo módulos (import/export)
- [ ] Puedo manejar errores con try/catch
- [ ] Sé usar localStorage
