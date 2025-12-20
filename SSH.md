# Cheat Sheet: SSH (Secure Shell)

Guía rápida y directa para configurar tus llaves SSH "sí o sí".

---

## 🚀 Configuración Paso a Paso (Windows y Mac)

Vamos paso a paso para dejarlo funcionando en ambos sistemas.

## 🔎 PASO 1: Verificar si ya tienes alguna clave SSH

Primero revisamos si ya existe algo.

**🪟 En Windows (CMD / PowerShell):**
```powershell
dir %USERPROFILE%\.ssh
```

**🍎 En Mac (Terminal):**
```bash
ls -al ~/.ssh
```

### Posibles resultados:
* ❌ *El sistema no puede encontrar la ruta / No such file* → no hay claves.
* ✅ Ves archivos como `id_ed25519` y `id_ed25519.pub`.

---

## 🔑 PASO 2: Crear una clave SSH (RECOMENDADO: ed25519)

Ejecuta este comando (es igual para ambos):

```bash
ssh-keygen -t ed25519 -C "tu_email@ejemplo.com"
```

1. Cuando pregunte **"Enter file in which to save..."**:
   👉 **Presiona ENTER** (usa la ruta por defecto).
2. Cuando pida **passphrase**:
   👉 **Presiona ENTER** (vacía) o pon una contraseña si quieres extra seguridad.

📌 Esto crea:
* **Windows:** `C:\Users\TU_USER\.ssh\id_ed25519`
* **Mac:** `/Users/tu_user/.ssh/id_ed25519`

---

## 🔁 PASO 3: Iniciar ssh-agent

El agente guarda tu llave en memoria para no pedir contraseña a cada rato.

**🪟 En Windows (PowerShell como Administrador):**
Necesitamos activar el servicio para que corra siempre.
```powershell
Get-Service -Name ssh-agent | Set-Service -StartupType Manual
Start-Service ssh-agent
```

**🍎 En Mac (Terminal):**
Solo iniciamos el proceso en la sesión actual.
```bash
eval "$(ssh-agent -s)"
```

---

## ➕ PASO 4: Agregar la clave al agente

Avisamos al agente que use nuestra nueva llave `ed25519`.

**🪟 En Windows:**
```powershell
ssh-add %USERPROFILE%\.ssh\id_ed25519
```

**🍎 En Mac:**
Además usamos `--apple-use-keychain` para que no pida clave al reiniciar.
```bash
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```

*Si todo está bien, verás: `Identity added`.*

---

## ✅ PASO 5: Verificar

Comprueba que la llave está cargada en el agente:

```bash
ssh-add -l
```

👉 Debe mostrar una línea con tu clave (sha256...).

---

## 🎯 AHORA: ¿CÓMO LA USO? (Casos Comunes)

Ya tienes la clave creada y cargada. El paso exacto depende de **para qué la necesitas**.

---

### 🥇 CASO 1: GitHub / GitLab (Sin Contraseña)

#### 🔹 1. Copiar tu clave pública
Necesitamos copiar el contenido de la clave `.pub` al portapapeles.

**🪟 Windows (PowerShell):**
```powershell
Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub | Set-Clipboard
# Si no te funciona Set-Clipboard, usa: type $env:USERPROFILE\.ssh\id_ed25519.pub | clip
```

**🍎 Mac (Terminal):**
```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

#### 🔹 2. Pegarla en GitHub
1. Entra a **GitHub** > **Settings** > **SSH and GPG keys**.
2. **New SSH key**.
3. **Title:** `Mi laptop`.
4. **Key:** Pega la clave (CTRL+V / CMD+V).
5. **Add SSH key**.

#### 🔹 3. Probar conexión
Ejecuta esto en tu terminal:

```bash
ssh -T git@github.com
```

✅ **Resultado Correcto:**
`Hi USER! You've successfully authenticated...`

#### 🔹 4. Usar repositorios por SSH
Ahora usa las URLs que empiezan con `git@`:

* **Clonar nuevo:**
  ```bash
  git clone git@github.com:usuario/repositorio.git
  ```
* **Cambiar repo existente a SSH:**
  ```bash
  git remote set-url origin git@github.com:usuario/repositorio.git
  ```

---

### 🥈 CASO 2: Conectar a Servidor Linux

Para entrar a un servidor remoto (VPS, EC2, Droplet):

```bash
ssh usuario@IP_DEL_SERVIDOR
```

Si quieres entrar **sin contraseña**, debes copiar tu clave pública al servidor:

**Comando mágico (desde tu compu local):**
```bash
ssh-copy-id usuario@IP_DEL_SERVIDOR
```
*(Luego de esto, entrarás directo sin pedir clave).*

---

### 🥉 CASO 3: Túneles / VPN / Automatización

Si necesitas esto para túneles o VPNs, generalmente necesitas subir tu clave privada o configurar `AuthorizedKeys` manualmente. Depende de si es:
* **Servidor Linux o Windows?**
* **¿Local o Internet?**

*(Consulta la referencia abajo para túneles específicos).*

---

## ✅ Checklist Final

✔ Clave creada (`id_ed25519`)
✔ ssh-agent corriendo
✔ Clave cargada (`ssh-add -l` la muestra)
✔ **Clave pública pegada en el destino (GitHub/Servidor)**

---

## 📚 Referencia Rápida de Comandos

### Conexión
```bash
ssh usuario@host
ssh -p 2222 usuario@host             # Puerto específico
ssh -i ~/.ssh/otra_llave usuario@host
```

### Transferencia (SCP)
```bash
# Subir
scp archivo.txt usuario@host:/ruta/destino/

# Descargar
scp usuario@host:/ruta/remota/archivo.txt .
```

### Túneles (Port Forwarding)
```bash
# Mi puerto 8080 -> Su puerto 3306
ssh -L 8080:localhost:3306 usuario@host
```
