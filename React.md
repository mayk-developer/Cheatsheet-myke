# Cheat Sheet: React Moderno (Hooks & Patrones)

Guía rápida de React enfocada en Componentes Funcionales, Hooks y patrones modernos.

## Anatomía de un Componente

```jsx
import { useState } from 'react';

// Componente Funcional (siempre empieza con Mayúscula)
export default function MiComponente({ titulo, initialCount = 0 }) {
  // Lógica y Hooks aquí
  const [count, setCount] = useState(initialCount);

  // Retorno de JSX
  return (
    <article className="card">
      <h1>{titulo}</h1>
      <p>Contador: {count}</p>
      <button onClick={() => setCount(count + 1)}>Sumar</button>
    </article>
  );
}
```

## Hooks Esenciales

**useState (Estado Local)**
```jsx
const [user, setUser] = useState(null);
const [isLoading, setIsLoading] = useState(true);

// Actualización basada en estado previo
setUser(prev => ({ ...prev, name: 'Nuevo' }));
```

**useEffect (Efectos Secundarios)**
Reemplaza `componentDidMount`, `componentDidUpdate`, `componentWillUnmount`.

```jsx
useEffect(() => {
  // Código que se ejecuta al montar y cuando cambian las dependencias
  const id = setInterval(() => console.log('Tick'), 1000);

  // Cleanup function (desmontaje)
  return () => clearInterval(id);
}, [dependencia1]); // Array de dependencias
```
*Tip: `[]` vacío ejecuta solo al montar. Sin array ejecuta en cada render (cuidado).*

**useRef (Referencias Mutables / DOM)**
No provoca re-renders cuando cambia su valor.
```jsx
const inputRef = useRef(null);
const countRef = useRef(0);

const focusInput = () => {
  inputRef.current.focus(); // Acceso directo al DOM
  countRef.current += 1;    // Variable mutable persistente
};
```

**useContext (Estado Global Simple)**
Evita el "prop drilling".
```jsx
// 1. Crear Contexto
const ThemeContext = createContext('light');

// 2. Proveer
<ThemeContext.Provider value="dark">
  <App />
</ThemeContext.Provider>

// 3. Consumir
const theme = useContext(ThemeContext);
```

**useReducer (Estado Complejo)**
Similar a Redux pero local.
```jsx
function reducer(state, action) {
  switch (action.type) {
    case 'increment': return { count: state.count + 1 };
    default: return state;
  }
}

const [state, dispatch] = useReducer(reducer, { count: 0 });
dispatch({ type: 'increment' });
```

## Rendimiento (Memoization)

Úsalos solo si hay problemas de rendimiento reales.

**useMemo (Cachear valores calculados)**
```jsx
// Solo recalcula si `items` cambia
const total = useMemo(() => items.reduce((a, b) => a + b, 0), [items]);
```

**useCallback (Cachear funciones)**
Para evitar que funciones se re-creen en cada render (útil al pasar props a hijos).
```jsx
const handleClick = useCallback(() => {
  doSomething(id);
}, [id]);
```

## Custom Hooks (Reutilizar Lógica)

El superpoder de React. Extrae lógica de estado para compartirla.

```jsx
function useVentanaSize() {
  const [size, setSize] = useState(window.innerWidth);

  useEffect(() => {
    const handleResize = () => setSize(window.innerWidth);
    window.addEventListener('resize', handleResize);
    return () => window.removeEventListener('resize', handleResize);
  }, []);

  return size;
}

// Uso
const width = useVentanaSize();
```

## Patrones Comunes

**Renderizado Condicional**
```jsx
{isLoggedIn ? <AdminPanel /> : <LoginForm />}
{hasError && <ErrorMessage />}
```

**Listas y Keys**
Siempre usa una `key` única y estable (evita índices si la lista cambia).
```jsx
<ul>
  {productos.map((p) => (
    <li key={p.id}>{p.nombre}</li>
  ))}
</ul>
```

**Reglas de los Hooks**
1. Solo llamar en el nivel superior (no dentro de loops, condiciones o funciones anidadas).
2. Solo llamar desde componentes de React o Custom Hooks.

## Ecosistema Moderno (Recomendaciones)

No reinventes la rueda.
- **Enrutamiento**: `React Router` (SPA) o el enrutador de `Next.js`.
- **Data Fetching**: `TanStack Query` (React Query) o `SWR`. *Evita usar useEffect para fetch simple.*
- **Formularios**: `React Hook Form` (rendimiento y validación fácil).
- **Estado Global**: `Zustand` (minimalista) o `Redux Toolkit` (complejo/enterprise).
- **Estilos**: `Tailwind CSS`, `Styled Components` o `CSS Modules`.
