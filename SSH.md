# Cheat Sheet: SSH (Secure Shell)

Guía rápida para conexiones remotas seguras y gestión de claves.

## Conexión Básica

**Conectar a un servidor**
```bash
ssh usuario@host
ssh usuario@192.168.1.10
```

**Especificar puerto**
```bash
ssh -p 2222 usuario@host
```

**Especificar archivo de identidad (clave privada)**
```bash
ssh -i ~/.ssh/mi_clave_pem usuario@host
```

## Gestión de Claves (Keys)

**Generar par de claves (Pública/Privada)**
```bash
ssh-keygen -t ed25519 -C "email@example.com"  # Recomendado (más seguro/rápido)
ssh-keygen -t rsa -b 4096 -C "email@example.com" # Compatibilidad legacy
```

**Copiar clave pública al servidor (Login sin contraseña)**
```bash
ssh-copy-id usuario@host
ssh-copy-id -i ~/.ssh/id_ed25519.pub usuario@host # Especificando clave
```

**Agente SSH (Evitar escribir passphrase)**
```bash
eval "$(ssh-agent -s)"   # Iniciar agente
ssh-add ~/.ssh/id_ed25519 # Añadir clave
```

## Transferencia de Archivos (SCP)

**Copiar de Local a Remoto**
```bash
scp archivo.txt usuario@host:/ruta/destino/
scp -r carpeta/ usuario@host:/ruta/destino/  # Recursivo
```

**Copiar de Remoto a Local**
```bash
scp usuario@host:/ruta/remota/archivo.txt .
scp -r usuario@host:/ruta/remota/carpeta .
```

**Usando puerto específico**
```bash
scp -P 2222 archivo.txt usuario@host:/ruta/
```

## Configuración Avanzada (~/.ssh/config)

Crear o editar `~/.ssh/config` para usar alias en lugar de IPs y usuarios largos.

```ssh
# ~/.ssh/config

Host mi-servidor
    HostName 192.168.1.10
    User maykol
    Port 22
    IdentityFile ~/.ssh/id_ed25519

Host produccion
    HostName ec2-xx-xx-xx.compute.amazonaws.com
    User ubuntu
    IdentityFile ~/.ssh/aws-key.pem
```

**Uso con alias**
```bash
ssh mi-servidor
scp archivo.txt produccion:/home/ubuntu/
```

## Túneles (Port Forwarding)

**Local Forwarding (-L)**
Acceder a un servicio del servidor (ej. base de datos en puerto 3306) desde mi puerto local 8080.
```bash
ssh -L 8080:localhost:3306 usuario@host
# Ahora puedes conectar a localhost:8080 y llegarás al 3306 del servidor
```

**Remote Forwarding (-R)**
Permitir que el servidor acceda a un servicio de mi máquina local (ej. mi server web en 3000) a través de su puerto 9000.
```bash
ssh -R 9000:localhost:3000 usuario@host
```

## Diagnóstico

**Modo Verbose (Depuración)**
```bash
ssh -v usuario@host   # Info básica
ssh -vvv usuario@host # Info muy detallada (útil para errores de conexión)
```
