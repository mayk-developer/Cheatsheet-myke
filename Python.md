
<div style="background: linear-gradient(135deg, #3776ab, #ffd43b); padding: 15px; border-radius: 10px; text-align: center; margin-bottom: 20px;">
  <h1 style="color: white; margin: 0;">🐍 Guía Completa de Python</h1>
  <p style="color: #f0f0f0; margin: 5px 0 0 0;">El lenguaje más versátil - Desde cero hasta avanzado</p>
</div>

<!-- QUÉ ES PYTHON -->
## 💡 ¿Qué es Python?
Python es un lenguaje de programación versátil, fácil de aprender y muy potente. Es usado en web, ciencia de datos, IA, automatización y más.

> [!INFO] ℹ️ ¿Dónde se usa Python?
> *   **Web**: Django, Flask, FastAPI
> *   **Data Science**: Pandas, NumPy, Matplotlib
> *   **Machine Learning**: TensorFlow, PyTorch, Scikit-learn
> *   **Automatización**: Scripts, web scraping
> *   **DevOps**: Ansible, automatización de infraestructura

**Tu primer código:**
```python
# Esto es un comentario
print("¡Hola, Python!")

# Variables
nombre = "Juan"
edad = 25
print(f"Hola, {nombre}. Tienes {edad} años.")
```

> [!TIP] 💡 Características de Python
> *   Sintaxis limpia y legible
> *   No usa llaves `{}` ni punto y coma `;`
> *   Usa indentación (espacios) para definir bloques
> *   Tipado dinámico (no declaras tipos)

---

<!-- INSTALACIÓN -->
## 1️⃣ Instalación

| Sistema | Cómo instalar |
| :--- | :--- |
| **Windows** | Descarga de `python.org` → Marcar "Add to PATH" |
| **macOS** | `brew install python` |
| **Linux** | `sudo apt install python3` |

```python
# Verificar instalación
python --version
# Python 3.12.0

# Ejecutar archivo
python mi_archivo.py

# Modo interactivo
python
>>> print("Hola")
Hola
```

---

<!-- VARIABLES Y TIPOS -->
## 2️⃣ Variables y tipos de datos

```python
# Strings (texto)
nombre = "Juan"
apellido = 'Pérez'
mensaje = """Texto
multilínea"""

# Números
entero = 25
decimal = 19.99
negativo = -10

# Booleanos
activo = True
eliminado = False

# None (valor nulo)
vacio = None

# Listas (mutables)
frutas = ["manzana", "banana", "naranja"]

# Tuplas (inmutables)
coordenadas = (10, 20)

# Diccionarios (clave: valor)
persona = {
    "nombre": "Juan",
    "edad": 25,
    "ciudad": "Lima"
}

# Sets (valores únicos)
numeros = {1, 2, 3, 3}  # → {1, 2, 3}

# Verificar tipo
type(nombre)   # <class 'str'>
type(edad)     # <class 'int'>
type(frutas)   # <class 'list'>
```

| Tipo | Ejemplo | Descripción |
| :--- | :--- | :--- |
| `str` | `"Hola"` | Texto |
| `int` | `42` | Entero |
| `float` | `3.14` | Decimal |
| `bool` | `True` / `False` | Booleano |
| `list` | `[1, 2, 3]` | Lista mutable |
| `tuple` | `(1, 2, 3)` | Tupla inmutable |
| `dict` | `{"a": 1}` | Diccionario |
| `set` | `{1, 2, 3}` | Conjunto único |

---

<!-- OPERADORES -->
## 3️⃣ Operadores

