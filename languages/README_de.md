# LocalBox2FA

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | Deutsch | [日本語](README_ja.md) | [Français](README_fr.md)

Eine schlanke Browser-Erweiterung zur Generierung von TOTP-2FA-Bestätigungscodes — deine Secrets werden komplett auf deinem Gerät generiert und gespeichert.

> Chromium-basiert · Manifest V3 · Lokale Verarbeitung · Datenschutz zuerst

---

## Warum LocalBox2FA?

Die meisten 2FA-Authentifikatoren benötigen eine Handy-App oder Cloud-Synchronisierung. LocalBox2FA läuft direkt in deinem Browser — kein Handy nötig, kein Konto erforderlich, und deine Secrets verlassen nie deinen Rechner.

| Vorteil | Details |
|---------|---------|
| 🔒 **Nur lokal** | Die gesamte TOTP-Berechnung läuft in deinem Browser über die Web Crypto API. Secrets verlassen nie dein Gerät. |
| 📱 **Kein Handy nötig** | 2FA-Codes direkt aus deiner Browser-Toolbar generieren — keine mobile App erforderlich. |
| 🚫 **Kein Konto** | Keine Registrierung, keine Cloud-Sync, kein Login. Einfach installieren und nutzen. |
| ⚡ **Sofort** | Codes werden in unter 10ms generiert. Ein Klick zum Kopieren in die Zwischenablage. |
| 🌙 **Dark Mode** | Folgt automatisch deiner System-Dark-Mode-Einstellung. |
| 🎯 **Minimal** | Keine Frameworks, keine Abhängigkeiten, kein Ballast. |

---

## Funktionen

### 🆓 Kostenlos

| Funktion | Beschreibung |
|----------|--------------|
| 🔐 **TOTP-Codegenerierung** | RFC 6238 kompatibel — akzeptiert Secret Keys von Google Authenticator, Authy und allen Standard-TOTP-Diensten |
| ⏱️ **30s Countdown** | Visuelle Fortschrittsanzeige mit Farbübergängen (Blau → Orange → Rot) |
| 📋 **Ein-Klick-Kopie** | Bestätigungscode sofort in die Zwischenablage kopieren |
| 💾 **Speichern & Verwalten** | Secret Keys mit benutzerdefinierten Namen speichern, jederzeit per Klick laden |
| 📋 **Live-Verlauf** | Alle gespeicherten Konten zeigen Echtzeit-Codes und Countdown-Timer |
| 🗑️ **Einzelnen Eintrag löschen** | Einzelne Einträge mit Bestätigungsdialog entfernen |
| 🔒 **Duplikat-Schutz** | Verhindert das doppelte Speichern desselben Secret Keys |
| 🌙 **Dark Mode** | Automatisches helles/dunkles Theme basierend auf Systemeinstellung |
| 🌍 **6 Sprachen** | Englisch, Chinesisch, Japanisch, Spanisch, Deutsch, Französisch |

### ⭐ Premium (Lizenz erforderlich)

| Funktion | Beschreibung |
|----------|--------------|
| 📤 **Einträge exportieren** | Alle Secrets als Textdatei (Name:Secret-Format) für Backup exportieren |
| 🗑️ **Alle Einträge löschen** | Alle gespeicherten Einträge auf einmal massenhaft löschen |

