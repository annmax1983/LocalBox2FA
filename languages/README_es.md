# LocalBox2FA
[English](../README.md) | [中文](README_zh.md) | Español | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

Una extensión ligera del navegador que genera códigos TOTP 2FA localmente — sus secretos permanecen por completo en su dispositivo.

> Basado en Chromium · Manifest V3 · Procesamiento local · Privacidad primero

---

## ¿Por qué LocalBox2FA?

La mayoría de autenticadores 2FA requieren una app móvil o sincronización en la nube. LocalBox2FA se ejecuta directamente en tu navegador — sin necesidad de teléfono, sin cuenta requerida, tus datos nunca salen de tu dispositivo.

| Ventaja | Detalle |
|---------|---------|
| 🔒 **Completamente local** | Todo el cálculo TOTP ocurre en tu navegador con la API Web Crypto. Los secretos nunca salen de tu dispositivo. |
| 📱 **Sin Teléfono** | Genera códigos 2FA directamente desde la barra de herramientas |
| 🚫 **Sin Cuenta** | Sin registro, sin sincronización, sin login. Instala y usa. |
| ⚡ **Instantáneo** | Códigos generados en menos de 10ms. Un clic para copiar. |
| 🌙 **Modo Oscuro** | Sigue automáticamente la preferencia de modo oscuro del sistema |
| 🎯 **Mínimo** | Sin frameworks, sin dependencias, sin peso extra. |

---

## Características

### 🆓 Funciones Gratuitas

| Característica | Descripción |
|----------------|-------------|
| 🔐 **Generación TOTP** | Compatible con RFC 6238 — funciona con Google Authenticator, Authy y todos los servicios TOTP |
| ⏱️ **30s Countdown** | Barra de progreso visual con transiciones de color (azul → naranja → rojo) |
| 📋 **Copia con Un Clic** | Copia el código de verificación al portapapeles instantáneamente |
| 💾 **Guardar y Gestionar** | Guarda claves secretas con nombres personalizados |
| 📋 **Historial en Vivo** | Todas las cuentas guardadas muestran códigos en tiempo real |
| 🗑️ **Eliminar Registro Individual** | Diálogo de confirmación antes de eliminar registros |
| 🔒 **Anti-Duplicados** | Evita guardar la misma clave secreta dos veces |
| 🌙 **Modo Oscuro** | Tema automático según la preferencia del sistema |
| 🌍 **6 Idiomas** | Inglés, Chino, Japonés, Español, Alemán, Francés |

### ⭐ Funciones Premium (Licencia Requerida)

| Característica | Descripción |
|----------------|-------------|
| 📤 **Exportar Registros** | Exporta todas las claves como archivo de texto para respaldo |
| 🗑️ **Limpiar Todos los Registros** | Eliminar todos los registros guardados a la vez |

> 💡 Compra única, licencia vinculada al dispositivo. [Obtener Licencia →](https://www.annmax1983.com/checkout.html?plugin=localbox2fa)

---



## Preview

<p align="center">
  <img src="images/A02.png" alt="LocalBox2FA Preview">
</p>



## Navegadores Compatibles

| Navegador | Estado |
|-----------|--------|
| Google Chrome | ✅ Totalmente compatible |
| Microsoft Edge | ✅ Totalmente compatible |
| Otros Chromium | ✅ Debería funcionar |

---

## Instalación

1. Abre la página de extensiones del navegador:
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
2. Activa el **Modo desarrollador** (esquina superior derecha)
3. Haz clic en **Cargar desempaquetado** y selecciona la carpeta `local-box2-fa`
4. Haz clic en el ícono 🔐 LocalBox2FA en la barra de herramientas

---

## Uso

### Generar un Código

1. Haz clic en el ícono de LocalBox2FA
2. Pega tu clave secreta TOTP (formato Base32) en el campo de entrada
3. Haz clic en **Generar** — aparece un código de 6 dígitos con countdown de 30s
4. Haz clic en **Copiar** para copiar el código al portapapeles

### Guardar en Historial

1. Después de generar un código, haz clic en **Guardar**
2. Ingresa un nombre (ej: "GitHub", "Google")
3. La cuenta aparece en tu lista de historial con código en vivo

### Usar Cuentas Guardadas

- Todas las cuentas guardadas muestran códigos en tiempo real
- Haz clic en cualquier cuenta para cargar su código
- Los códigos se actualizan automáticamente cada 30 segundos

---

## Cómo Funciona

```
Ingresar clave secreta (Base32)
       ↓
Web Crypto API calcula HMAC-SHA1
       ↓
Genera código TOTP de 6 dígitos (RFC 6238)
       ↓
30 segundos de countdown con auto-refresh
       ↓
Un clic para copiar al portapapeles
```

Todo el cálculo ocurre localmente usando la Web Crypto API del navegador. Tus secretos nunca se envían a través de la red.

---

## Privacidad

- ✅ **Los secretos permanecen en tu dispositivo** — Todo el cálculo TOTP ocurre localmente; los secretos guardados nunca salen de tu navegador
- ✅ **Sin análisis** — Sin rastreo, sin telemetría, sin cookies
- ✅ **Red solo para la activación de licencia** — Si activas una licencia Premium, tu clave de licencia y un identificador de dispositivo mínimo se envían al servidor de licencias para su verificación. Las funciones gratuitas funcionan completamente sin conexión y no realizan ninguna solicitud de red
- ✅ **Permisos mínimos** — `storage` (para recordar el estado de la licencia) y acceso solo al dominio del servidor de licencias

---

---

## Aviso de código fuente

> ⚠️ **Este repositorio no publica el código fuente.** Contiene únicamente documentación de uso, notas de versión y recursos de soporte. La extensión se distribuye exclusivamente a través de Chrome Web Store. No se proporcionan paquetes de instalación sin conexión ni código fuente para usuarios finales.


## Licencia

Copyright © 2026 LocalBox2FA. Todos los derechos reservados.

---

## ❤️ Apoyo

¡Si LocalBox2FA te resulta útil, considera apoyar el proyecto!

**[👉 Apoyar LocalBox2FA](https://annmax1983.github.io/LocalBox2FA/)**