```python
# Aritméticos
5 + 3     # 8   Suma
5 - 3     # 2   Resta
5 * 3     # 15  Multiplicación
5 / 3     # 1.666... División
5 // 3    # 1   División entera
5 % 3     # 2   Módulo (resto)
5 ** 3    # 125 Potencia

# Comparación
5 == 5    # True   Igual
5 != 3    # True   Diferente
5 > 3     # True   Mayor
5 >= 5    # True   Mayor o igual
5 < 3     # False  Menor
5 <= 5    # True   Menor o igual

# Lógicos
True and True   # True  (ambos)
True or False   # True  (al menos uno)
not True        # False (negación)

# Asignación
x = 10
x += 5    # x = x + 5  → 15
x -= 3    # x = x - 3  → 12
x *= 2    # x = x * 2  → 24

# Pertenencia
"a" in "hola"      # True
3 in [1, 2, 3]     # True
"x" not in "hola"  # True

# Identidad
a is b       # ¿Mismo objeto?
a is not b   # ¿Diferente objeto?
```

---

<!-- STRINGS -->
## 4️⃣ Strings (cadenas de texto)

```python
texto = "Hola Mundo"

# Métodos
texto.upper()           # "HOLA MUNDO"
texto.lower()           # "hola mundo"
texto.capitalize()      # "Hola mundo"
texto.title()           # "Hola Mundo"
texto.strip()           # Quita espacios
texto.replace("Mundo", "Python")  # "Hola Python"
texto.split(" ")        # ["Hola", "Mundo"]
"-".join(["a", "b"])    # "a-b"
texto.startswith("Hola") # True
texto.endswith("do")    # True
texto.find("Mundo")     # 5 (posición)
len(texto)              # 10 (longitud)

# Indexación y slicing
texto[0]       # "H" (primer carácter)
texto[-1]      # "o" (último)
texto[0:4]     # "Hola" (del 0 al 3)
texto[5:]      # "Mundo" (del 5 al final)
texto[::-1]    # "odnuM aloH" (invertir)

# f-strings (formateo moderno) ✅
nombre = "Juan"
edad = 25
print(f"Hola, {nombre}. Tienes {edad} años.")
print(f"En 5 años tendrás {edad + 5} años.")
print(f"Precio: {19.99:.2f}")  # "19.99" (2 decimales)
```

---

<!-- CONDICIONALES -->
## 5️⃣ Condicionales

```python
edad = 18

# if - elif - else
if edad >= 18:
    print("Eres mayor de edad")
elif edad >= 13:
    print("Eres adolescente")
else:
    print("Eres niño")

# Operador ternario
mensaje = "Mayor" if edad >= 18 else "Menor"

# Múltiples condiciones
if edad >= 18 and edad < 65:
    print("Adulto en edad laboral")

if edad < 18 or edad >= 65:
    print("Descuento especial")

# Verificar None
if variable is None:
    print("Sin valor")

# Verificar si está vacío
lista = []
if not lista:  # Lista vacía es False
    print("Lista vacía")

# Match (Python 3.10+)
match comando:
    case "inicio":
        print("Iniciando...")
    case "salir":
        print("Saliendo...")
    case _:
        print("Comando desconocido")
```

> [!WARNING] ⚠️ Importante
> Python usa **indentación** (4 espacios) para definir bloques de código. ¡No mezcles tabs y espacios!

---

<!-- LISTAS -->
## 6️⃣ Listas

```python
# Crear lista
frutas = ["manzana", "banana", "naranja"]
numeros = [1, 2, 3, 4, 5]
mixta = [1, "hola", True, 3.14]

# Acceder
frutas[0]       # "manzana"
frutas[-1]      # "naranja" (último)
frutas[0:2]     # ["manzana", "banana"]

# Modificar
frutas[0] = "pera"

# Métodos
frutas.append("uva")      # Agregar al final
frutas.insert(0, "kiwi")  # Insertar en posición
frutas.extend(["a", "b"]) # Agregar múltiples
frutas.remove("banana")   # Eliminar por valor
frutas.pop()              # Eliminar último
frutas.pop(0)             # Eliminar por índice
frutas.clear()            # Vaciar lista
frutas.sort()             # Ordenar
frutas.reverse()          # Invertir
frutas.index("banana")    # Posición
frutas.count("banana")    # Contar ocurrencias
len(frutas)               # Longitud

# Copiar lista
copia = frutas.copy()
copia = frutas[:]

# List comprehension ✅
cuadrados = [x**2 for x in range(5)]  # [0, 1, 4, 9, 16]
pares = [x for x in range(10) if x % 2 == 0]  # [0, 2, 4, 6, 8]
```

