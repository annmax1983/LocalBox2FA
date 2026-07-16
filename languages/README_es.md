# LocalBox2FA
[English](../README.md) | [中文](README_zh.md) | Español | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

Una extensión ligera del navegador que genera códigos TOTP 2FA localmente — sin subida de datos, completamente offline.

> Basado en Chromium · Manifest V3 · Completamente sin conexión · Privacidad primero

---

## ¿Por qué LocalBox2FA?

La mayoría de autenticadores 2FA requieren una app móvil o sincronización en la nube. LocalBox2FA se ejecuta directamente en tu navegador — sin necesidad de teléfono, sin cuenta requerida, tus datos nunca salen de tu dispositivo.

| Ventaja | Detalle |
|---------|---------|
| 🔒 **Completamente local** | Todo el cálculo TOTP ocurre en tu navegador con la API Web Crypto. Sin subida. |
| 📱 **Sin Teléfono** | Genera códigos 2FA directamente desde la barra de herramientas |
| 🚫 **Sin Cuenta** | Sin registro, sin sincronización, sin login. Instala y usa. |
| ⚡ **Instantáneo** | Códigos generados en menos de 10ms. Un clic para copiar. |
| 🌙 **Modo Oscuro** | Sigue automáticamente la preferencia de modo oscuro del sistema |
| 🎯 **Mínimo** | Menos de 50KB. Sin frameworks, sin dependencias |

---

## Características

| Característica | Descripción |
|----------------|-------------|
| 🔐 **Generación TOTP** | Compatible con RFC 6238 — funciona con Google Authenticator, Authy y todos los servicios TOTP |
| ⏱️ **30s Countdown** | Barra de progreso visual con transiciones de color (azul → naranja → rojo) |
| 📋 **Copia con Un Clic** | Copia el código de verificación al portapapeles instantáneamente |
| 💾 **Guardar y Gestionar** | Guarda claves secretas con nombres personalizados |
| 📋 **Historial en Vivo** | Todas las cuentas guardadas muestran códigos en tiempo real |
| 📤 **Exportar** | Exporta todas las claves como archivo de texto (formato nombre:clave) |
| 🗑️ **Eliminación Segura** | Diálogo de confirmación antes de eliminar registros |
| 🔒 **Anti-Duplicados** | Evita guardar la misma clave secreta dos veces |
| 🌙 **Modo Oscuro** | Tema automático según la preferencia del sistema |
| 🌍 **6 Idiomas** | Inglés, Chino, Japonés, Español, Alemán, Francés |

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

Todo el cálculo ocurre localmente usando la Web Crypto API del navegador. Sin solicitudes de red, sin subida de datos.

---

## Privacidad

- ✅ **Sin subida de datos** — Todo el cálculo TOTP ocurre localmente
- ✅ **Sin análisis** — Sin rastreo, sin telemetría
- ✅ **Sin solicitudes de red** — La extensión funciona completamente offline
- ✅ **Solo almacenamiento local** — Secretos guardados en localStorage del navegador
- ✅ **Sin permisos** — El manifest no declara permisos

---

## Licencia

Copyright © 2026 LocalBox2FA. Todos los derechos reservados.

---

## ❤️ Apoyo

¡Si LocalBox2FA te resulta útil, considera apoyar el proyecto!

**[👉 Apoyar LocalBox2FA](https://annmax1983.github.io/LocalBox2FA/)**
