# ⚛️ Guía Completa de React

Biblioteca para construir interfaces de usuario

---

## 💡 ¿Qué es React?

React es una biblioteca de JavaScript para construir interfaces de usuario (UI). Fue creada por Facebook y es la más popular para desarrollo web moderno.

<div style="background: #f8f9fa; border: 2px solid #e9ecef; border-radius: 10px; padding: 20px; margin: 15px 0;">
  <p style="text-align: center; margin-bottom: 15px;"><strong>Concepto clave: Componentes</strong></p>
  <div style="display: flex; align-items: center; justify-content: center; gap: 10px; flex-wrap: wrap;">
    <div style="background: #fff; border: 2px solid #61dafb; border-radius: 10px; padding: 12px 16px; text-align: center; min-width: 100px;">
      <div style="font-size: 24px;">🧩</div>
      <strong>Header</strong>
    </div>
    <div style="background: #fff; border: 2px solid #61dafb; border-radius: 10px; padding: 12px 16px; text-align: center; min-width: 100px;">
      <div style="font-size: 24px;">🧩</div>
      <strong>Sidebar</strong>
    </div>
    <div style="background: #fff; border: 2px solid #61dafb; border-radius: 10px; padding: 12px 16px; text-align: center; min-width: 100px;">
      <div style="font-size: 24px;">🧩</div>
      <strong>Card</strong>
    </div>
    <div style="background: #fff; border: 2px solid #61dafb; border-radius: 10px; padding: 12px 16px; text-align: center; min-width: 100px;">
      <div style="font-size: 24px;">🧩</div>
      <strong>Button</strong>
    </div>
  </div>
  <p style="text-align: center; margin-top: 15px; color: #666;">Tu app = Conjunto de componentes reutilizables</p>
</div>

> [!INFO] ℹ️ ¿Por qué usar React?
> *   **Componentes** - Código reutilizable y organizado
> *   **Virtual DOM** - Actualizaciones rápidas y eficientes
> *   **Unidireccional** - Datos fluyen en una dirección
> *   **Ecosistema** - Miles de librerías y recursos

---

## 1. Crear proyecto React

**Opción 1: Vite (Recomendado) ✅**
```bash
# Crear proyecto con Vite
npm create vite@latest mi-app -- --template react

# Entrar a la carpeta
cd mi-app

# Instalar dependencias
npm install

# Iniciar servidor de desarrollo
npm run dev
```

**Opción 2: Create React App**
```bash
# Crear proyecto con CRA
npx create-react-app mi-app

cd mi-app
npm start
```

**Estructura del proyecto:**
<div style="background: #1e1e1e; color: #d4d4d4; padding: 15px; border-radius: 8px; font-family: monospace; font-size: 13px;">
<span style="color: #dcb67a;">📁 mi-app/</span><br>
├── <span style="color: #dcb67a;">📁 node_modules/</span><br>
├── <span style="color: #dcb67a;">📁 public/</span><br>
│   └── <span style="color: #9cdcfe;">index.html</span><br>
├── <span style="color: #dcb67a;">📁 src/</span><br>
│   ├── <span style="color: #9cdcfe;">App.jsx</span>         ← Componente principal<br>
│   ├── <span style="color: #9cdcfe;">App.css</span><br>
│   ├── <span style="color: #9cdcfe;">main.jsx</span>        ← Punto de entrada<br>
│   └── <span style="color: #9cdcfe;">index.css</span><br>
├── <span style="color: #9cdcfe;">package.json</span><br>
└── <span style="color: #9cdcfe;">vite.config.js</span>
</div>

---

## 2. JSX - HTML en JavaScript

JSX es una sintaxis que permite escribir HTML dentro de JavaScript.

```jsx
// JSX se ve como HTML pero es JavaScript
const elemento = <h1>Hola Mundo</h1>;

// Con JavaScript dentro (usar llaves {})
const nombre = "Juan";
const saludo = <h1>Hola, {nombre}</h1>;

// Expresiones JavaScript
const elemento = <p>2 + 2 = {2 + 2}</p>;

// Atributos (usar camelCase)
<div className="contenedor">...</div>  // class → className
<label htmlFor="email">...</label>   // for → htmlFor
<input onChange={...} />           // onchange → onChange

// Estilos inline (objeto)
<div style={{ color: 'red', fontSize: '20px' }}>...</div>
```

> [!WARNING] ⚠️ Reglas de JSX:
> *   Siempre devolver UN solo elemento padre (o usar `<Fragment>` o `<>`)
> *   Cerrar TODAS las etiquetas: `<img />`, `<br />`
> *   `class` → `className`
> *   `for` → `htmlFor`