---

<!-- DICCIONARIOS -->
## 7️⃣ Diccionarios

```python
# Crear diccionario
persona = {
    "nombre": "Juan",
    "edad": 25,
    "ciudad": "Lima",
    "hobbies": ["leer", "programar"]
}

# Acceder
persona["nombre"]          # "Juan"
persona.get("nombre")      # "Juan"
persona.get("pais", "N/A") # "N/A" (valor por defecto)

# Modificar
persona["edad"] = 26       # Actualizar
persona["email"] = "j@mail.com"  # Agregar nuevo

# Eliminar
del persona["ciudad"]      # Eliminar clave
persona.pop("edad")        # Eliminar y retornar

# Métodos
persona.keys()             # Todas las claves
persona.values()           # Todos los valores
persona.items()            # Pares (clave, valor)
persona.update({"pais": "Perú"})  # Actualizar múltiples

# Verificar si existe clave
if "nombre" in persona:
    print("Existe")

# Iterar
for clave, valor in persona.items():
    print(f"{clave}: {valor}")

# Dict comprehension
cuadrados = {x: x**2 for x in range(5)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

---

<!-- BUCLES -->
## 8️⃣ Bucles

```python
# for - iterar sobre secuencia
frutas = ["manzana", "banana", "naranja"]
for fruta in frutas:
    print(fruta)

# for con range
for i in range(5):       # 0, 1, 2, 3, 4
    print(i)

for i in range(1, 6):    # 1, 2, 3, 4, 5
    print(i)

for i in range(0, 10, 2): # 0, 2, 4, 6, 8 (paso 2)
    print(i)

# for con enumerate (índice + valor)
for i, fruta in enumerate(frutas):
    print(f"{i}: {fruta}")

# while
contador = 0
while contador < 5:
    print(contador)
    contador += 1

# break y continue
for i in range(10):
    if i == 3:
        continue  # Salta a la siguiente iteración
    if i == 7:
        break     # Sale del bucle
    print(i)

# else en bucles (se ejecuta si no hay break)
for i in range(5):
    print(i)
else:
    print("Bucle completado")
```

---

<!-- FUNCIONES -->
## 9️⃣ Funciones

```python
# Función básica
def saludar():
    print("¡Hola!")

saludar()  # ¡Hola!

# Con parámetros
def saludar(nombre):
    print(f"¡Hola, {nombre}!")

saludar("Juan")  # ¡Hola, Juan!

# Con return
def sumar(a, b):
    return a + b

resultado = sumar(3, 5)  # 8

# Parámetros por defecto
def saludar(nombre="Invitado"):
    print(f"¡Hola, {nombre}!")

saludar()         # ¡Hola, Invitado!
saludar("Ana")   # ¡Hola, Ana!

# Argumentos con nombre (kwargs)
def crear_usuario(nombre, edad, ciudad="Lima"):
    return {"nombre": nombre, "edad": edad, "ciudad": ciudad}

crear_usuario(nombre="Juan", edad=25)
crear_usuario("Juan", 25, ciudad="Bogotá")

# *args (múltiples argumentos)
def sumar_todos(*numeros):
    return sum(numeros)

sumar_todos(1, 2, 3, 4)  # 10

# **kwargs (argumentos con nombre variables)
def imprimir_info(**datos):
    for clave, valor in datos.items():
        print(f"{clave}: {valor}")

imprimir_info(nombre="Juan", edad=25)

# Lambda (función anónima)
doble = lambda x: x * 2
doble(5)  # 10

suma = lambda a, b: a + b
suma(3, 5)  # 8

