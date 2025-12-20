# 📊 Cheat Sheet: Google Sheets

> [!INFO] Resumen
> El poder de la nube: colaboración en tiempo real y fórmulas exclusivas de Google.

## 🌩️ Fórmulas Cloud (Solo en Sheets)

> [!TIP] Superpoderes
> Estas funciones hacen cosas que Excel tradicional no puede hacer sin plugins.

| Fórmula | Descripción | Ejemplo |
| :--- | :--- | :--- |
| `IMPORTRANGE` | **Importa datos de OTRA hoja** (URL). Requiere permiso una vez. | `=IMPORTRANGE("url", "Hoja!A1:B")` |
| `QUERY` | **SQL en tus celdas.** Filtra y ordena con lenguaje de base de datos. | `=QUERY(A:C, "Select A Where B > 100", 1)` |
| `SPARKLINE` | Gráficos diminutos dentro de una sola celda. | `=SPARKLINE(A1:A10)` |
| `GOOGLEFINANCE`| Cotizaciones en tiempo real (Stocks, Divisas). | `=GOOGLEFINANCE("USDCOP")` |
| `IMAGE` | Inserta una imagen desde una URL. | `=IMAGE("https://...")` |
| `UNIQUE` | Lista de valores únicos (elimina duplicados dinámicamente). | `=UNIQUE(A:A)` |

## ⌨️ Atajos de Teclado (Mac vs Windows)

> [!IMPORTANT] Habilitar Atajos
> Asegúrate de activar: `Ayuda > Atajos de teclado > [x] Anular atajos del navegador` si algunos no funcionan.

> [!ABSTRACT] Acciones Esenciales
| Acción | 🍎 Mac | 🪟 Windows |
| :--- | :--- | :--- |
| **Ver TODOS los atajos** | `Cmd + /` | `Ctrl + /` |
| **Poner/Quitar Filtros** | *Menú Datos* (o `Ctrl+Opt+R`) | `Ctrl + Shift + L` (a veces) |
| **Buscar y Reemplazar** | `Cmd + Shift + H` | `Ctrl + H` |
| **Rellenar Abajo** | `Cmd + D` | `Ctrl + D` |
| **Rellenar Derecha** | `Cmd + R` | `Ctrl + R` |
| **Pegar SOLO VALORES** | `Cmd + Shift + V` | `Ctrl + Shift + V` |
| **Pegar SOLO FORMATO** | `Cmd + Option + V` | `Ctrl + Alt + V` |
| **Insertar Enlace** | `Cmd + K` | `Ctrl + K` |
| **Insertar Comentario** | `Cmd + Option + M` | `Ctrl + Alt + M` |

> [!EXAMPLE] Filas y Columnas
| Acción | 🍎 Mac | 🪟 Windows |
| :--- | :--- | :--- |
| **Insertar Fila Encima** | `Ctrl + Option + I`, luego `R` | `Alt + I`, luego `R` |
| **Eliminar Fila** | `Ctrl + Option + E`, luego `D` | `Alt + E`, luego `D` |
| **Ocultar Fila** | `Cmd + Option + 9` | `Ctrl + Alt + 9` |

## 👥 Colaboración y Trucos

> [!SUCCESS] Smart Canvas
> Escribe **`@`** en cualquier celda para insertar:
> - Personas (notifica por email).
> - Archivos (crea enlace inteligente).
> - Fechas (calendario desplegable).

> [!WARNING] Vistas de Filtro (¡Vital!)
> Si trabajas en equipo, **NO USES EL FILTRO NORMAL**.
> Ve a `Datos > Vistas de filtro > Crear nueva`.
> *Esto filtra los datos SOLO PARA TI sin desordenar la vista de tus compañeros.*