```jsx
// ❌ Error: múltiples elementos sin padre
return (
  <h1>Título</h1>
  <p>Párrafo</p>
);

// ✅ Correcto: usar Fragment
return (
  <>
    <h1>Título</h1>
    <p>Párrafo</p>
  </>
);
```

---

## 3. Componentes

Los componentes son funciones que devuelven JSX. Son los bloques de construcción de React.

```jsx
// Componente funcional básico
function Saludo() {
  return <h1>¡Hola Mundo!</h1>;
}

// Componente con arrow function
const Saludo = () => {
  return <h1>¡Hola Mundo!</h1>;
};

// Usar el componente
function App() {
  return (
    <div>
      <Saludo />
      <Saludo />
      <Saludo />
    </div>
  );
}
```

> [!TIP] 💡 Convención:
> Los componentes siempre empiezan con **mayúscula**: `MiComponente`, no `miComponente`.

---

## 4. Props - Pasar datos a componentes

Las props son argumentos que pasas a los componentes (como parámetros de función).

```jsx
// Componente que recibe props
function Tarjeta({ titulo, descripcion, imagen }) {
  return (
    <div className="tarjeta">
      <img src={imagen} alt={titulo} />
      <h2>{titulo}</h2>
      <p>{descripcion}</p>
    </div>
  );
}

// Usando el componente con props
function App() {
  return (
    <div>
      <Tarjeta
        titulo="React"
        descripcion="Biblioteca de UI"
        imagen="/react.png"
      />
      <Tarjeta
        titulo="Vue"
        descripcion="Framework progresivo"
        imagen="/vue.png"
      />
    </div>
  );
}

// Props con valores por defecto
function Boton({ texto = "Click", color = "blue" }) {
  return <button style={{ background: color }}>{texto}</button>;
}

// Children prop (contenido entre etiquetas)
function Contenedor({ children }) {
  return <div className="contenedor">{children}</div>;
}

<Contenedor>
  <h1>Título</h1>
  <p>Este contenido se pasa como children</p>
</Contenedor>
```

> [!CAUTION] 🚨 Las props son de solo lectura:
> Nunca modifiques las props directamente. Son inmutables.

---

## 5. useState - Estado del componente

El estado permite que los componentes "recuerden" información y se actualicen cuando cambia.

```jsx
import { useState } from 'react';

function Contador() {
  // Declarar estado: [valor, funcionParaCambiar]
  const [contador, setContador] = useState(0);

  return (
    <div>
      <p>Contador: {contador}</p>
      <button onClick={() => setContador(contador + 1)}>
        Incrementar
      </button>
      <button onClick={() => setContador(0)}>
        Reiniciar
      </button>
    </div>
  );
}

// Estado con diferentes tipos
const [nombre, setNombre] = useState("");           // String
const [activo, setActivo] = useState(false);       // Boolean
const [items, setItems] = useState([]);           // Array
const [usuario, setUsuario] = useState({});       // Objeto
const [data, setData] = useState(null);           // Null inicial
```

**Actualizar estado correctamente:**
```jsx
// ❌ Incorrecto: Modificar directamente
contador = contador + 1;

// ✅ Correcto: Usar la función setter
setContador(contador + 1);

// ✅ Mejor: Usar función cuando dependes del valor anterior
setContador(prev => prev + 1);

// Actualizar arrays
setItems([...items, nuevoItem]);                // Agregar
setItems(items.filter(i => i.id !== id));       // Eliminar
setItems(items.map(i => i.id === id ? {...i, done: true} : i)); // Actualizar

// Actualizar objetos
setUsuario({ ...usuario, nombre: "Juan" });
```

---

## 6. Eventos

```jsx
function Formulario() {
  const [texto, setTexto] = useState("");

  // Evento click
  const handleClick = () => {
    console.log("¡Click!");
  };

  // Evento con parámetro
  const handleClickConParam = (mensaje) => {
    console.log(mensaje);
  };

  // Evento input (formularios)
  const handleChange = (e) => {
    setTexto(e.target.value);
  };

  // Evento submit
  const handleSubmit = (e) => {
    e.preventDefault();  // Prevenir recarga
    console.log("Enviado:", texto);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={texto}
        onChange={handleChange}
        placeholder="Escribe algo..."
      />
      <button type="submit">Enviar</button>
      <button type="button" onClick={handleClick}>Click</button>
      <button onClick={() => handleClickConParam("Hola")}>
        Con parámetro
      </button>
    </form>
  );
}
```

