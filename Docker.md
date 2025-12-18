# Cheat Sheet: Docker

Guía rápida para la gestión de contenedores e imágenes con Docker.

## Gestión de Imágenes

**Construir imagen**
```bash
docker build -t mi-app:v1 .
docker build -f Dockerfile.dev -t mi-app:dev . # Usar otro Dockerfile
```

**Descargar imagen**
```bash
docker pull python:3.9
docker pull postgres:alpine
```

**Listar y Eliminar**
```bash
docker images
docker rmi mi-app:v1
docker image prune  # Eliminar imágenes sin etiqueta (dangling)
```

## Gestión de Contenedores

**Ejecutar contenedor**
```bash
docker run hello-world
docker run -it ubuntu bash  # Interactivo
```

**Ejecutar en segundo plano (Detached)**
```bash
docker run -d -p 8080:80 --name mi-web nginx
# -d: Detached
# -p: Puerto host:contenedor
# --name: Nombre personalizado
```

**Listar contenedores**
```bash
docker ps      # En ejecución
docker ps -a   # Todos
docker ps -q   # Solo IDs
```

**Controlar estado**
```bash
docker stop mi-web
docker start mi-web
docker restart mi-web
```

**Eliminar**
```bash
docker rm mi-web
docker rm -f mi-web  # Forzar si está corriendo
docker rm $(docker ps -aq) # Eliminar TODOS (¡Cuidado!)
```

## Logs y Ejecución

**Ver logs**
```bash
docker logs mi-web
docker logs -f mi-web  # Seguir en tiempo real
docker logs --tail 100 mi-web # Últimas 100 líneas
```

**Ejecutar comando en contenedor activo**
```bash
docker exec -it mi-web bash
docker exec -it mi-db psql -U user  # Ejemplo postgres
```

## Redes (Networks)

**Gestión de redes**
```bash
docker network ls
docker network create mi-red
docker network inspect mi-red
```

**Conectar contenedor a red**
```bash
docker run --network mi-red ...
docker network connect mi-red mi-contenedor
```

## Volúmenes (Volumes)

**Gestión de volúmenes**
```bash
docker volume ls
docker volume create mi-data
docker volume inspect mi-data
docker volume prune  # Eliminar no usados
```

**Usar volúmenes**
```bash
docker run -v mi-data:/var/lib/mysql ...  # Volumen nombrado
docker run -v $(pwd)/data:/app/data ...   # Bind mount (carpeta local)
```

## Dockerfile Básico

Ejemplo de estructura común:

```dockerfile
# Imagen base
FROM node:18-alpine

# Directorio de trabajo
WORKDIR /app

# Copiar dependencias primero (para aprovechar caché)
COPY package*.json ./

# Instalar dependencias
RUN npm install

# Copiar código fuente
COPY . .

# Exponer puerto
EXPOSE 3000

# Comando de inicio
CMD ["npm", "start"]
```

## Docker Compose

**Comandos básicos**
```bash
docker-compose up        # Iniciar (bloquea terminal)
docker-compose up -d     # Iniciar en segundo plano
docker-compose down      # Detener y borrar todo
docker-compose down -v   # Borrar también volúmenes
```

**Gestión**
```bash
docker-compose logs -f
docker-compose ps
docker-compose restart servicio
docker-compose build     # Reconstruir imágenes
```

## Limpieza del Sistema

**Prune (Limpieza general)**
```bash
docker system prune      # Borra contenedores parados, redes sin usar, etc.
docker system prune -a   # Borra TAMBIÉN imágenes no usadas
```

**Inspección**
```bash
docker inspect mi-contenedor  # Ver toda la info (JSON)
docker stats                  # Ver uso de CPU/Memoria en vivo
```
