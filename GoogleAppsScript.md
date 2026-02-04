# 📬 Sistema de Notificaciones Automáticas para Google Drive

> **Versión:** 1.0  
> **Fecha:** Diciembre 2024  
> **Autor:** Maykol Madueño  
> **Empresa:** Hergonsa

---

## 📋 Descripción General

Este sistema permite enviar notificaciones automáticas por correo electrónico cuando se suben archivos a una carpeta de Google Drive y todas sus subcarpetas anidadas.

### ✨ Características

- ✅ Monitoreo automático cada X minutos
- ✅ Detecta archivos en subcarpetas de cualquier nivel de profundidad
- ✅ Notifica a TODOS los colaboradores de la carpeta
- ✅ Excluye de la notificación a quien subió el archivo
- ✅ Un solo correo grupal (no individual)
- ✅ Diseño profesional del email en HTML
- ✅ Sin costo adicional (usa recursos gratuitos de Google)
- ✅ No requiere tener nada abierto, corre en segundo plano

---

## 🏗️ Arquitectura

```
┌─────────────────────────────────────────────────────────────┐
│                    GOOGLE APPS SCRIPT                        │
│                                                              │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐     │
│  │   Trigger   │───▶│ checkNew    │───▶│   Gmail     │     │
│  │ (cada X min)│    │   Files()   │    │  sendEmail  │     │
│  └─────────────┘    └─────────────┘    └─────────────┘     │
│                            │                                 │
│                            ▼                                 │
│                    ┌─────────────┐                          │
│                    │ Google Drive│                          │
│                    │     API     │                          │
│                    └─────────────┘                          │
└─────────────────────────────────────────────────────────────┘
```

---

## ⚙️ Configuración Inicial

### Paso 1: Obtener el ID de la Carpeta

1. Abre la carpeta en Google Drive
2. Copia el ID de la URL:

```
https://drive.google.com/drive/folders/XXXXXXXXXXXXXXXXXXXXXXX
                                        └──────────────────────┘
                                           Este es el ID
```

### Paso 2: Crear el Proyecto en Apps Script

