# LocalBox2FA

[English](../README.md) | [中文](README_zh.md) | Español | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

Una extensión ligera para el navegador que genera códigos de verificación TOTP 2FA — tus secretos se generan y almacenan completamente en tu dispositivo.

> Basada en Chromium · Manifest V3 · Procesamiento local · Privacidad ante todo

---

## ¿Por qué LocalBox2FA?

La mayoría de aplicaciones de autenticación 2FA requieren una app en el móvil o sincronización en la nube. LocalBox2FA se ejecuta directamente en tu navegador — sin necesidad de móvil, sin cuenta requerida y tus secretos nunca salen de tu máquina.

| Ventaja | Detalle |
|---------|--------|
| 🔒 **Solo local** | Todo el cálculo TOTP ocurre en tu navegador usando la Web Crypto API. Los secretos nunca salen de tu dispositivo. |
| 📱 **Sin necesidad de móvil** | Genera códigos 2FA directamente desde la barra de herramientas de tu navegador — sin app móvil necesaria. |
| 🚫 **Sin cuenta** | Sin registro, sin sincronización en la nube, sin inicio de sesión. Instala y usa. |
| ⚡ **Instantáneo** | Los códigos se generan en menos de 10 ms. Un clic para copiar al portapapeles. |
| 🌙 **Modo oscuro** | Sigue automáticamente la preferencia de modo oscuro de tu sistema. |
| 🎯 **Mínima** | Sin frameworks, sin dependencias, sin peso muerto. |

---

## Funcionalidades

### 🆓 Gratis

| Funcionalidad | Descripción |
|---------|-------------|
| 🔐 **Generación de códigos TOTP** | Compatible con RFC 6238 — acepta claves secretas de Google Authenticator, Authy y todos los servicios TOTP estándar |
| ⏱️ **Cuenta atrás de 30s** | Barra de progreso visual con transiciones de color (azul → naranja → rojo) |
| 📋 **Copia con un clic** | Copia el código de verificación al portapapeles al instante |
| 💾 **Guardar y gestionar** | Guarda claves secretas con nombres personalizados, haz clic para recargar en cualquier momento |
| 📋 **Historial en vivo** | Todas las cuentas guardadas muestran códigos en tiempo real y temporizadores de cuenta atrás |
| 🔎 **Buscar y renombrar** | Encuentra cualquier cuenta al instante, renómbralas cuando quieras |
| 🗑️ **Eliminar registro individual** | Elimina registros individuales con diálogo de confirmación |
| 🔒 **Protección contra duplicados** | Evita guardar la misma clave secreta dos veces |
| 🌙 **Modo oscuro** | Tema oscuro/claro automático según la preferencia del sistema |
| 🌍 **6 idiomas** | Inglés, chino, japonés, español, alemán y francés |

### ⭐ Premium (Requiere licencia)

| Funcionalidad | Descripción |
|---------|-------------|
| 📤 **Exportar registros** | Exporta todos los secretos como archivo de texto (formato nombre:secreto) para respaldo |
| 🗑️ **Borrar todos los registros** | Elimina masivamente todos los registros guardados de una vez |
| 📥 **Importar registros** | Restaura cuentas desde un archivo de texto de respaldo |
| 📱 **Mostrar código QR** | Código QR escaneable para transferir cuentas a tu app de autenticación |