<table style="width: 100%; border-collapse: collapse; margin: 15px 0; font-size: 14px;">
  <thead style="background: #61dafb; color: #20232a;">
    <tr>
      <th style="border: 1px solid #ddd; padding: 10px;">Evento HTML</th>
      <th style="border: 1px solid #ddd; padding: 10px;">Evento React</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;">onclick</td>
      <td style="border: 1px solid #ddd; padding: 10px;">onClick</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;">onchange</td>
      <td style="border: 1px solid #ddd; padding: 10px;">onChange</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;">onsubmit</td>
      <td style="border: 1px solid #ddd; padding: 10px;">onSubmit</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;">onmouseover</td>
      <td style="border: 1px solid #ddd; padding: 10px;">onMouseOver</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;">onkeydown</td>
      <td style="border: 1px solid #ddd; padding: 10px;">onKeyDown</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;">onfocus</td>
      <td style="border: 1px solid #ddd; padding: 10px;">onFocus</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;">onblur</td>
      <td style="border: 1px solid #ddd; padding: 10px;">onBlur</td>
    </tr>
  </tbody>
</table>

---

## 7. Renderizado condicional

```jsx
function MiComponente({ isLoggedIn, user, items }) {
  
  // Con if/else
  if (isLoggedIn) {
    return <h1>Bienvenido, {user.name}</h1>;
  }
  return <h1>Por favor inicia sesión</h1>;
}

// Con operador ternario
return (
  <div>
    {isLoggedIn ? <span>Hola, {user}</span> : <span>Invitado</span>}
  </div>
);

// Con && (AND) - Mostrar solo si es true
return (
  <div>
    {isLoggedIn && <span>Bienvenido</span>}
    {items.length > 0 && <span>Tienes {items.length} items</span>}
  </div>
);

// Mostrar/ocultar con estado
const [mostrar, setMostrar] = useState(false);

return (
  <div>
    <button onClick={() => setMostrar(!mostrar)}>
      {mostrar ? 'Ocultar' : 'Mostrar'}
    </button>
    {mostrar && <p>Contenido visible</p>}
  </div>
);
```

---

## 8. Renderizar listas

```jsx
function ListaUsuarios() {
  const usuarios = [
    { id: 1, nombre: "Juan", edad: 25 },
    { id: 2, nombre: "María", edad: 30 },
    { id: 3, nombre: "Carlos", edad: 28 },
  ];

  return (
    <ul>
      {usuarios.map(usuario => (
        <li key={usuario.id}>
          {usuario.nombre} - {usuario.edad} años
        </li>
      ))}
    </ul>
  );
}

// Con componente separado
function UsuarioItem({ usuario }) {
  return (
    <li>{usuario.nombre} - {usuario.edad} años</li>
  );
}

function ListaUsuarios({ usuarios }) {
  return (
    <ul>
      {usuarios.map(usuario => (
        <UsuarioItem key={usuario.id} usuario={usuario} />
      ))}
    </ul>
  );
}
```

> [!CAUTION] 🚨 La prop `key` es obligatoria:
> Cada elemento de una lista necesita una `key` única. Usa IDs, nunca índices del array si la lista puede cambiar.

---

## 9. useEffect - Efectos secundarios

useEffect permite ejecutar código después del renderizado (fetch, suscripciones, timers, etc.).

```jsx
import { useState, useEffect } from 'react';

function MiComponente() {
  const [datos, setDatos] = useState([]);
  const [contador, setContador] = useState(0);

  // Se ejecuta en CADA renderizado
  useEffect(() => {
    console.log("Componente renderizado");
  });

  // Se ejecuta SOLO al montar (array vacío)
  useEffect(() => {
    console.log("Componente montado");
    fetchDatos();
  }, []);  // ← Array de dependencias vacío

  // Se ejecuta cuando cambia 'contador'
  useEffect(() => {
    console.log("Contador cambió:", contador);
  }, [contador]);  // ← Dependencia específica

  // Con cleanup (limpieza al desmontar)
  useEffect(() => {
    const timer = setInterval(() => {
      console.log("Tick");
    }, 1000);

    // Función de limpieza
    return () => {
      clearInterval(timer);
      console.log("Limpieza ejecutada");
    };
  }, []);

  // Fetch de datos
  const fetchDatos = async () => {
    const response = await fetch('https://api.ejemplo.com/datos');
    const data = await response.json();
    setDatos(data);
  };

  return <div>...</div>;
}
```

