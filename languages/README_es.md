# LocalBox2FA

[English](../README.md) | [中文](README_zh.md) | Español | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

Una extensión ligera para el navegador que genera códigos TOTP de doble factor. Los secretos se crean y se usan en tu dispositivo: sin cuenta de la extensión, sin app en el móvil y sin servidores nuestros. Si quieres las mismas cuentas en otro ordenador, la sincronización cifrada opcional puede llevarlas a través de la cuenta de navegador que ya usas.

> Basada en Chromium · Manifest V3 · Procesamiento local · Privacidad ante todo

---

## Funcionalidades

### 🆓 Gratis

| Función | Descripción |
|---------|-------------|
| 🔐 **Códigos TOTP** | RFC 6238. Pega un secreto Base32 o un enlace `otpauth://totp/...` completo. Admite 6–8 dígitos, período personalizado y SHA-1 / SHA-256 / SHA-512 (por defecto: 6 dígitos, 30 s, SHA-1). HOTP no es compatible. |
| ⏱️ **Cuenta atrás en vivo** | Cada cuenta guardada muestra su código y su cuenta atrás, que se renueva al cambiar el período |
| 📋 **Copia con un clic** | Haz clic en una fila o en «Copiar» para poner el código actual en el portapapeles |
| 💾 **Guardar y gestionar** | Pon nombre al guardar, busca en la lista, renombra o elimina entradas |
| 🔒 **Detección de duplicados** | El mismo secreto no se puede guardar dos veces: mayúsculas, espacios y relleno se normalizan antes de comparar |
| 📱 **Transferencia por QR** | Muestra un código QR escaneable para llevar una cuenta a un autenticador del móvil |
| 🗑️ **Borrar todo** | Elimina todas las cuentas guardadas a la vez, tras confirmar |
| 🛡️ **Contraseña maestra** | Cifrado AES-GCM 256 opcional para los secretos guardados. La clave se deriva con PBKDF2-SHA256 (600.000 iteraciones), solo vive en memoria y se pide cada vez que abres la ventana |
| 📤 **Exportar** | Descarga todos los secretos en un archivo `.txt` en texto plano |
| 📥 **Importar** | Restaura cuentas desde ese archivo, una por línea |
| 🌙 **Modo oscuro** | Sigue la preferencia clara/oscura del sistema |
| 🌍 **6 idiomas** | Inglés, chino, japonés, español, alemán, francés |

> Exportar, importar, borrar todo y mostrar el QR son gratuitos. Respaldar, restaurar, borrar y transferir tus propios secretos es higiene de datos, no una función de pago.

### ⭐ Premium (requiere licencia)

| Función | Descripción |
|---------|-------------|
| 🔄 **Sincronización entre dispositivos** | Sincronización opcional de las cuentas guardadas entre dispositivos con la misma cuenta de navegador. Los secretos viajan sellados con tu contraseña maestra; la sincronización se ejecuta mientras la ventana está abierta y solo los conflictos reales te piden elegir |

