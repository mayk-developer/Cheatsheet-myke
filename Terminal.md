# Cheat Sheet: Terminal (Bash/Zsh)

Guía rápida de comandos esenciales para la terminal.

## Navegación del Sistema de Archivos

**Mostrar directorio actual (Print Working Directory)**
```bash
pwd
```

**Listar archivos y directorios**
```bash
ls      # Simple
ls -la  # Lista todo, incluyendo ocultos, con detalles
ls -lh  # Tamaños legibles por humanos
```

**Cambiar de directorio**
```bash
cd nombre_directorio  # Entrar a directorio
cd ..                 # Subir un nivel
cd ~                  # Ir al home
cd -                  # Ir al directorio anterior
```

## Gestión de Archivos y Directorios

**Crear directorios**
```bash
mkdir nombre_carpeta
mkdir -p ruta/completa/carpeta  # Crea directorios padres si no existen
```

**Crear archivos**
```bash
touch archivo.txt
```

**Copiar**
```bash
cp archivo.txt copia.txt
cp -r carpeta_origen carpeta_destino  # Recursivo para directorios
```

**Mover o Renombrar**
```bash
mv viejo.txt nuevo.txt
mv archivo.txt carpeta_destino/
```

**Eliminar**
```bash
rm archivo.txt
rm -rf carpeta_inutil  # Recursivo y forzado (¡Cuidado!)
```

## Visualización y Edición

**Ver contenido**
```bash
cat archivo.txt
less archivo.txt  # Paginado (salir con q)
head -n 5 archivo.txt  # Primeras 5 líneas
tail -f log.txt   # Ver últimas líneas en tiempo real
```

**Editores**
```bash
nano archivo.txt  # Fácil de usar
vim archivo.txt   # Avanzado
code .            # Abrir VS Code en el directorio actual
```

## Permisos y Propietarios

**Cambiar permisos (chmod)**
```bash
chmod +x script.sh  # Hacer ejecutable
chmod 755 archivo   # rwx para dueño, rx para otros
chmod 600 clave.pem # Solo lectura/escritura para dueño (seguro)
```

**Cambiar propietario (chown)**
```bash
chown usuario:grupo archivo
chown -R usuario:grupo carpeta  # Recursivo
```

## Búsqueda y Filtrado

**Buscar texto en archivos (grep)**
```bash
grep "error" server.log
grep -r "TODO" ./src  # Recursivo en directorio
grep -i "texto" archivo # Insensible a mayúsculas
```

**Buscar archivos (find)**
```bash
find . -name "*.js"        # Por nombre
find . -type f -size +10M  # Archivos mayores a 10MB
```

## Redirección y Tuberías (Pipes)

**Redirección de salida**
```bash
comando > archivo.txt   # Guarda salida en archivo (sobrescribe)
comando >> archivo.txt  # Añade al final del archivo
```

**Tuberías (Pipes)**
```bash
cat archivo.txt | grep "error"  # Pasa la salida de cat a grep
ps aux | grep node              # Busca procesos node
```

## Variables de Entorno

**Ver y definir**
```bash
env                 # Ver todas las variables
echo $HOME          # Ver valor de una variable
export MI_VAR="hola" # Definir variable para la sesión
```

## Sistema y Procesos

**Monitorización**
```bash
ps aux       # Todos los procesos
top          # Monitor tiempo real
htop         # Monitor tiempo real (más amigable)
uptime       # Tiempo de actividad y carga del sistema
whoami       # Usuario actual
sw_vers      # Versión de macOS
history      # Historial de comandos
```

**Terminar procesos**
```bash
kill 1234        # Matar por PID
killall node     # Matar por nombre
kill -9 1234     # Forzar cierre
```

## Redes

**Diagnóstico**
```bash
ping google.com
curl -I https://example.com  # Ver cabeceras HTTP
curl -O https://example.com/file.zip # Descargar archivo
lsof -i :8080                # Ver qué proceso usa el puerto 8080
ipconfig getifaddr en0       # Obtener IP local (Wi-Fi generalmente)
```

**SSH**
```bash
ssh usuario@servidor
ssh -i clave.pem usuario@servidor
```

## Compresión

**Tar (Archivos .tar.gz)**
```bash
tar -czvf archivo.tar.gz carpeta/  # Comprimir
tar -xzvf archivo.tar.gz           # Descomprimir
```

**Zip**
```bash
zip -r archivo.zip carpeta/
unzip archivo.zip
```

## Disco

**Espacio**
```bash
df -h  # Espacio libre en disco
du -sh carpeta/ # Tamaño que ocupa una carpeta
ncdu            # Analizador de disco interactivo (requiere instalación)
```

## Mantenimiento y Limpieza

**Limpieza de Sistema y Paquetes**
```bash
brew cleanup             # Elimina versiones antiguas de paquetes Homebrew
rm -rf ~/.Trash/*        # Vacía la papelera
sudo rm -rf /Library/Caches/* # Limpia cachés del sistema (¡Cuidado!)
```

**Limpieza de Desarrollo**
```bash
docker system prune -a   # Elimina todo lo no usado en Docker
xcrun simctl delete unavailable # Elimina simuladores de iOS viejos
```

**Purgar Espacio en Disco (Snapshots locales)**
El espacio "Purgable" suele estar ocupado por instantáneas locales de Time Machine.
```bash
tmutil listlocalsnapshots /              # Listar snapshots
# Método 1 (Estándar): Eliminar snapshots
for d in $(tmutil listlocalsnapshots / | grep -oE '[0-9]+-[0-9]+-[0-9]+-[0-9]+'); do sudo tmutil deletelocalsnapshots $d; done
```

**Método 2 (Agresivo - Si el espacio no se libera)**
Si macOS no libera el espacio "Purgable" (cachés, swap), puedes forzarlo creando un archivo gigante hasta llenar el disco y luego borrándolo. El sistema borrará automáticamente lo purgable para hacer espacio.
```bash
dd if=/dev/zero of=~/borrame.file bs=15m    # Crea un archivo hasta llenar el disco (Ctrl+C cuando diga 'No space')
rm ~/borrame.file                           # Bórralo inmediatamente
```

**Purgar Memoria RAM**
```bash
sudo purge  # Libera memoria RAM inactiva (requiere contraseña)
```

## Crear Atajos Personalizados (Aliases)

Puedes crear tus propios comandos cortos para sustituir los largos.

**Definir un alias**
```bash
alias nombre="comando largo"
# Ejemplo: 'll' en lugar de 'ls -la'
alias ll="ls -la"
```

**Hacerlos permanentes**
Debes agregarlos a tu archivo de configuración (`.bashrc` o `.zshrc`).

## Atajos de Teclado

- `Ctrl + C`: Cancelar comando.
- `Ctrl + L`: Limpiar pantalla.
- `Ctrl + R`: Buscar en el historial de comandos.
- `Ctrl + A` / `Ctrl + E`: Ir al Inicio / Fin de línea.
- `Ctrl + U`: Borrar toda la línea (desde el cursor hacia atrás).
- `Ctrl + K`: Borrar el resto de la línea (desde el cursor hacia adelante).
- `Ctrl + W`: Borrar la palabra anterior.
