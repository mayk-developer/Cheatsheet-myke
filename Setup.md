# Cheat Sheet: Setup Definitivo para Programadores (macOS 2024+)

Guía "Opinionated" con las herramientas más modernas, rápidas y eficientes del momento.

## 🍺 1. El Gestor de Paquetes: Homebrew

Todo empieza aquí.
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

*Tip Pro: Crea un archivo `Brewfile` en tu home para reinstalar todo en un nuevo Mac con `brew bundle`.*

## 🚀 2. La Terminal Moderna

Olvídate de la terminal por defecto.

### Emulador de Terminal
- **[Warp](https://www.warp.dev/)**: La terminal del siglo XXI. IA integrada, edición tipo bloque (como un editor de código), rapidísima. (**Recomendado**)
  ```bash
  brew install --cask warp
  ```
- **iTerm2**: La clásica confiable, super configurable.
  ```bash
  brew install --cask iterm2
  ```

### Shell & Prompts
Haz que tu terminal se vea genial y te dé información útil (git branch, versiones, errores).

1.  **Starship**: Prompt minimalista, ultrarrápido y compatible con cualquier shell.
    ```bash
    brew install starship
    # Añadir al final de ~/.zshrc:
    # eval "$(starship init zsh)"
    ```
2.  **Oh My Zsh**: Framework para gestionar configuración de Zsh.
    ```bash
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
    ```
3.  **Plugins Imprescindibles**:
    ```bash
    # Autosugerencias (como en fish)
    brew install zsh-autosuggestions
    # Coloreado de sintaxis
    brew install zsh-syntax-highlighting
    ```

### CLI "Vitaminados" (Rust Replacements)
Reemplazos modernos para comandos `unix` antiguos.
```bash
brew install bat      # cat con alas (colores, paginación)
brew install eza      # ls moderno (iconos, git status)
brew install fd       # find más rápido y amigable
brew install ripgrep  # grep ultrarrápido (comando: rg)
brew install fzf      # Buscador difuso (Ctrl+R supervitaminado)
brew install tldr     # Man pages resumidas y con ejemplos
brew install jq       # Procesador de JSON en terminal
```

## 🛠️ 3. Lenguajes & Version Managers

No instales lenguajes directo con brew si puedes evitarlo. Usa gestores de versiones.

### Python: `uv` (The new standard)
Olvídate de pip, poetry y venv lentos. `uv` es escrito en Rust y es instantáneo.
```bash
# Instalar uv
curl -LsSf https://astral.sh/uv/install.sh | sh

# Uso
uv python install 3.12   # Instalar Python
uv venv                  # Crear entorno virtual rapidísimo
uv pip install requests  # Instalar paquetes
```

### Node.js: `Volta` vs `nvm`
`Volta` es más simple y rápido que `nvm`.
```bash
# Instalar Volta
curl https://get.volta.sh | bash

# Uso
volta install node       # Instala la última LTS
volta install node@20    # Instala versión específica
```

### Otros
```bash
brew install go          # Go (suele actualizarse bien con brew)
brew install rustup-init # Rust
```

## 💻 4. Editores e IDEs

- **Cursor**: VS Code con "Superpoderes de IA". Si pagas Copilot, cancelalo y usa esto.
  ```bash
  brew install --cask cursor
  ```
- **VS Code**: El estándar si prefieres configurar todo tú mismo.
  ```bash
  brew install --cask visual-studio-code
  ```
- **JetBrains Toolbox**: Para instalar PyCharm, WebStorm, IntelliJ, etc.
  ```bash
  brew install --cask jetbrains-toolbox
  ```

## 🐳 5. Contenedores & Bases de Datos

### OrbStack (Reemplazo de Docker Desktop)
Mucho más ligero, rápido y nativo que Docker Desktop. Consume menos batería y RAM.
```bash
brew install --cask orbstack
```

### Bases de Datos Locales (Sin Docker)
Si necesitas correr Postgres/Redis/MySQL rápido sin configurar contenedores.
- **DBngin**: Levanta bases de datos en 1 click.
  ```bash
  brew install --cask dbngin
  ```
- **Postgres.app**: La forma más mac-native de correr Postgres.

## ⚡ 6. Productividad Mac

Herramientas que todo dev debería tener.

- **Raycast**: Reemplazo de Spotlight. Calculadora, conversores, gestión de ventanas, extensiones... es otro nivel. (**Imprescindible**)
  ```bash
  brew install --cask raycast
  ```
- **Rectangle**: Gestión de ventanas (Snap) tipo Windows.
  ```bash
  brew install --cask rectangle
  ```
- **Obsidian**: Tu segundo cerebro (donde lees esto).
  ```bash
  brew install --cask obsidian
  ```
- **Shottr**: Capturas de pantalla con herramientas de pixelar, medir, etc.
  ```bash
  brew install --cask shottr
  ```

## 🎨 7. Fuentes (Nerd Fonts)

Necesarias para que tu terminal muestre iconos bonitos.
```bash
brew install list-nerd-font-installed # (opcional para ver listas)
# Recomendadas:
brew install --cask font-jetbrains-mono-nerd-font
brew install --cask font-hack-nerd-font
brew install --cask font-fira-code-nerd-font
```
**Configurar**: Luego en tu terminal (Warp/iTerm) selecciona "JetBrainsMono Nerd Font" como tipografía.