> Compra única, licencia de por vida: 2 activaciones por plugin. Cada entorno de navegador cuenta como una; puedes desactivar cuando quieras para liberar una plaza. [Obtener licencia →](https://www.annmax1983.com/checkout.html?plugin=localbox2fa)

---

## Vista previa

<p align="center">
  <img src="../images/A02.png" alt="Vista previa de LocalBox2FA">
</p>

---

## Navegadores compatibles

| Navegador | Estado |
|-----------|--------|
| Google Chrome | ✅ Totalmente compatible |
| Microsoft Edge | ✅ Totalmente compatible |
| Otros navegadores basados en Chromium | ✅ Deberían funcionar |

---

## Instalación

1. Abre la página de extensiones de tu navegador:
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
2. Activa el **modo de desarrollador** (interruptor arriba a la derecha)
3. Pulsa **Cargar descomprimida** y elige la carpeta `LocalBox2FA`
4. Pulsa el icono 🔐 de LocalBox2FA en la barra de herramientas

---

## Uso

### Generar un código

1. Pulsa el icono de LocalBox2FA en la barra de herramientas
2. Pega un secreto Base32 o un enlace `otpauth://totp/...` completo en el campo
3. Pulsa **Generar**: el código aparece con su cuenta atrás
4. Pulsa **Copiar** para llevarlo al portapapeles

Un secreto Base32 usa los valores por defecto (6 dígitos, 30 s, SHA-1). Un enlace `otpauth://` completo trae sus propios dígitos, período y algoritmo, necesario para servicios que no usan los valores por defecto.

### Guardar una cuenta

1. Después de generar un código, pulsa **Guardar**
2. Escribe un nombre (por ejemplo «GitHub» o «Google»)
3. La cuenta aparece en la lista con su código y cuenta atrás en vivo

### Usar las cuentas guardadas

- Haz clic en cualquier cuenta para copiar su código actual
- Usa el buscador para filtrar una lista larga
- El icono del lápiz renombra; el icono ✕ elimina tras confirmar
- **Borrar todo**, al pie, elimina todos los registros guardados

### Pasar una cuenta al móvil

Pulsa el icono ▣ de una cuenta guardada para ver un código QR con su enlace `otpauth://`. Escanéalo con un autenticador del móvil para importar la cuenta allí.

### Cifrar tus secretos

Abre **Ajustes (⚙) → Contraseña maestra** y pulsa **Activar cifrado**:

1. Elige una contraseña maestra y confírmala
2. Todos los secretos guardados se sellan al instante; solo los metadatos (nombre, dígitos, período, algoritmo, marcas de tiempo e identificadores aleatorios de registro/dispositivo) siguen legibles
3. A partir de entonces, la pantalla de bloqueo pide la contraseña antes de mostrar cualquier código

Notas:

- La contraseña **no se puede restablecer ni recuperar**. Si la olvidas, la pantalla de bloqueo ofrece borrarlo todo y empezar de nuevo, así que mantén una copia exportada.
- La clave derivada solo vive en memoria y desaparece al cerrar la ventana; por eso se pide en cada apertura.
- Cada secreto sellado está vinculado a su registro: un texto cifrado copiado a otra cuenta no se puede abrir, de modo que una copia sincronizada manipulada no puede apuntar un nombre conocido a otro secreto.
- **Desactivar el cifrado** descifra todos los registros a texto plano. Si algún registro no se puede descifrar, la operación se rechaza, se listan las cuentas afectadas y no se cambia nada: elimínalas primero y reintenta.
- Los registros sellados llevan el prefijo 🔐 en la lista; un registro que no se puede descifrar también muestra 🔐 en lugar de un código.

### Sincronizar entre dispositivos (Premium)

La sincronización lleva las cuentas guardadas entre ordenadores con la misma cuenta de navegador. Permanece **desactivada hasta que la actives**, requiere contraseña maestra y una licencia activa.

**Primer dispositivo**

1. Abre **Ajustes (⚙) → Sincronización entre dispositivos** y pulsa **Activar sincronización**
2. Revisa la pantalla de consentimiento: muestra cuántas cuentas se subirán y qué puede ver el proveedor del navegador
3. Confirma. Los registros se sellan y se escriben en `chrome.storage.sync`

**Segundo dispositivo**

1. Inicia sesión con la misma cuenta en el navegador e instala LocalBox2FA
2. Abre **Ajustes → Sincronización entre dispositivos → Unirse a una sincronización existente**
3. Introduce la **misma contraseña maestra** que en el primer dispositivo

La extensión nunca sincroniza la contraseña ni una clave derivada. El segundo dispositivo solo recibe la sal, el número de iteraciones y el verificador de la bóveda, comprueba la contraseña con ellos y sella los registros locales en texto plano con la misma clave. Una contraseña incorrecta se rechaza antes de fusionar nada.

**Por qué la fusión es segura**

- Cada registro tiene su propia clave de almacenamiento y un ID estable, además de una marca de borrado explícita (tombstone): una clave ausente nunca significa «borrado», y un dispositivo no puede borrar lo que añadió otro escribiendo la lista completa
- Antes de sobrescribir, la extensión vuelve a leer la copia más reciente de la nube; si otro dispositivo la cambió o la borró mientras tanto, la subida se aplaza y la diferencia se plantea como un conflicto real
- Una comparación a tres bandas (último estado sincronizado / local / remoto) aplica automáticamente los cambios sin conflicto
- Si la misma cuenta se modificó de verdad en dos dispositivos, un diálogo te pide conservar **este dispositivo**, **el otro** o **ambos**: nada se sobrescribe sin tu elección
- Un dispositivo con una **contraseña maestra distinta** nunca puede sobrescribir la bóveda sincronizada; informa de un desajuste de bóveda
- Mantén todos los dispositivos que comparten una bóveda en la misma versión de la extensión; una versión anterior puede no reconocer el formato sellado actual y reemplazar registros con copias antiguas

**Notas**

- La sincronización se ejecuta al abrir la ventana (tras desbloquear) y cuando otro dispositivo cambia los datos; no hay botón «Sincronizar ahora»
- Desactivarla conserva la copia en la nube para tus otros dispositivos. Usa **Eliminar datos sincronizados** en el mismo panel para quitarla de la cuenta del navegador; los demás dispositivos conservan sus cuentas locales y desactivan la sincronización al detectar que la copia desapareció
- El cifrado no se puede desactivar mientras la sincronización está activa, porque los registros en texto plano nunca se suben
- La clave de licencia no se sincroniza; cada dispositivo se activa por separado
- Los datos viajan por el servicio de sincronización de tu cuenta de navegador (Google o Microsoft, según el navegador). Los nombres de cuenta y los ajustes TOTP son legibles para ese servicio; los secretos van sellados con AES-GCM y tu contraseña maestra. Si quieres cifrar también el transporte de extremo a extremo, activa la frase de contraseña de sincronización del navegador (Chrome: *Sincronización y servicios de Google → Opciones de cifrado*)
- Se aplican las cuotas de sincronización del navegador (unos 100 KB en total, 8 KB por elemento); la extensión informa de un error de cuota en lugar de descartar registros en silencio

### Exportar e importar

- Pulsa **Exportar** para descargar todos los secretos guardados en un archivo `.txt`
- Cada línea es `NombreDeCuenta:Secreto`, o `NombreDeCuenta:otpauth://…` en cuentas con dígitos, período o algoritmo no predeterminados
- Pulsa **Importar** y elige ese archivo para restaurar cuentas; las líneas ya guardadas se omiten
- El archivo exportado es **texto plano** y no está protegido por tu contraseña maestra

---

## Cómo funciona

```
Introduce un secreto Base32 o un enlace otpauth://
       ↓
Web Crypto API calcula el HMAC (SHA-1 por defecto)
       ↓
Código TOTP de 6–8 dígitos (RFC 6238)
       ↓
Cuenta atrás con renovación automática
       ↓
Copia al portapapeles con un clic
```

Todo el cálculo ocurre en local con la Web Crypto API del navegador. Generar un código nunca hace una petición de red. Los datos guardados solo salen del dispositivo cuando activas expresamente la sincronización cifrada.

---

## Privacidad y permisos

- **Local por defecto** — los secretos guardados viven en `chrome.storage.local` y no salen del dispositivo salvo que actives la sincronización
- **Cifrado opcional** — sin contraseña maestra los secretos están en texto plano. Al activarlo, cada secreto se sella con AES-GCM 256; la clave se deriva de tu contraseña (PBKDF2-SHA256, 600k iteraciones) y solo se guarda en memoria
- **Sincronización opcional** — los registros sellados, los nombres de cuenta, los ajustes TOTP y la sal/iteraciones/verificador de la bóveda se escriben en `chrome.storage.sync` y los transporta tu cuenta de navegador. La contraseña maestra y la clave de licencia nunca se incluyen
- **Sin analítica** — sin rastreo, telemetría, cookies ni scripts de terceros
- **Sin acceso a páginas** — sin content scripts, sin acceso al historial, pestañas o marcadores
- **Red mínima** — sin licencia, la extensión no hace ninguna petición de red, salvo reintentar una liberación de licencia que quedó en cola sin conexión. Con licencia contacta con `api.annmax1983.com` para activar, reverificar (como máximo cada 2 horas al abrir la ventana) y liberar la licencia. Esas peticiones llevan la clave de licencia, un identificador de instalación aleatorio y metadatos del navegador (nombre/versión, idiomas, zona horaria, User-Agent); los secretos y los códigos generados nunca se incluyen
- **Permisos mínimos** — solo `storage`, más acceso al dominio del servidor de licencias. La sincronización no añade permisos ni usa servidores nuestros

El detalle campo por campo está en [privacy-policy.html](../privacy-policy.html).

---

## ⚠️ Notas de seguridad

- **El cifrado es opcional** — de fábrica, los secretos se guardan sin cifrar en el almacenamiento local de la extensión. Cualquiera con acceso a tu perfil de navegador puede leerlos. Activa la contraseña maestra para sellarlos.
- **Sin recuperación de contraseña** — la contraseña maestra no se puede restablecer y los registros sellados no se pueden recuperar sin ella. Si la olvidas, la única opción es borrarlo todo desde la pantalla de bloqueo. Mantén una copia exportada y guárdala bien, porque es texto plano.
- **Quitar la extensión borra los datos locales** — desinstalarla o borrar su almacenamiento local elimina permanentemente todas las cuentas de este dispositivo. Con la sincronización activa queda una copia en tu cuenta de navegador y puede restaurarse reactivando la licencia y uniéndose a la sincronización existente con la misma contraseña maestra; usa antes **Eliminar datos sincronizados** si quieres que desaparezca.
- **La sincronización no es un respaldo** — los borrados se propagan: si borras una cuenta en un dispositivo, se borra en los demás. Mantén una copia exportada de todo lo que no puedas volver a crear.
- **Confianza en la cuenta del navegador** — los datos sincronizados viajan por el servicio de tu proveedor de navegador. Los secretos van sellados con tu contraseña maestra, pero los nombres de cuenta y los ajustes TOTP no. Quien tenga acceso a tu cuenta de navegador *y* a tu contraseña maestra puede leer los secretos; activa la frase de contraseña de sincronización para cifrar también el transporte.
- **Los archivos exportados no están cifrados** — trata el `.txt` como un secreto y no lo compartas.
- **Buena práctica** — elimina un secreto de la extensión cuando ya esté en una app de autenticación dedicada.

---

## Compatibilidad

LocalBox2FA implementa RFC 6238 TOTP y acepta secretos generados por Google Authenticator, Authy y otras herramientas 2FA habituales. Es una herramienta independiente y no tiene relación oficial con esas marcas.

---

## Aviso sobre el código fuente

> ⚠️ **Este repositorio no publica código fuente.** Solo contiene documentación de uso, notas de versión y recursos de soporte. La extensión se distribuye exclusivamente a través de Chrome Web Store; no se ofrece paquete de instalación offline ni código fuente para el usuario final.

---

## Licencia

Copyright © 2026 LocalBox2FA. Todos los derechos reservados.

---

## ❤️ Apoyo

Si LocalBox2FA te resulta útil, ¡puedes apoyar el proyecto!

**[👉 Apoyar LocalBox2FA](https://annmax1983.github.io/LocalBox2FA/)**
