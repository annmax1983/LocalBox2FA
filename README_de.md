# LocalBox2FA

[English](README.md) | [中文](README_zh.md) | [Español](README_es.md) | Deutsch | [日本語](README_ja.md) | [Français](README_fr.md)

Ein leichtgewichtiger Browsererweiterung zur lokalen Generierung von TOTP 2FA-Bestätigungscodes — ohne Upload, komplett offline.

> Chromium-basiert · Manifest V3 · 100% Offline · Datenschutz zuerst

---

## Warum LocalBox2FA?

Die meisten 2FA-Authentifikatoren erfordern eine Handy-App oder Cloud-Synchronisierung. LocalBox2FA läuft direkt in Ihrem Browser — kein Handy nötig, kein Konto erforderlich, keine Daten verlassen Ihr Gerät.

| Vorteil | Detail |
|---------|--------|
| 🔒 **100% Lokal** | Alle TOTP-Berechnungen erfolgen im Browser über die Web Crypto API. Kein Upload. |
| 📱 **Kein Handy nötig** | 2FA-Codes direkt in der Browser-Symbolleiste generieren |
| 🚫 **Kein Konto** | Keine Registrierung, keine Cloud-Sync, kein Login. Installieren und nutzen. |
| ⚡ **Sofort** | Codes in unter 10ms generiert. Ein Klick zum Kopieren. |
| 🌙 **Dark Mode** | Folgt automatisch der System-Dark-Mode-Einstellung |
| 🎯 **Minimal** | Unter 50KB. Keine Frameworks, keine Abhängigkeiten |

---

## Funktionen

| Funktion | Beschreibung |
|----------|-------------|
| 🔐 **TOTP-Code-Generierung** | RFC 6238-kompatibel — funktioniert mit Google Authenticator, Authy und allen TOTP-Diensten |
| ⏱️ **30s Countdown** | Visueller Fortschrittsbalken mit Farbverlauf (Blau → Orange → Rot) |
| 📋 **Ein-Klick-Kopie** | Bestätigungscode sofort in die Zwischenablage kopieren |
| 💾 **Speichern & Verwalten** | Secret-Keys mit benutzerdefinierten Namen speichern |
| 📋 **Live-Verlauf** | Alle gespeicherten Konten zeigen Echtzeit-Codes und Countdown |
| 📤 **Export** | Alle Secrets als Textdatei exportieren (Name:Secret Format) |
| 🗑️ **Sicheres Löschen** | Bestätigungsdialog vor dem Löschen |
| 🔒 **Duplikat-Schutz** | Verhindert doppelte Speicherung desselben Secret-Keys |
| 🌙 **Dark Mode** | Automatisches Dark/Light-Theme basierend auf Systemeinstellung |
| 🌍 **6 Sprachen** | Englisch, Chinesisch, Japanisch, Spanisch, Deutsch, Französisch |

---

## Unterstützte Browser

| Browser | Status |
|---------|--------|
| Google Chrome | ✅ Vollständig unterstützt |
| Microsoft Edge | ✅ Vollständig unterstützt |
| Andere Chromium-basierte | ✅ Sollte funktionieren |

---

## Installation

1. Öffnen Sie die Browsererweiterungsseite:
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
2. Aktivieren Sie den **Entwicklermodus** (oben rechts)
3. Klicken Sie auf **Entpackte Erweiterung laden** und wählen Sie den `local-box2-fa` Ordner
4. Klicken Sie auf das 🔐 LocalBox2FA-Symbol in der Symbolleiste

---

## Verwendung

### Code generieren

1. Klicken Sie auf das LocalBox2FA-Symbol
2. Fügen Sie Ihren TOTP Secret-Key (Base32-Format) ein
3. Klicken Sie auf **Generieren** — ein 6-stelliger Code mit 30s Countdown erscheint
4. Klicken Sie auf **Kopieren** um den Code in die Zwischenablage zu kopieren

### Im Verlauf speichern

1. Nach der Codegenerierung klicken Sie auf **Speichern**
2. Geben Sie einen Namen ein (z.B. „GitHub", „Google")
3. Das Konto erscheint in Ihrer Verlaufsliste mit Live-Code

### Gespeicherte Konten verwenden

- Alle gespeicherten Konten zeigen Echtzeit-Codes und Countdown
- Klicken Sie auf ein Konto um seinen Code zu laden
- Codes werden alle 30 Sekunden automatisch aktualisiert

---

## So funktioniert es

```
Secret-Key eingeben (Base32)
       ↓
Web Crypto API berechnet HMAC-SHA1
       ↓
6-stelliger TOTP-Code wird generiert (RFC 6238)
       ↓
30-Sekunden-Countdown mit Auto-Refresh
       ↓
Ein-Klick-Kopie in die Zwischenablage
```

Alle Berechnungen erfolgen lokal über die Web Crypto API des Browsers. Keine Netzwerkanfragen, kein Daten-Upload.

---

## Datenschutz

- ✅ **Kein Daten-Upload** — Alle TOTP-Berechnungen erfolgen lokal
- ✅ **Keine Analysen** — Kein Tracking, keine Telemetrie
- ✅ **Keine Netzwerkanfragen** — Erweiterung arbeitet komplett offline
- ✅ **Nur lokale Speicherung** — Secrets im Browser-localStorage gespeichert
- ✅ **Keine Berechtigungen** — Manifest erklärt keine Berechtigungen

---

## Lizenz

Copyright © 2026 LocalBox2FA. Alle Rechte vorbehalten.

---

## ❤️ Unterstützung

Wenn Ihnen LocalBox2FA hilft, erwägen Sie bitte eine Unterstützung!

**[👉 LocalBox2FA unterstützen](https://annmax1983.github.io/LocalBox2FA/)**