# Funciones útiles con lambda
numeros = [1, 2, 3, 4, 5]
dobles = list(map(lambda x: x * 2, numeros))      # [2, 4, 6, 8, 10]
pares = list(filter(lambda x: x % 2 == 0, numeros)) # [2, 4]
```

---

<!-- CLASES -->
## 🔟 Clases (POO)

```python
class Persona:
    # Constructor
    def __init__(self, nombre, edad):
        self.nombre = nombre    # Atributo público
        self.edad = edad
        self._privado = "valor"  # Convención: privado

    # Método
    def saludar(self):
        return f"Hola, soy {self.nombre}"

    # Método con parámetros
    def cumplir_años(self):
        self.edad += 1

    # Representación string
    def __str__(self):
        return f"Persona({self.nombre}, {self.edad})"

# Crear instancia
juan = Persona("Juan", 25)
print(juan.nombre)     # Juan
print(juan.saludar()) # Hola, soy Juan

# Herencia
class Estudiante(Persona):
    def __init__(self, nombre, edad, carrera):
        super().__init__(nombre, edad)  # Llamar al padre
        self.carrera = carrera

    def estudiar(self):
        return f"{self.nombre} estudia {self.carrera}"

ana = Estudiante("Ana", 20, "Ingeniería")
print(ana.saludar())   # Hola, soy Ana (heredado)
print(ana.estudiar())  # Ana estudia Ingeniería
```

---

<!-- MANEJO DE ERRORES -->
## 1️⃣1️⃣ Manejo de errores

```python
try:
    resultado = 10 / 0
except ZeroDivisionError:
    print("No se puede dividir por cero")
except Exception as e:
    print(f"Error: {e}")
else:
    print("Todo bien")  # Si no hay error
finally:
    print("Siempre se ejecuta")

# Lanzar excepciones
def dividir(a, b):
    if b == 0:
        raise ValueError("No se puede dividir por cero")
    return a / b

# Excepciones comunes
# ValueError     - Valor incorrecto
# TypeError      - Tipo incorrecto
# KeyError       - Clave no existe en dict
# IndexError     - Índice fuera de rango
# FileNotFoundError - Archivo no existe
```

---

<!-- ARCHIVOS -->
## 1️⃣2️⃣ Manejo de archivos

```python
# Escribir archivo
with open("archivo.txt", "w") as f:
    f.write("Hola Mundo\n")
    f.write("Segunda línea")

# Leer archivo completo
with open("archivo.txt", "r") as f:
    contenido = f.read()

# Leer línea por línea
with open("archivo.txt", "r") as f:
    for linea in f:
        print(linea.strip())

# Leer todas las líneas como lista
with open("archivo.txt", "r") as f:
    lineas = f.readlines()

# Agregar al final (append)
with open("archivo.txt", "a") as f:
    f.write("\nNueva línea")

# Modos: "r" (leer), "w" (escribir), "a" (agregar), "rb" (binario)

# JSON
import json

datos = {"nombre": "Juan", "edad": 25}

# Guardar JSON
with open("datos.json", "w") as f:
    json.dump(datos, f, indent=2)

# Leer JSON
with open("datos.json", "r") as f:
    datos = json.load(f)
```

---

<!-- MÓDULOS -->
## 1️⃣3️⃣ Módulos e importaciones

```python
# Importar módulo completo
import math
print(math.sqrt(16))  # 4.0

# Importar con alias
import math as m
print(m.pi)  # 3.14159...

# Importar funciones específicas
from math import sqrt, pi
print(sqrt(16))  # 4.0

# Importar todo (no recomendado)
from math import *

# Módulos útiles de la biblioteca estándar
import os          # Sistema operativo
import sys         # Sistema
import datetime    # Fechas y tiempo
import random      # Números aleatorios
import re          # Expresiones regulares
import json        # JSON
import csv         # Archivos CSV

# Crear tu propio módulo: mi_modulo.py
# def saludar(nombre):
#     return f"Hola, {nombre}"

# Usarlo:
from mi_modulo import saludar
```

> [!TIP] 💡 Instalar paquetes externos con pip
> ```bash
> # Instalar
> pip install requests
> 
> # Ver instalados
> pip list
> 
> # Guardar dependencias
> pip freeze > requirements.txt
> 
> # Instalar desde archivo
> pip install -r requirements.txt
> ```

---

<!-- FUNCIONES ÚTILES -->
## 1️⃣4️⃣ Funciones útiles incorporadas

```python
# Entrada del usuario
nombre = input("¿Cómo te llamas? ")