<table style="width: 100%; border-collapse: collapse; margin: 15px 0; font-size: 14px;">
  <thead style="background: #61dafb; color: #20232a;">
    <tr>
      <th style="border: 1px solid #ddd; padding: 10px;">Dependencias</th>
      <th style="border: 1px solid #ddd; padding: 10px;">¿Cuándo se ejecuta?</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;">Sin array</td>
      <td style="border: 1px solid #ddd; padding: 10px;">En cada renderizado</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;"><code>[]</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">Solo al montar (una vez)</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>[valor]</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">Al montar + cuando cambia valor</td>
    </tr>
  </tbody>
</table>

---

## 10. Otros Hooks importantes

<div style="background: linear-gradient(135deg, #e8f4fd, #d1ecf1); border: 1px solid #61dafb; border-radius: 10px; padding: 15px; margin: 10px 0;">
  <h4 style="color: #0c5460; margin-bottom: 8px;">useRef - Referencias a elementos DOM</h4>
  <pre style="margin: 10px 0; background: #1e1e1e; padding: 10px; border-radius: 5px;"><code style="color: #d4d4d4;">import { useRef } from 'react';

function InputFocus() {
  const inputRef = useRef(null);

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <>
      &lt;input ref={inputRef} /&gt;
      &lt;button onClick={focusInput}&gt;Enfocar&lt;/button&gt;
    </>
  );
}</code></pre>
</div>

<div style="background: linear-gradient(135deg, #e8f4fd, #d1ecf1); border: 1px solid #61dafb; border-radius: 10px; padding: 15px; margin: 10px 0;">
  <h4 style="color: #0c5460; margin-bottom: 8px;">useContext - Estado global sin props drilling</h4>
  <pre style="margin: 10px 0; background: #1e1e1e; padding: 10px; border-radius: 5px;"><code style="color: #d4d4d4;">import { createContext, useContext } from 'react';

// Crear contexto
const TemaContext = createContext('light');

// Proveer contexto
function App() {
  return (
    &lt;TemaContext.Provider value="dark"&gt;
      &lt;MiComponente /&gt;
    &lt;/TemaContext.Provider&gt;
  );
}

// Consumir contexto
function MiComponente() {
  const tema = useContext(TemaContext);
  return &lt;div&gt;Tema actual: {tema}&lt;/div&gt;;
}</code></pre>
</div>

<div style="background: linear-gradient(135deg, #e8f4fd, #d1ecf1); border: 1px solid #61dafb; border-radius: 10px; padding: 15px; margin: 10px 0;">
  <h4 style="color: #0c5460; margin-bottom: 8px;">useMemo / useCallback - Optimización</h4>
  <pre style="margin: 10px 0; background: #1e1e1e; padding: 10px; border-radius: 5px;"><code style="color: #d4d4d4;">// useMemo: Memoriza un VALOR calculado
const valorCaro = useMemo(() => {
  return calculoPesado(datos);
}, [datos]);

// useCallback: Memoriza una FUNCIÓN
const handleClick = useCallback(() => {
  console.log(contador);
}, [contador]);</code></pre>
</div>

---

## 11. Custom Hooks

Puedes crear tus propios hooks para reutilizar lógica.

```jsx
// Hook personalizado para fetch
function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch(url);
        const json = await response.json();
        setData(json);
      } catch (err) {
        setError(err);
      } finally {
        setLoading(false);
      }
    };
    fetchData();
  }, [url]);

  return { data, loading, error };
}

// Usar el hook
function Usuarios() {
  const { data, loading, error } = useFetch('/api/usuarios');

  if (loading) return <p>Cargando...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return <ul>{data.map(u => <li key={u.id}>{u.name}</li>)}</ul>;
}
```

> [!TIP] 💡 Regla:
> Los custom hooks siempre empiezan con "use": `useFetch`, `useLocalStorage`, `useForm`.

---

## 12. React Router - Navegación

```jsx
// Instalar: npm install react-router-dom

import { BrowserRouter, Routes, Route, Link, useParams, useNavigate } from 'react-router-dom';

// Configurar rutas
function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Inicio</Link>
        <Link to="/about">Acerca</Link>
        <Link to="/usuarios">Usuarios</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/usuarios" element={<Usuarios />} />
        <Route path="/usuarios/:id" element={<Usuario />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </BrowserRouter>
  );
}

// Obtener parámetros de URL
function Usuario() {
  const { id } = useParams();
  return <h1>Usuario ID: {id}</h1>;
}

// Navegación programática
function MiComponente() {
  const navigate = useNavigate();

  const irAHome = () => {
    navigate('/');
  };

  return <button onClick={irAHome}>Ir a Home</button>;
}
```

---

## 13. Estilos en React

