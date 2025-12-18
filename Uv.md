# Cheat Sheet: UV (Python Package Manager)

`uv` es un gestor de paquetes y proyectos Python escrito en Rust, diseñado para ser extremadamente rápido. Reemplaza a `pip`, `pip-tools` y `virtualenv`.

## 📥 Instalación

### Método Recomendado (macOS/Linux)
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Otras opciones
| Método | Comando |
| :--- | :--- |
| **Homebrew** | `brew install uv` |
| **Pip** | `pip install uv` |
| **Windows** | `powershell -c "irm https://astral.sh/uv/install.ps1 | iex"` |

## 🚀 Gestión de Proyectos (Estilo Cargo/Poetry)

Comandos modernos para gestionar dependencias en un proyecto (`pyproject.toml`).

| Comando | Acción |
| :--- | :--- |
| `uv init` | Inicializa un nuevo proyecto en el directorio actual. |
| `uv add <paquete>` | Agrega una dependencia y la instala. |
| `uv add --dev <paquete>` | Agrega una dependencia de desarrollo. |
| `uv remove <paquete>` | Elimina una dependencia. |
| `uv run <script.py>` | Ejecuta un script dentro del entorno virtual del proyecto. |
| `uv run -- <comando>` | Ejecuta cualquier comando en el entorno enterno. |
| `uv sync` | Sincroniza el entorno con `uv.lock`. |

## 📦 Reemplazo de Pip (Interfaz compatible)

Si prefieres usarlo como un `pip` más rápido.

| Comando Tradicional | Comando UV |
| :--- | :--- |
| `pip install <paquete>` | `uv pip install <paquete>` |
| `pip install -r req.txt` | `uv pip install -r requirements.txt` |
| `pip list` | `uv pip list` |
| `pip freeze` | `uv pip freeze` |
| `pip compile` | `uv pip compile` (Genera requisitos bloqueados) |
| `pip sync` | `uv pip sync` (Sincroniza entorno) |

## 🌐 Entornos Virtuales

| Comando | Acción |
| :--- | :--- |
| `uv venv` | Crea un entorno virtual en `.venv`. |
| `uv venv mi_entorno` | Crea un entorno virtual con nombre personalizado. |
| `uv venv --python 3.12` | Crea un entorno virtual con una versión específica de Python. |

## 🐍 Gestión de Python

`uv` también puede instalar y gestionar versiones de Python.

| Comando | Acción |
| :--- | :--- |
| `uv python list` | Lista las versiones de Python disponibles e instaladas. |
| `uv python install 3.12` | Instala Python 3.12. |
| `uv python uninstall 3.12` | Desinstala una versión de Python. |
| `uv python pin 3.11` | Fija la versión de Python para el proyecto actual. |

---
*Más información en la [documentación oficial](https://docs.astral.sh/uv/).*
