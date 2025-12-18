# Cheat Sheet: Git

Guía esencial para el control de versiones con Git.

## Configuración Inicial

**Configurar usuario**
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "email@example.com"
```

**Ver configuración**
```bash
git config --list
```

## Iniciar y Clonar

**Nuevo repositorio**
```bash
git init
```

**Clonar repositorio**
```bash
git clone https://github.com/usuario/repo.git
git clone https://github.com/usuario/repo.git nombre_carpeta
```

## Flujo de Trabajo Básico

**Ver estado**
```bash
git status
```

**Añadir cambios (Staging)**
```bash
git add archivo.txt
git add .  # Añadir todo
```

**Guardar cambios (Commit)**
```bash
git commit -m "Mensaje descriptivo"
git commit -am "Añadir y commit de archivos modificados"
```

## Gestión de Ramas (Branches)

**Listar y Crear**
```bash
git branch        # Listar locales
git branch -a     # Listar todas (incluyendo remotas)
git branch nueva-rama  # Crear rama
```

**Cambiar de rama**
```bash
git checkout nombre-rama
git switch nombre-rama  # Alternativa moderna
```

**Crear y cambiar**
```bash
git checkout -b nueva-rama
```

**Fusionar (Merge)**
```bash
git merge rama-a-fusionar
```

**Eliminar rama**
```bash
git branch -d nombre-rama  # Si ya está fusionada
git branch -D nombre-rama  # Forzar eliminación
```

## Repositorios Remotos

**Gestionar remotos**
```bash
git remote -v
git remote add origin https://github.com/user/repo.git
```

**Sincronizar**
```bash
git fetch origin        # Descargar cambios sin fusionar
git pull origin main    # Descargar y fusionar
git push origin main    # Subir cambios
git push -u origin main # Subir y establecer upstream
```

## Deshacer Cambios

**Descartar cambios locales**
```bash
git restore archivo.txt
git checkout -- archivo.txt  # Versión antigua
```

**Sacar del staging (Unstage)**
```bash
git restore --staged archivo.txt
git reset HEAD archivo.txt
```

**Deshacer commits**
```bash
git reset --soft HEAD~1  # Deshace commit, mantiene cambios en staging
git reset --hard HEAD~1  # Deshace commit y BORRA cambios
git revert <commit-hash> # Crea nuevo commit invirtiendo cambios
```

## Historial y Logs

**Ver historial**
```bash
git log
git log --oneline
git log --graph --oneline --all  # Gráfico visual
```

**Ver diferencias**
```bash
git diff            # Working directory vs Staging
git diff --staged   # Staging vs Último commit
```

## Stashing (Guardado Temporal)

**Guardar y recuperar**
```bash
git stash           # Guardar temporalmente
git stash list      # Ver lista
git stash pop       # Aplicar y borrar el último
git stash apply     # Aplicar sin borrar
```

## Avanzado: Rebase y Cherry-pick

**Rebase (Reescribir historia)**
```bash
git checkout feature
git rebase main     # Pone tus cambios sobre lo último de main
```

**Rebase Interactivo (Limpiar commits)**
```bash
git rebase -i HEAD~3  # Modificar los últimos 3 commits
```

**Cherry-pick (Copiar commit específico)**
```bash
git cherry-pick <commit-hash>  # Aplica un commit de otra rama a la actual
```

## Etiquetas (Tags)

**Crear etiquetas**
```bash
git tag v1.0.0
git tag -a v1.0.0 -m "Versión 1.0.0"
git push origin v1.0.0
```

## Ignorar Archivos (.gitignore)

Crear un archivo `.gitignore` en la raíz para excluir archivos:
```gitignore
node_modules/
.env
*.log
.DS_Store
```

## Salvavidas

**Reflog (Recuperar lo perdido)**
```bash
git reflog  # Muestra TODOS los movimientos de HEAD
# Luego puedes hacer git reset --hard <hash-del-reflog> para volver a ese punto
```

## Resolución de Conflictos

1. Identificar archivos en conflicto con `git status`.
2. Abrir archivos y buscar marcas `<<<<<<<`, `=======`, `>>>>>>>`.
3. Editar para dejar el código deseado.
4. Añadir al staging: `git add archivo_resuelto.txt`.
5. Finalizar: `git commit`.

## Casuísticas y Trucos Avanzados

### Traer un archivo específico de otra rama
Recuperar o traer solo un archivo desde otra rama sin fusionar toda la rama.
```bash
# Trae el archivo y lo deja en Stage (listo para commit)
git checkout nombre-rama -- ruta/al/archivo.ext

# Versión moderna (más explicita)
git restore --source nombre-rama -- ruta/al/archivo.ext
```

### Modificar el último commit (Amend)
Útil si olvidaste añadir un archivo o quieres cambiar el mensaje del último commit *que aún no has subido*.
```bash
# Añade cambios olvidados al último commit
git add archivo-olvidado.txt
git commit --amend --no-edit  # Mantiene el mensaje original

# Cambiar solo el mensaje
git commit --amend -m "Nuevo mensaje corregido"
```

### Unificar Commits (Squash)
Combinar múltiples commits en uno solo antes de fusionar.
```bash
# Al fusionar una rama, aplasta todo su historial en un solo commit en tu rama actual
git merge --squash feature-branch
git commit -m "Implementar feature completa"
```

### Limpiar área de trabajo (Clean)
Eliminar archivos no rastreados (untracked) que no quieres (ej. archivos de build generados).
```bash
git clean -n   # (Dry Run) Muestra qué se borraría
git clean -fd  # (Force Directory) Borra archivos y directorios no rastreados
```

### Investigación y Depuración
Herramientas para encontrar culpables o errores.
```bash
# Ver quién modificó cada línea de un archivo
git blame archivo.txt

# Búsqueda binaria para encontrar el commit que introdujo un bug
git bisect start
git bisect bad HEAD    # La versión actual está mal
git bisect good <hash> # Esta versión antigua estaba bien
# ... Git te moverá entre commits ...
git bisect reset       # Terminar
```

### Alias Útiles
Comandos cortos para ahorrar tiempo. Configúralos una vez:
```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.lg "log --oneline --graph --all"

# Uso:
git co main
git st
git lg
```