```jsx
// 1. CSS normal (importar archivo)
import './MiComponente.css';

function MiComponente() {
  return <div className="mi-clase">...</div>;
}

// 2. CSS Modules (evita conflictos)
import styles from './MiComponente.module.css';

function MiComponente() {
  return <div className={styles.contenedor}>...</div>;
}

// 3. Estilos inline
const estilos = {
  backgroundColor: '#f0f0f0',
  padding: '20px',
  borderRadius: '8px'
};

<div style={estilos}>...</div>
<div style={{ color: 'red', fontSize: '20px' }}>...</div>

// 4. Clases condicionales
<div className={`btn ${activo ? 'btn-activo' : ''}`}>...</div>
```

> [!INFO] ℹ️ Librerías de estilos populares:
> *   **Tailwind CSS** - Clases utilitarias
> *   **Styled Components** - CSS-in-JS
> *   **Material UI** - Componentes prediseñados
> *   **Chakra UI** - Componentes accesibles

---

## ✨ Buenas prácticas

<table style="width: 100%; border-collapse: collapse; margin: 15px 0; font-size: 14px;">
  <thead style="background: #61dafb; color: #20232a;">
    <tr>
      <th style="border: 1px solid #ddd; padding: 10px;">✅ Hacer</th>
      <th style="border: 1px solid #ddd; padding: 10px;">❌ Evitar</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;">Componentes pequeños y enfocados</td>
      <td style="border: 1px solid #ddd; padding: 10px;">Componentes gigantes con mucha lógica</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;">Usar <code>const</code> para estado</td>
      <td style="border: 1px solid #ddd; padding: 10px;">Modificar estado directamente</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;">Keys únicas en listas (IDs)</td>
      <td style="border: 1px solid #ddd; padding: 10px;">Usar índices como key</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;">Mover lógica a custom hooks</td>
      <td style="border: 1px solid #ddd; padding: 10px;">Repetir lógica en componentes</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;">Nombrar componentes con mayúscula</td>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>miComponente</code></td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;">useEffect con dependencias correctas</td>
      <td style="border: 1px solid #ddd; padding: 10px;">Ignorar advertencias de dependencias</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;">Destructuring de props</td>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>props.nombre</code> repetidamente</td>
    </tr>
  </tbody>
</table>

```jsx
// ✅ Estructura de carpetas recomendada
src/
├── components/
│   ├── Button/
│   │   ├── Button.jsx
│   │   ├── Button.module.css
│   │   └── index.js
│   └── Card/
├── hooks/
│   └── useFetch.js
├── pages/
│   ├── Home.jsx
│   └── About.jsx
├── context/
│   └── AuthContext.jsx
├── services/
│   └── api.js
└── utils/
    └── helpers.js
```

---

## 📋 Referencia rápida de Hooks

<table style="width: 100%; border-collapse: collapse; margin: 15px 0; font-size: 14px;">
  <thead style="background: #61dafb; color: #20232a;">
    <tr>
      <th style="border: 1px solid #ddd; padding: 10px;">Hook</th>
      <th style="border: 1px solid #ddd; padding: 10px;">Uso</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>useState</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">Manejar estado local del componente</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;"><code>useEffect</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">Efectos secundarios (fetch, suscripciones)</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>useContext</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">Consumir contexto (estado global)</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;"><code>useRef</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">Referencias a DOM, valores que persisten</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>useMemo</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">Memorizar valores costosos</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;"><code>useCallback</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">Memorizar funciones</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>useReducer</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">Estado complejo (alternativa a useState)</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="border: 1px solid #ddd; padding: 10px;"><code>useParams</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">Obtener parámetros de URL (Router)</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ddd; padding: 10px;"><code>useNavigate</code></td>
      <td style="border: 1px solid #ddd; padding: 10px;">Navegación programática (Router)</td>
    </tr>
  </tbody>
</table>

---

## ✓ Checklist de aprendizaje

- [ ] Sé crear un proyecto con Vite o CRA
- [ ] Entiendo JSX y sus reglas
- [ ] Puedo crear componentes funcionales
- [ ] Sé pasar y recibir props
- [ ] Domino useState para manejar estado
- [ ] Sé manejar eventos (onClick, onChange, onSubmit)
- [ ] Puedo hacer renderizado condicional
- [ ] Sé renderizar listas con map y key
- [ ] Entiendo useEffect y sus dependencias
- [ ] Conozco useRef y useContext
- [ ] Puedo crear custom hooks
- [ ] Sé usar React Router para navegación
- [ ] Conozco diferentes formas de aplicar estilos