> 💡 Compra única, licencia vinculada al dispositivo. [Obtener licencia →](https://www.annmax1983.com/checkout.html?plugin=localbox2fa)

---

## Aviso de compatibilidad

Esta extensión cumple con el estándar TOTP RFC 6238 y soporta claves secretas generadas por Google Authenticator, Authy y otras herramientas 2FA principales. Es una herramienta independiente y no tiene afiliación oficial con las marcas mencionadas.

---

## Vista previa

<p align="center">
  <img src="images/A02.png" alt="Vista previa de LocalBox2FA">
</p>

---

## Navegadores compatibles

| Navegador | Estado |
|---------|--------|
| Google Chrome | ✅ Totalmente compatible |
| Microsoft Edge | ✅ Totalmente compatible |
| Otros navegadores basados en Chromium | ✅ Debería funcionar |

---

## Instalación

1. Abre la página de extensiones de tu navegador:
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
2. Activa el **modo de desarrollador** (interruptor arriba a la derecha)
3. Haz clic en **Cargar descomprimida** y selecciona la carpeta `local-box2-fa`
4. Haz clic en el icono 🔐 de LocalBox2FA en tu barra de herramientas para empezar

---

## Uso

### Generar un código

1. Haz clic en el icono de LocalBox2FA en tu barra de herramientas
2. Pega tu clave secreta TOTP (formato Base32) en el campo de entrada
3. Haz clic en **Generar** — aparece un código de 6 dígitos con una cuenta atrás de 30s
4. Haz clic en **Copiar** para copiar el código al portapapeles

### Guardar en el historial

1. Después de generar un código, haz clic en **Guardar**
2. Introduce un nombre (ej. "GitHub", "Google")
3. La cuenta aparece en tu lista de historial con un código en vivo

### Usar cuentas guardadas

- Todas las cuentas guardadas muestran códigos en tiempo real y temporizadores de cuenta atrás
- Haz clic en cualquier cuenta para cargar su código en la visualización principal
- Los códigos se actualizan automáticamente cada 30 segundos

### Exportar y respaldar

- Haz clic en **Exportar** para descargar todos los secretos guardados como archivo `.txt`
- Formato: `NombreCuenta:ClaveSecreta` (una por línea)
- Guarda este archivo en un lugar seguro — contiene tus claves secretas

---

## Cómo funciona

```
Introducir clave secreta (Base32)
       ↓
La Web Crypto API calcula HMAC-SHA1
       ↓
Genera código TOTP de 6 dígitos (RFC 6238)
       ↓
Cuenta atrás de 30 segundos con auto-actualización
       ↓
Copia al portapapeles con un clic
```

Todo el cálculo ocurre localmente usando la Web Crypto API del navegador. Tus secretos nunca realizan una solicitud de red.

---

## Privacidad

LocalBox2FA está construida con la privacidad como principio fundamental:

- ✅ **Los secretos se quedan en tu dispositivo** — Todo el cálculo TOTP ocurre localmente; los secretos guardados nunca salen de tu navegador
- ✅ **Sin analíticas** — Sin rastreo, sin telemetría, sin cookies
- ✅ **Red solo para activación de licencia** — Si activas una licencia Premium, tu clave de licencia y un identificador mínimo de dispositivo se envían al servidor de licencias para verificarla. Las funcionalidades gratuitas funcionan completamente sin conexión y nunca realizan solicitudes de red.
- ✅ **Permisos mínimos** — `storage` (para recordar el estado de tu licencia) y acceso al dominio del servidor de licencias únicamente

---

## ⚠️ Notas de seguridad

**Por favor, lee atentamente antes de usar:**

- **🔑 Almacenamiento en texto plano** — Las claves secretas se almacenan en el almacenamiento de la extensión (`chrome.storage.local`) **sin cifrar**. Cualquiera con acceso a tu perfil de navegador puede ver todas las claves guardadas.
- **💾 Eliminar la extensión = pérdida de datos** — Desinstalar la extensión o borrar sus datos **eliminará permanentemente** todas las cuentas guardadas. Por favor, exporta un archivo de respaldo con antelación.
- **📄 El archivo de exportación no está cifrado** — El archivo `.txt` de respaldo exportado contiene claves secretas en texto plano. Guárdalo de forma segura y evita compartirlo públicamente.
- **🛡️ Mejores prácticas** — Elimina los secretos guardados de la extensión después de transferirlos a una aplicación de autenticación dedicada.

---

## Aviso sobre el código fuente

> ⚠️ **Este repositorio no publica código fuente.** Contiene únicamente documentación de uso, notas de lanzamiento y recursos de soporte. La extensión se distribuye exclusivamente a través de Chrome Web Store. No se proporcionan paquetes de instalación sin conexión ni código fuente para usuarios finales.

---

## Licencia

Copyright © 2026 LocalBox2FA. Todos los derechos reservados.

---

## ❤️ Apoyo

Si te resulta útil LocalBox2FA, ¡considera apoyar el proyecto!

**[👉 Apoyar LocalBox2FA](https://annmax1983.github.io/LocalBox2FA/)**