> 💡 Einmaliger Kauf, gerätegebundene Lizenz. [Lizenz erhalten →](https://www.annmax1983.com/checkout.html?plugin=localbox2fa)

---

## Kompatibilitätshinweis

Diese Erweiterung entspricht dem RFC 6238 TOTP-Standard und unterstützt Secret Keys, die von Google Authenticator, Authy und anderen gängigen 2FA-Tools generiert werden. Es ist ein unabhängiges Tool und hat keine offizielle Verbindung zu den genannten Marken.

---

## Vorschau

<p align="center">
  <img src="images/A02.png" alt="LocalBox2FA Vorschau">
</p>

---

## Unterstützte Browser

| Browser | Status |
|---------|--------|
| Google Chrome | ✅ Vollständig unterstützt |
| Microsoft Edge | ✅ Vollständig unterstützt |
| Andere Chromium-basierte Browser | ✅ Sollte funktionieren |

---

## Installation

1. Öffne die Erweiterungsseite deines Browsers:
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
2. Aktiviere den **Entwicklermodus** (Schalter oben rechts)
3. Klicke auf **Entpackte Erweiterung laden** und wähle den Ordner `local-box2-fa`
4. Klicke auf das 🔐 LocalBox2FA-Symbol in deiner Toolbar zum Starten

---

## Verwendung

### Einen Code generieren

1. Klicke auf das LocalBox2FA-Symbol in deiner Toolbar
2. Füge deinen TOTP Secret Key (Base32-Format) ins Eingabefeld ein
3. Klicke auf **Generieren** — ein 6-stelliger Code erscheint mit 30s Countdown
4. Klicke auf **Kopieren**, um den Code in die Zwischenablage zu kopieren

### Im Verlauf speichern

1. Nach der Codegenerierung klicke auf **Speichern**
2. Gib einen Namen ein (z.B. „GitHub", „Google")
3. Das Konto erscheint in deiner Verlaufsliste mit einem Live-Code

### Gespeicherte Konten verwenden

- Alle gespeicherten Konten zeigen Echtzeit-Codes und Countdown-Timer
- Klicke auf ein beliebiges Konto, um seinen Code in die Hauptanzeige zu laden
- Codes werden alle 30 Sekunden automatisch aktualisiert

### Exportieren & Sichern

- Klicke auf **Exportieren**, um alle gespeicherten Secrets als `.txt`-Datei herunterzuladen
- Format: `Kontoname:SecretKey` (einer pro Zeile)
- Bewahre diese Datei sicher auf — sie enthält deine Secret Keys

---

## So funktioniert es

```
Secret Key eingeben (Base32)
       ↓
Web Crypto API berechnet HMAC-SHA1
       ↓
Generiert 6-stelligen TOTP-Code (RFC 6238)
       ↓
30-Sekunden-Countdown mit Auto-Refresh
       ↓
Ein-Klick-Kopie in die Zwischenablage
```

Die gesamte Berechnung passiert lokal über die Web Crypto API des Browsers. Deine Secrets lösen nie eine Netzwerkanfrage aus.

---

## Datenschutz

LocalBox2FA wurde mit Datenschutz als Grundprinzip entwickelt:

- ✅ **Secrets bleiben auf deinem Gerät** — Die gesamte TOTP-Berechnung passiert lokal; gespeicherte Secrets verlassen nie deinen Browser
- ✅ **Keine Analytik** — Kein Tracking, keine Telemetrie, keine Cookies
- ✅ **Netzwerk nur für Lizenzaktivierung** — Bei Aktivierung einer Premium-Lizenz werden dein Lizenzschlüssel und eine minimale Geräteidentifikation an den Lizenzserver gesendet, um sie zu verifizieren. Kostenlose Funktionen funktionieren vollständig offline und lösen nie eine Netzwerkanfrage aus.
- ✅ **Minimale Berechtigungen** — `storage` (zum Speichern deines Lizenzstatus) und Zugriff auf die Lizenzserver-Domain

---

## ⚠️ Sicherheitshinweise

**Bitte vor der Nutzung sorgfältig lesen:**

- **🔑 Klartext-Speicherung** — Secret Keys werden im Browser-`localStorage` **ohne Verschlüsselung** gespeichert. Jeder mit Zugang zu deinem Browserprofil kann alle gespeicherten Schlüssel einsehen.
- **💾 Daten löschen = Datenverlust** — Das Löschen des Browser-Caches oder der Seiten-Daten **löscht dauerhaft** alle gespeicherten Konten. Bitte exportiere vorher eine Backup-Datei.
- **📄 Export-Datei ist unverschlüsselt** — Die exportierte `.txt`-Backup-Datei enthält Klartext-Secret Keys. Bewahre sie sicher auf und vermeide öffentliche Weitergabe.
- **🛡️ Best Practice** — Lösche gespeicherte Secrets aus der Erweiterung, nachdem du sie in eine dedizierte Authentifikator-App übertragen hast.

---

## Quellcode-Hinweis

> ⚠️ **Dieses Repository veröffentlicht keinen Quellcode.** Es enthält nur Nutzerdokumentation, Versionshinweise und Support-Ressourcen. Die Erweiterung wird ausschließlich über den Chrome Web Store vertrieben. Es werden keine Offline-Installationspakete oder Endbenutzer-Quellcodes bereitgestellt.

---

## Lizenz

Copyright © 2026 LocalBox2FA. Alle Rechte vorbehalten.

---

## ❤️ Support

Wenn dir LocalBox2FA hilft, unterstütze das Projekt gerne!

**[👉 LocalBox2FA unterstützen](https://annmax1983.github.io/LocalBox2FA/)**
