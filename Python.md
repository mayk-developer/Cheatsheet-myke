# Cheat Sheet: Python Moderno (3.10+)

Guía exhaustiva y moderna para el desarrollo profesional en Python.

## Fundamentos y Tipos
**Tipos Básicos & Conversiones**
```python
x: int = 10
y: float = 3.14
s: str = "text"
is_valid: bool = True

# Conversión explícita
n = int("10")
s = str(3.14)
b = bool(0) # False (0, "", [], None son falsy)
```

**Operadores Clave**
- `//` División entera (floor division)
- `**` Exponenciación
- `is` Identidad de objeto (vs `==` igualdad de valor)

## Estructuras de Datos Avanzadas

### Listas (Lists)
Secuencias mutables.
```python
nums = [0, 1, 2, 3, 4, 5]

# Slicing [start:stop:step]
last = nums[-1]         # 5
sub = nums[1:4]         # [1, 2, 3]
rev = nums[::-1]        # Inversión rápida [5, 4, ..., 0]

# Métodos útiles
nums.append(6)          # Agrega al final
nums.extend([7, 8])     # Une otra lista
nums.insert(0, -1)      # Inserta en índex
item = nums.pop()       # Remueve y retorna el último
nums.sort(reverse=True) # Ordena in-place
```

### Diccionarios (Dicts)
Mapas clave-valor mutables.
```python
# Creación
user = {"id": 1, "name": "Ana"}
empty = {}

# Acceso seguro
name = user.get("name", "Anon") # Default si no existe

# Operaciones Modernas (3.9+)
defaults = {"theme": "dark", "lang": "en"}
settings = defaults | {"lang": "es"} # Merge (crea nuevo)
defaults |= {"lang": "fr"}           # Update in-place

# Iteración
for k, v in user.items():
    print(f"{k}: {v}")
```

### Sets (Conjuntos)
Colecciones desordenadas de elementos únicos. Útiles para eliminar duplicados y lógica de conjuntos.
```python
a = {1, 2, 3}
b = {3, 4, 5}

union = a | b          # {1, 2, 3, 4, 5}
inter = a & b          # {3}
diff = a - b           # {1, 2}
sym_diff = a ^ b       # {1, 2, 4, 5} (elementos en a o b pero no ambos)
```

### Tuplas & NamedTuple
Inmutables. `NamedTuple` da nombres a los campos.
```python
point = (10, 20)
x, y = point # Unpacking

from collections import namedtuple
Point = namedtuple("Point", ["x", "y"])
p = Point(10, 20)
print(p.x) # 10
```

### Comprehensions
La forma "Pythonic" de crear colecciones.
```python
# Lists: Cuadrados de pares
sq = [x**2 for x in range(10) if x % 2 == 0]

# Dicts: ID -> Usuario
users_map = {u.id: u for u in users}

# Sets: Nombres únicos
names = {u.name for u in users}

# Generators: Ahorran memoria (lazy evaluation)
gen = (x**2 for x in range(10000))
```

## Control de Flujo Moderno

### Pattern Matching (`match` / `case`) (3.10+)
Un "switch" estructural muy poderoso.
```python
data = {"status": 200, "payload": "OK"}

match data:
    case {"status": 200, "payload": result}:
        print(f"Éxito: {result}")
    case {"status": 404}:
        print("No encontrado")
    case {"status": error_code}: # Captura valor
        print(f"Error: {error_code}")
    case _: # Default
        print("Desconocido")
```

### Operador Walrus (`:=`) (3.8+)
Asignación dentro de una expresión.
```python
if (n := len(items)) > 10:
    print(f"Demasiados items: {n}")
    
while (line := file.readline()):
    print(line)
```

## Funciones

### Argumentos
```python
def func(a, b=1, *args, **kwargs):
    # a: posicional
    # b: keyword con default
    # args: tupla de extras posicionales
    # kwargs: dict de extras nombrados
    pass

# Forzar keyword-only (después del *)
def connect(*, timeout: int): ...
connect(timeout=5) # OK
# connect(5) # Error
```

