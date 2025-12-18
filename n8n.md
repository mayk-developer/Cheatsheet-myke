# Cheat Sheet: n8n Local con OrbStack

La forma más rápida, ligera y moderna de correr n8n en tu Mac, usando **OrbStack** como motor de contenedores (reemplazo de Docker Desktop).

## 🐋 1. Instalar OrbStack

Si aún no tienes Docker, o usas Docker Desktop (es pesado), cámbiate a OrbStack. Es nativo de Swift y vuela.

```bash
brew install --cask orbstack
```
*Abre la app "OrbStack" una vez para finalizar la instalación.*

---



## ⚡ 3. Mejor forma de correr n8n (Docker Compose)

La forma más ordenada y recomendada.

### 1️⃣ Crear carpeta
```bash
mkdir n8n && cd n8n
```

### 2️⃣ Crear `docker-compose.yml`
Ejecuta:
```bash
nano docker-compose.yml
```
Pega el siguiente contenido (y guarda con `Ctrl+O`, `Enter`, `Ctrl+X`):

```yaml
version: "3.8"

services:
  n8n:
    image: docker.n8n.io/n8nio/n8n
    container_name: n8n
    restart: always
    ports:
      - "5678:5678"
    environment:
      - N8N_BASIC_AUTH_ACTIVE=true
      - N8N_BASIC_AUTH_USER=admin
      - N8N_BASIC_AUTH_PASSWORD=admin123
      - GENERIC_TIMEZONE=America/Lima
      - TZ=America/Lima
    volumes:
      - ./n8n_data:/home/node/.n8n
```

### 3️⃣ Levantar n8n (Instalación Automática)
Al ejecutar esto, Docker **descarga (instala)** la imagen completa de n8n dentro del contenedor y la inicia.

```bash
docker compose up -d
```
👉 **Acceso**: Abre `http://localhost:5678` en tu navegador (Safari/Chrome).

🔑 **Credenciales** (configuradas en el YAML):
- **Usuario**: `admin`
- **Password**: `admin123`

### 📦 Instalar paquetes extra (Python/Node) *dentro* del contenedor
Si necesitas librerías adicionales (ej. `moment` o `pandas`) para tus workflows:

**Node.js (npm):**
```bash
docker exec -u root -it n8n npm install -g nombre_paquete
```
*(Debes agregar `NODE_FUNCTION_ALLOW_EXTERNAL=nombre_paquete` en tu docker-compose environment)*

**Python:**
Viene con Python básico. Para instalar pip packages:
```bash
docker exec -u root -it n8n apk add --update python3 py3-pip
docker exec -u root -it n8n pip install nombre_paquete
```

---

### 🐛 Opción con Tunneling (Webhooks Públicos)
Para exponer tu n8n a internet (webhooks de Stripe/Slack) sin configurar nada extra:

Añade esto al `environment` en tu `docker-compose.yml`:
```yaml
      - N8N_TUNNEL_SUBDOMAIN=tu-nombre-unico
```
Y cambia el comando de inicio en el yaml (añadiendo `command`):
```yaml
    command: "start --tunnel"
```

---

## 🛠️ 3. Gestión Diaria

Comandos esenciales para controlar tu instancia.

| Acción | Comando |
| :--- | :--- |
| **Ver Logs** (en vivo) | `docker logs -f n8n` |
| **Detener** | `docker stop n8n` |
| **Iniciar** | `docker start n8n` |
| **Reiniciar** | `docker restart n8n` |
| **Entrar a la consola** | `docker exec -it n8n /bin/sh` |

### 🔎 Ver estado de contenedores

**Contenedores en ejecución**
```bash
docker ps
```
Lista todos los contenedores que están corriendo actualmente.
- **CONTAINER ID**: ID único.
- **NAMES**: Nombre del contenedor (ej. `n8n`).
- **STATUS**: Estado actual (activo, pausado, reiniciando...).

**Todos los contenedores (incluidos los parados)**
```bash
docker ps -a
```
Muestra el historial completo. En la columna **STATUS** verás:
- `Exited (0) X minutes ago` → Contenedor apagado correctamente.
- `Up 2 minutes` → Contenedor activo y corriendo.

---

## 🔄 4. Actualizar n8n

Mantén tu automatización al día.

```bash
# 1. Bajar la última versión
docker compose pull

# 2. Recrear el contenedor con la nueva imagen
docker compose up -d
```

---

## 🤖 5. Integration: n8n + AI Local (Ollama)

¿Quieres crear agentes de IA gratis y privados?
Si corres [Ollama](https://ollama.com) en tu Mac:

1.  En n8n, usa el nodo **HTTP Request** o los nodos de LangChain.
2.  **URL Base**: Usa `http://host.docker.internal:11434` en lugar de `localhost`.
    *OrbStack/Docker ven a tu Mac como `host.docker.internal`.*

---

## 📂 6. Backups

Donde viven tus datos (workflows/credenciales):

```bash
# Ver dónde está montado el volumen
docker volume inspect n8n_data
```

Para hacer backup manual, puedes usar el CLI de n8n dentro del container:
```bash
docker exec -u node n8n n8n export:workflow --all --output=/home/node/.n8n/backups/latest.json
```
*(Luego copias ese archivo desde el volumen a tu Mac).*