# Conversión de tipos
int("42")       # 42
float("3.14")   # 3.14
str(42)         # "42"
list("abc")     # ["a", "b", "c"]
bool(1)         # True

# Matemáticas
abs(-5)         # 5
round(3.7)      # 4
round(3.14159, 2)  # 3.14
min(1, 2, 3)    # 1
max(1, 2, 3)    # 3
sum([1, 2, 3])  # 6
pow(2, 3)       # 8 (2^3)

# Iterables
len([1, 2, 3])       # 3
sorted([3, 1, 2])    # [1, 2, 3]
reversed([1, 2, 3])  # iterador invertido
enumerate(["a", "b"]) # [(0, "a"), (1, "b")]
zip([1, 2], ["a", "b"])  # [(1, "a"), (2, "b")]
map(lambda x: x*2, [1,2,3])  # [2, 4, 6]
filter(lambda x: x>1, [1,2,3]) # [2, 3]
any([False, True])  # True (al menos uno)
all([True, True])   # True (todos)

# Random
import random
random.random()           # 0.0 - 1.0
random.randint(1, 10)     # 1-10 inclusive
random.choice(["a","b"])  # Elemento aleatorio
random.shuffle(lista)     # Mezclar lista

# Datetime
from datetime import datetime, timedelta
ahora = datetime.now()
ahora.strftime("%Y-%m-%d %H:%M:%S")
mañana = ahora + timedelta(days=1)
```

---

<!-- ENTORNOS VIRTUALES -->
## 1️⃣5️⃣ Entornos virtuales
Los entornos virtuales aíslan las dependencias de cada proyecto.

```bash
# Crear entorno virtual
python -m venv venv

# Activar (Windows)
venv\Scripts\activate

# Activar (macOS/Linux)
source venv/bin/activate

# Instalar dependencias
pip install requests flask

# Guardar dependencias
pip freeze > requirements.txt

# Desactivar
deactivate
```

> [!TIP] 💡 Estructura de proyecto recomendada
> ```text
> mi_proyecto/
> ├── venv/               # Entorno virtual
> ├── src/
> │   ├── __init__.py
> │   └── main.py
> ├── tests/
> │   └── test_main.py
> ├── requirements.txt
> ├── README.md
> └── .gitignore
> ```

---

<!-- REFERENCIA -->
## 📋 Referencia rápida

| Categoría | Funciones/Métodos |
| :--- | :--- |
| **Strings** | `upper(), lower(), strip(), split(), join(), replace(), find(), startswith(), endswith(), format()` |
| **Listas** | `append(), insert(), extend(), remove(), pop(), clear(), sort(), reverse(), index(), count(), copy()` |
| **Diccionarios** | `keys(), values(), items(), get(), pop(), update(), clear(), copy()` |
| **Sets** | `add(), remove(), discard(), union(), intersection(), difference()` |
| **Archivos** | `open(), read(), readline(), readlines(), write(), close()` |
| **Built-ins** | `print(), input(), len(), range(), type(), int(), str(), list(), dict(), sum(), min(), max(), sorted(), enumerate(), zip(), map(), filter()` |

---

<!-- CHECKLIST -->
## ✓ Checklist de aprendizaje

- [ ] Sé instalar Python y ejecutar scripts
- [ ] Entiendo variables y tipos de datos
- [ ] Domino operadores aritméticos y lógicos
- [ ] Puedo trabajar con strings y f-strings
- [ ] Sé usar condicionales (if/elif/else)
- [ ] Domino listas y sus métodos
- [ ] Sé usar diccionarios
- [ ] Entiendo bucles for y while
- [ ] Puedo crear y usar funciones
- [ ] Sé crear clases y usar herencia
- [ ] Entiendo manejo de errores (try/except)
- [ ] Puedo leer y escribir archivos
- [ ] Sé importar módulos y usar pip
- [ ] Entiendo entornos virtuales
