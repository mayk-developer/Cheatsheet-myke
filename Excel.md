# 📗 Cheat Sheet: Microsoft Excel

> [!INFO] Resumen
> Guía definitiva de fórmulas avanzadas, tablas dinámicas y atajos comparados para **Mac** y **Windows**.

## 🧠 Fórmulas Imprescindibles

> [!TIP] Tip Pro: XLOOKUP
> Olvida `VLOOKUP` (BUSCARV). `XLOOKUP` no se rompe si insertas columnas y es más rápido.

### Búsqueda y Referencia
| Fórmula | Descripción | Ejemplo |
| :--- | :--- | :--- |
| `BUSCARX` | **El Rey.** Busca en cualquier dirección. | `=BUSCARX(valor, buscar_en, devolver_de)` |
| `BUSCARV` | El clásico (obsoleto pero omnipresente). | `=BUSCARV(valor, rango, col, 0)` |
| `INDICE + COINCIDIR` | La alternativa potente clásica. | `=INDICE(col_retorno, COINCIDIR(valor, col_busq, 0))` |

### Lógica
| Fórmula | Descripción | Ejemplo |
| :--- | :--- | :--- |
| `SI.CONJUNTO` | Múltiples condiciones (Adiós SIs anidados). | `=SI.CONJUNTO(A1>10,"Alto", A1>5,"Medio", VERDADERO,"Bajo")` |
| `SI.ERROR` | Limpia tus errores (#N/A) con elegancia. | `=SI.ERROR(fórmula, "No encontrado")` |

## ⌨️ Atajos de Teclado (Mac vs Windows)

> [!ABSTRACT] Navegación y Selección
| Acción | 🍎 Mac | 🪟 Windows |
| :--- | :--- | :--- |
| **Seleccionar Columna** | `Ctrl + Espacio` | `Ctrl + Espacio` |
| **Seleccionar Fila** | `Shift + Espacio` | `Shift + Espacio` |
| **Saltar al final** | `Cmd + Flechas` | `Ctrl + Flechas` |
| **Seleccionar hasta final**| `Cmd + Shift + Flechas`| `Ctrl + Shift + Flechas`|
| **Cambiar Hoja** | `Option + Flechas` | `Ctrl + RePág / AvPág` |
| **Ir a la celda A1** | `Cmd + Fn + Izq` | `Ctrl + Inicio` |

> [!SUCCESS] Datos y Herramientas (¡Muy Usados!)
| Acción | 🍎 Mac | 🪟 Windows |
| :--- | :--- | :--- |
| **Poner/Quitar Filtros** | `Cmd + Shift + F` | `Ctrl + Shift + L` |
| **Buscar** | `Cmd + F` | `Ctrl + B` (o `Ctrl+F`) |
| **Reemplazar** | `Ctrl + H` (o `Cmd+Shift+H`) | `Ctrl + L` (o `Ctrl+H`) |
| **Rellenar Abajo** | `Cmd + D` | `Ctrl + D` |
| **Rellenar Derecha** | `Cmd + R` | `Ctrl + R` |
| **Crear Tabla** | `Cmd + T` | `Ctrl + T` |

> [!EXAMPLE] Edición y Formato
| Acción | 🍎 Mac | 🪟 Windows |
| :--- | :--- | :--- |
| **Editar Celda** | `Ctrl + U` (o F2) | `F2` |
| **Pegado Especial** | `Cmd + Ctrl + V` | `Ctrl + Alt + V` |
| **Autosuma** | `Cmd + Shift + T` | `Alt + =` |
| **Insertar Fecha** | `Ctrl + ;` | `Ctrl + ;` |
| **Insertar Hora** | `Cmd + ;` | `Ctrl + Shift + :` |
| **Formato Moneda** | `Ctrl + Shift + 4` ($) | `Ctrl + Shift + 4` ($) |
| **Formato Porcentaje** | `Ctrl + Shift + 5` (%) | `Ctrl + Shift + 5` (%) |

## 📊 Tablas Dinámicas (Pivot Tables)

> [!NOTE] Pasos Rápidos
> 1. `Insertar > Tabla Dinámica`.
> 2. **Filas**: Categorías (ej. *Producto*).
> 3. **Valores**: Métricas (ej. *Ventas*).

**Trucos de Visualización:**
- **% del Total**: Click derecho en el valor > `Mostrar valores como` > `% del total general`.
- **Agrupar Fechas**: Click derecho en una fecha > `Agrupar` > Selecciona "Meses" y "Años".

## 🚀 Trucos "Pata Negra"

> [!SUCCESS] Flash Fill (Relleno Rápido)
> Escribe un patrón (ej: extraer nombre de `juan@empresa.com` -> "Juan") y presiona:
> - **Mac**: `Ctrl + E`
> - **Win**: `Ctrl + E`
> Excel completará toda la columna mágicamente.

> [!WARNING] Limpieza de Datos
> Antes de analizar, siempre:
> 1. `Datos > Quitar Duplicados`.
> 2. `Datos > Texto en columnas` (si tienes todo pegado en una celda).
> 3. Selecciona datos y presiona `Ctrl+T` (Mac/Win) para convertir en **Tabla Oficial** (filtros y diseño automático).