### Type Hinting (Tipado Estático)
Esencial para proyectos grandes.
```python
from typing import List, Optional, Callable, Union

# Sintaxis moderna (3.10+) usa | para Union
def process(items: List[int]) -> int | None:
    if not items:
        return None
    return sum(items)

# Aliases
UserId = int
def get_user(uid: UserId) -> str: ...
```

### Decoradores
Modifican comportamiento de funciones.
```python
from functools import wraps

def log_exec(func):
    @wraps(func) # Preserva metadata original
    def wrapper(*args, **kwargs):
        print(f"Llamando a {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@log_exec
def add(a, b): return a + b
```

## Programación Orientada a Objetos (OOP)

### Dataclasses (3.7+)
La forma moderna de crear clases de datos.
```python
from dataclasses import dataclass, field

@dataclass
class Product:
    name: str
    price: float
    tags: list[str] = field(default_factory=list) # Mutable default seguro
    active: bool = True

    def discount_price(self, pct: float) -> float:
        return self.price * (1 - pct)
```

### Clases y Herencia
```python
class Animal:
    def speak(self): pass

class Dog(Animal):
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        super().speak() # Llama al padre
        return "Woof"

# Propiedades
class Circle:
    def __init__(self, r): self._r = r
    
    @property
    def radius(self): return self._r
    
    @radius.setter
    def radius(self, val): 
        if val < 0: raise ValueError 
        self._r = val
```

## Manejo de Errores y Archivos

### Try / Except
```python
try:
    result = 10 / 0
except ZeroDivisionError as e:
    print(f"Error: {e}")
except (ValueError, TypeError):
    print("Error de tipo o valor")
else:
    print("Todo salió bien") # Si no hubo excepción
finally:
    print("Siempre me ejecuto") # Cleanup
```

### Archivos con Context Managers
Siempre usa `with`.
```python
from pathlib import Path

# Pathlib (Moderno)
path = Path("data.json")

# Escribir
path.write_text('{"id": 1}')

# Leer
content = path.read_text()

# Manejo tradicional línea a línea
with open("large_log.txt", "r", encoding="utf-8") as f:
    for line in f:
        process(line)
```

## Concurrencia (AsyncIO)

Programación asíncrona para I/O (Web, DBs).
```python
import asyncio

async def fetch_data(id: int):
    print(f"Iniciando {id}")
    await asyncio.sleep(1) # Simula espera I/O
    print(f"Fin {id}")
    return id * 2

async def main():
    # Ejecuta concurrentemente
    results = await asyncio.gather(fetch_data(1), fetch_data(2))
    print(results) # [2, 4]

if __name__ == "__main__":
    asyncio.run(main())
```

## Librerías Estándar Esenciales

- **`datetime`**: Manejo de fechas.
  ```python
  from datetime import datetime, timezone, timedelta
  now_utc = datetime.now(timezone.utc)
  tomorrow = now_utc + timedelta(days=1)
  ```
- **`json`**: Serialización.
  ```python
  import json
  data_str = json.dumps(my_dict, indent=2)
  my_dict = json.loads(data_str)
  ```
- **`collections`**: Estructuras extra.
  ```python
  from collections import Counter, defaultdict
  counts = Counter(["a", "b", "a"]) # {'a': 2, 'b': 1}
  groups = defaultdict(list) # Default value vacío automático
  ```
- **`itertools`**: Iteradores eficientes.
  ```python
  import itertools
  flat = list(itertools.chain([1,2], [3,4])) # Flatten
  ```

## Tooling y Entornos

### F-Strings (Formato)
```python
value = 123.4567
print(f"Dinero: ${value:.2f}")  # $123.46
print(f"Debug: {value=}")       # Debug: value=123.4567
```

### Entornos Virtuales (Venv / Uv)
Siempre aísla dependencias.
```bash
# Crear (estándar)
python3 -m venv .venv
source .venv/bin/activate

# Uv (Recomendado, mucho más rápido)
uv venv
uv pip install requests
```

### Testing (Pytest)
No uses `unittest` antiguo si puedes evitarlo.
```python
# test_app.py
def test_add():
    assert add(2, 3) == 5
```
Ejecutar con `pytest`.