1. Inicia sesión con la cuenta que será el **owner** del script
2. Ve a [script.google.com](https://script.google.com)
3. Click en **"Nuevo proyecto"**
4. Nombra el proyecto (ej: "Notificaciones Drive - [Nombre Carpeta]")
5. Borra el código existente
6. Pega el código completo (ver sección Código Fuente)
7. Modifica el `ROOT_FOLDER_ID` con tu ID de carpeta
8. Guarda (Ctrl+S)

### Paso 3: Activar el Monitoreo

1. Selecciona **`createTrigger`** del menú desplegable
2. Click en **▶️ Ejecutar**
3. Autoriza los permisos cuando te lo pida
4. ¡Listo! Ya está funcionando

---

## 🎛️ Panel de Control - Funciones Disponibles

| Función | Descripción | Cuándo usarla |
|---------|-------------|---------------|
| `createTrigger` | Activa el monitoreo automático | Una vez al configurar |
| `deleteTrigger` | Detiene el monitoreo | Cuando quieras pausar |
| `testNotification` | Prueba manual (busca archivos de última hora) | Para probar |
| `debugCollaborators` | Ver lista de colaboradores | Para verificar permisos |
| `checkNewFiles` | Función principal | Se ejecuta automáticamente |

---

## ⏱️ Intervalos Recomendados

| Intervalo | Ejecuciones/día | Uso recomendado |
|-----------|-----------------|-----------------|
| 1 minuto | 1,440 | Notificaciones urgentes |
| **5 minutos** | 288 | **Recomendado** - Buen balance |
| 15 minutos | 96 | Carpetas con poco movimiento |
| 30 minutos | 48 | Mínimo consumo de recursos |

Para cambiar el intervalo, modifica:

```javascript
const CONFIG = {
  ROOT_FOLDER_ID: 'tu-id-aqui',
  CHECK_INTERVAL_MINUTES: 5  // Cambiar este valor
};
```

Luego ejecuta `createTrigger` nuevamente.

---

## 📊 Límites Gratuitos de Google

| Recurso | Límite Diario | Notas |
|---------|---------------|-------|
| Tiempo de ejecución | 90 min/día | Suficiente para uso normal |
| Emails enviados | 100/día (Gmail) | 1,500/día con Google Workspace |
| Llamadas a Drive | 20,000/día | Muy amplio |
| Triggers | 20 por usuario | Suficiente para varias carpetas |

---

## 📧 Formato del Email

El sistema envía un correo con el siguiente formato:

```
┌─────────────────────────────────────────┐
│         Nuevos Archivos                 │  ← Header azul
├─────────────────────────────────────────┤
│                                         │
│  Hola,                                  │
│                                         │
│  [Nombre] ha subido X archivo(s) a la   │
│  carpeta compartida:                    │
│                                         │
│  ┌───────────────────────────────────┐  │
│  │ Archivo              │   Acción   │  │
│  ├───────────────────────────────────┤  │
│  │ documento.pdf        │  [Abrir]   │  │
│  │ Carpeta: Subcarpeta1 │            │  │
│  └───────────────────────────────────┘  │
│                                         │
├─────────────────────────────────────────┤
│  Mensaje automático del sistema...      │  ← Footer
└─────────────────────────────────────────┘
```

---

## 🔄 Replicar para Otra Carpeta

### Checklist Rápido

- [ ] Identificar la nueva carpeta y obtener su ID
- [ ] Definir quién será el owner (desde qué cuenta se crean los scripts)
- [ ] Crear nuevo proyecto en Apps Script (con la cuenta del owner)
- [ ] Pegar el código y cambiar `ROOT_FOLDER_ID`
- [ ] Ejecutar `createTrigger`
- [ ] Probar con `testNotification`

### Importante

| Aspecto | Detalle |
|---------|---------|
| **Owner del script** | La cuenta que crea el proyecto |
| **Emails salen desde** | La cuenta del owner |
| **Colaboradores notificados** | Todos los que tienen acceso a la carpeta |
| **Subcarpetas** | Se incluyen automáticamente (cualquier nivel) |

---

## 🐛 Solución de Problemas

### No llegan los correos

1. Ejecuta `debugCollaborators` y verifica que detecta a todos
2. Ejecuta `testNotification` y revisa los logs
3. Verifica que el trigger esté activo (⏰ Activadores)

### Error de permisos

1. Elimina el trigger con `deleteTrigger`
2. Ejecuta `createTrigger` nuevamente
3. Acepta todos los permisos

### Quiero cambiar el intervalo

1. Modifica `CHECK_INTERVAL_MINUTES` en el código
2. Guarda
3. Ejecuta `deleteTrigger`
4. Ejecuta `createTrigger`

### Quiero pausar temporalmente

- Ejecuta `deleteTrigger`
- Para reactivar: ejecuta `createTrigger`

---

## 📁 Estructura de Carpetas Soportada

```
📁 Carpeta Principal (ROOT_FOLDER_ID)
│
├── 📄 archivo.pdf ✅ Detectado
│
├── 📁 Subcarpeta Nivel 1
│   ├── 📄 documento.docx ✅ Detectado
│   │
│   └── 📁 Subcarpeta Nivel 2
│       ├── 📄 imagen.png ✅ Detectado
│       │
│       └── 📁 Subcarpeta Nivel 3
│           └── 📄 video.mp4 ✅ Detectado
│
└── 📁 Otra Subcarpeta
    └── 📄 excel.xlsx ✅ Detectado
```

**Cualquier nivel de profundidad es detectado automáticamente.**

---

## 💻 Código Fuente Completo

```javascript
// ============================================
// CONFIGURACIÓN - Modifica estos valores
// ============================================
const CONFIG = {
  ROOT_FOLDER_ID: 'TU_ID_DE_CARPETA_AQUI', // ID de tu carpeta
  CHECK_INTERVAL_MINUTES: 5 // Cada cuántos minutos revisar
};

// ============================================
// FUNCIÓN PRINCIPAL - Se ejecuta automáticamente
// ============================================
function checkNewFiles() {
  const scriptProperties = PropertiesService.getScriptProperties();
  const lastCheck = scriptProperties.getProperty('lastCheck');
  const lastCheckDate = lastCheck ? new Date(lastCheck) : new Date(Date.now() - 60000);
  
  console.log('Ultimo check: ' + lastCheckDate.toISOString());
  
  const now = new Date();
  scriptProperties.setProperty('lastCheck', now.toISOString());
  
  const allFolderIds = getAllSubfolderIds(CONFIG.ROOT_FOLDER_ID);
  allFolderIds.push(CONFIG.ROOT_FOLDER_ID);
  
  console.log('Carpetas a revisar: ' + allFolderIds.length);
  
  const newFiles = [];
  
  allFolderIds.forEach(folderId => {
    try {
      const folder = DriveApp.getFolderById(folderId);
      const files = folder.getFiles();
      
      while (files.hasNext()) {
        const file = files.next();
        const createdDate = file.getDateCreated();
        
        if (createdDate > lastCheckDate) {
          newFiles.push({
            id: file.getId(),
            name: file.getName(),
            link: file.getUrl(),
            uploadedBy: file.getOwner().getEmail(),
            uploadedByName: file.getOwner().getName(),
            createdTime: createdDate,
            folderName: folder.getName()
          });
        }
      }
    } catch (e) {
      console.log('Error accediendo carpeta ' + folderId + ': ' + e.message);
    }
  });
  
  if (newFiles.length === 0) {
    console.log('No hay archivos nuevos');
    return;
  }
  
  console.log('Archivos nuevos encontrados: ' + newFiles.length);
  newFiles.forEach(f => console.log('  - ' + f.name + ' | Subido por: ' + f.uploadedBy));
  
  const collaborators = getCollaborators(CONFIG.ROOT_FOLDER_ID);
  console.log('Colaboradores encontrados: ' + collaborators.length);
  collaborators.forEach(c => console.log('  - ' + c.email + ' (' + c.role + ')'));
  
  const filesByUploader = {};
  newFiles.forEach(file => {
    if (!filesByUploader[file.uploadedBy]) {
      filesByUploader[file.uploadedBy] = {
        uploaderName: file.uploadedByName,
        files: []
      };
    }
    filesByUploader[file.uploadedBy].files.push(file);
  });
  
  Object.keys(filesByUploader).forEach(uploaderEmail => {
    const data = filesByUploader[uploaderEmail];
    console.log('Procesando archivos de: ' + uploaderEmail);
    
    const recipients = collaborators.filter(c => 
      c.email.toLowerCase() !== uploaderEmail.toLowerCase()
    );
    
    console.log('Destinatarios: ' + recipients.length);
    recipients.forEach(r => console.log('  -> ' + r.email));
    
    if (recipients.length > 0) {
      sendNotificationEmail(recipients, data.files, data.uploaderName);
    } else {
      console.log('No hay destinatarios para notificar');
    }
  });
}

// ============================================
// OBTENER SUBCARPETAS RECURSIVAMENTE
// ============================================
function getAllSubfolderIds(parentFolderId, allIds = []) {
  try {
    const parentFolder = DriveApp.getFolderById(parentFolderId);
    const subfolders = parentFolder.getFolders();
    
    while (subfolders.hasNext()) {
      const subfolder = subfolders.next();
      const subfolderId = subfolder.getId();
      allIds.push(subfolderId);
      getAllSubfolderIds(subfolderId, allIds);
    }
  } catch (e) {
    console.log('Error obteniendo subcarpetas: ' + e.message);
  }
  
  return allIds;
}

// ============================================
// OBTENER TODOS LOS COLABORADORES
// ============================================
function getCollaborators(folderId) {
  const collaborators = [];
  const addedEmails = new Set();
  
  try {
    const folder = DriveApp.getFolderById(folderId);
    const editors = folder.getEditors();
    const viewers = folder.getViewers();
    const owner = folder.getOwner();
    
    if (owner) {
      collaborators.push({
        email: owner.getEmail(),
        name: owner.getName() || owner.getEmail().split('@')[0],
        role: 'owner'
      });
      addedEmails.add(owner.getEmail().toLowerCase());
    }
    
    editors.forEach(user => {
      const email = user.getEmail().toLowerCase();
      if (!addedEmails.has(email)) {
        collaborators.push({
          email: user.getEmail(),
          name: user.getName() || user.getEmail().split('@')[0],
          role: 'editor'
        });
        addedEmails.add(email);
      }
    });
    
    viewers.forEach(user => {
      const email = user.getEmail().toLowerCase();
      if (!addedEmails.has(email)) {
        collaborators.push({
          email: user.getEmail(),
          name: user.getName() || user.getEmail().split('@')[0],
          role: 'viewer'
        });
        addedEmails.add(email);
      }
    });
    
  } catch (e) {
    console.log('Error obteniendo colaboradores: ' + e.message);
  }
  
  return collaborators;
}

// ============================================
// ENVIAR EMAIL DE NOTIFICACIÓN
// ============================================
function sendNotificationEmail(recipients, files, uploaderName) {
  const filesCount = files.length;
  
  const subject = filesCount === 1 
    ? `Nuevo archivo: ${files[0].name}`
    : `${filesCount} nuevos archivos en carpeta compartida`;
  
  const tableRows = files.map(f => `
    <tr>
      <td style="padding: 12px 15px; border-bottom: 1px solid #e0e0e0;">
        <strong>${f.name}</strong><br>
        <span style="color: #888; font-size: 12px;">Carpeta: ${f.folderName}</span>
      </td>
      <td style="padding: 12px 15px; border-bottom: 1px solid #e0e0e0; text-align: center;">
        <a href="${f.link}" style="background-color: #1a73e8; color: white; padding: 10px 20px; text-decoration: none; border-radius: 4px; display: inline-block;">Abrir</a>
      </td>
    </tr>
  `).join('');
  
  const allEmails = recipients.map(r => r.email);
  
  const htmlBody = `
  <div style="font-family: 'Segoe UI', Arial, sans-serif; max-width: 600px; margin: 0 auto; background-color: #f5f5f5; padding: 20px;">
    <div style="background-color: #ffffff; border-radius: 8px; overflow: hidden; box-shadow: 0 2px 10px rgba(0,0,0,0.1);">
      
      <div style="background-color: #1a73e8; padding: 25px; text-align: center;">
        <h1 style="color: white; margin: 0; font-size: 22px;">Nuevo${filesCount > 1 ? 's' : ''} Archivo${filesCount > 1 ? 's' : ''}</h1>
      </div>
      
      <div style="padding: 30px;">
        <p style="color: #333; font-size: 16px; margin-top: 0;">Hola,</p>
        
        <p style="color: #555; font-size: 15px; line-height: 1.6;">
          <strong>${uploaderName}</strong> ha subido ${filesCount} archivo${filesCount > 1 ? 's' : ''} a la carpeta compartida:
        </p>
        
        <table style="width: 100%; border-collapse: collapse; margin: 20px 0; background-color: #fafafa; border-radius: 6px; overflow: hidden;">
          <thead>
            <tr style="background-color: #f0f0f0;">
              <th style="padding: 12px 15px; text-align: left; color: #333; font-weight: 600;">Archivo</th>
              <th style="padding: 12px 15px; text-align: center; color: #333; font-weight: 600;">Accion</th>
            </tr>
          </thead>
          <tbody>
            ${tableRows}
          </tbody>
        </table>
        
      </div>
      
      <div style="background-color: #f9f9f9; padding: 20px; text-align: center; border-top: 1px solid #eee;">
        <p style="color: #999; font-size: 12px; margin: 0;">Este es un mensaje automatico del sistema de notificaciones.</p>
      </div>
      
    </div>
  </div>`;
  
  try {
    GmailApp.sendEmail(allEmails.join(','), subject, '', {
      htmlBody: htmlBody,
      name: uploaderName
    });
    console.log('Email enviado a: ' + allEmails.join(', '));
  } catch (e) {
    console.log('Error enviando email: ' + e.message);
  }
}

// ============================================
// CONFIGURAR TRIGGER AUTOMÁTICO
// ============================================
function createTrigger() {
  const triggers = ScriptApp.getProjectTriggers();
  triggers.forEach(trigger => {
    if (trigger.getHandlerFunction() === 'checkNewFiles') {
      ScriptApp.deleteTrigger(trigger);
    }
  });
  
  ScriptApp.newTrigger('checkNewFiles')
    .timeBased()
    .everyMinutes(CONFIG.CHECK_INTERVAL_MINUTES)
    .create();
  
  console.log('Trigger creado: cada ' + CONFIG.CHECK_INTERVAL_MINUTES + ' minuto(s)');
}

// ============================================
// ELIMINAR TRIGGER
// ============================================
function deleteTrigger() {
  const triggers = ScriptApp.getProjectTriggers();
  triggers.forEach(trigger => {
    if (trigger.getHandlerFunction() === 'checkNewFiles') {
      ScriptApp.deleteTrigger(trigger);
      console.log('Trigger eliminado');
    }
  });
}

// ============================================
// FUNCIÓN DE PRUEBA
// ============================================
function testNotification() {
  const scriptProperties = PropertiesService.getScriptProperties();
  scriptProperties.setProperty('lastCheck', new Date(Date.now() - 3600000).toISOString());
  checkNewFiles();
}

// ============================================
// DEBUG - Ver colaboradores
// ============================================
function debugCollaborators() {
  const folderId = CONFIG.ROOT_FOLDER_ID;
  const folder = DriveApp.getFolderById(folderId);
  
  console.log('=== INFORMACION DE LA CARPETA ===');
  console.log('Nombre: ' + folder.getName());
  console.log('Owner: ' + folder.getOwner().getEmail());
  
  console.log('\n=== EDITORES ===');
  folder.getEditors().forEach(user => {
    console.log('- ' + user.getEmail());
  });
  
  console.log('\n=== VIEWERS ===');
  folder.getViewers().forEach(user => {
    console.log('- ' + user.getEmail());
  });
  
  console.log('\n=== TODOS LOS COLABORADORES ===');
  const collaborators = getCollaborators(folderId);
  collaborators.forEach(c => {
    console.log('- ' + c.email + ' (' + c.role + ')');
  });
}
```

---

## 📞 Soporte

Si tienes problemas:

1. Revisa los logs en **Ver → Registros de ejecución**
2. Verifica que el trigger esté activo en **⏰ Activadores**
3. Ejecuta `debugCollaborators` para verificar permisos

---

## 📝 Historial de Cambios

| Versión | Fecha    | Cambios         |
| ------- | -------- | --------------- |
| 1.0     | Dic 2025 | Versión inicial |

---

> **Nota:** Este documento fue generado como guía de implementación. Guárdalo en un lugar seguro para futuras referencias.
