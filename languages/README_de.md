# LocalBox2FA

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | Deutsch | [日本語](README_ja.md) | [Français](README_fr.md)

Eine schlanke Browser-Erweiterung zur Generierung von TOTP-2FA-Bestätigungscodes — deine Secrets werden komplett auf deinem Gerät generiert und gespeichert.

> Chromium-basiert · Manifest V3 · Lokale Verarbeitung · Datenschutz zuerst

---

## Neu in v1.3.0

| Änderung | Details |
|----------|---------|
| 🛡️ **Master-Passwort-Verschlüsselung** | Optional aktivierbare AES-GCM-256-Verschlüsselung für gespeicherte Secrets. Der Schlüssel wird per PBKDF2-SHA256 (600.000 Iterationen + zufälligem Salt) aus Ihrem Passwort abgeleitet und liegt nur im Speicher. Das Passwort wird bei jedem Öffnen des Popups abgefragt |
| 🔓 **Export / Import / Alles löschen jetzt kostenlos** | Die eigenen Secrets zu sichern, wiederherzustellen und zu löschen ist Datenpflege, keine Bezahlfunktion. Premium bleibt nur die QR-Code-Übertragung |
| 📄 **Datenschutzerklärung korrigiert** | Jetzt mit dem tatsächlichen Speicherort (`chrome.storage.local`), den tatsächlichen Netzwerkzeitpunkten (Aktivierung, höchstens eine Nachprüfung pro 2 h beim Öffnen, Deaktivierung) und der tatsächlichen Feldliste |

**Upgrade von v1.2.x? Nichts zu tun.** Von älteren Versionen gespeicherte Einträge bleiben im Klartext und funktionieren unverändert — Liste, Codes, Countdown, Export, Import und Löschen sind nicht betroffen, und der Storage-Key ist unverändert, es wird also nichts neu geschrieben. Ein Eintrag wird erst verschlüsselt, wenn Sie ein Master-Passwort setzen; danach trägt er das Präfix 🔐. Klartext- und verschlüsselte Einträge können in einer Liste koexistieren. Keine Migration, kein Reset, keine Neueingabe.

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
| 🔎 **Suchen & Umbenennen** | Finde jedes Konto sofort, benenne Konten jederzeit um |
| 🗑️ **Einzelnen Eintrag löschen** | Einzelne Einträge mit Bestätigungsdialog entfernen |
| 🔒 **Duplikat-Schutz** | Verhindert das doppelte Speichern desselben Secret Keys |
| 🌙 **Dark Mode** | Automatisches helles/dunkles Theme basierend auf Systemeinstellung |
| 🌍 **6 Sprachen** | Englisch, Chinesisch, Japanisch, Spanisch, Deutsch, Französisch |
| 🛡️ **Master-Passwort-Verschlüsselung** | Optionale AES-GCM-256-Verschlüsselung der gespeicherten Secrets; Schlüssel per PBKDF2-SHA256 (600.000 Iterationen) abgeleitet, Abfrage bei jedem Öffnen des Popups |

### ⭐ Premium (Lizenz erforderlich)

| Funktion | Beschreibung |
|---------|-------------|
| 📱 **QR-Code-Anzeige** | Scanbarer QR-Code, um Konten auf den Authentifikator Ihres Smartphones zu übertragen |

> 💡 Einmaliger Kauf, lebenslange Lizenz — 2 Aktivierungen pro Plugin. Jede Browserumgebung zählt als eine; jederzeit deaktivierbar, um einen Platz freizugeben. [Lizenz erhalten →](https://www.annmax1983.com/checkout.html?plugin=localbox2fa)

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
3. Klicke auf **Entpackte Erweiterung laden** und wähle den Ordner `LocalBox2FA`
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

### 🔒 Secrets verschlüsseln

Öffnen Sie **Einstellungen (⚙) → Master-Passwort** und klicken Sie auf **Verschlüsselung aktivieren**:

1. Vergeben und bestätigen Sie ein Master-Passwort
2. Alle bereits gespeicherten Secrets werden sofort versiegelt; sie tragen dann das Präfix 🔐 in der Liste
3. Beim nächsten Öffnen des Popups erscheint zuerst der Sperrbildschirm — Codes werden erst nach Eingabe des Passworts angezeigt

Hinweise:

- Das Master-Passwort kann **nicht zurückgesetzt oder wiederhergestellt** werden. Wenn Sie es vergessen, bleibt nur, im Sperrbildschirm alles zu löschen und neu zu beginnen — halten Sie deshalb ein exportiertes Backup bereit.
- Der abgeleitete Schlüssel liegt nur im Speicher und verschwindet mit dem Schließen des Popups — deshalb wird das Passwort bei jedem Öffnen abgefragt.
- **Verschlüsselung deaktivieren** im selben Bereich entschlüsselt alle Einträge wieder zu Klartext.

### Exportieren & Sichern

- Klicken Sie auf **Export**, um alle gespeicherten Secrets als `.txt`-Datei herunterzuladen
- Format: `Kontoname:Secret` (eine Zeile pro Eintrag); bei abweichenden Stellen/Periode/Algorithmus `Kontoname:otpauth://…`
- Bewahren Sie die Datei sicher auf — **sie ist unverschlüsselt** und wird nicht durch das Master-Passwort geschützt

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
- ✅ **Optionale Verschlüsselung im Ruhezustand** — Ohne Master-Passwort liegen Secrets im Klartext. Nach dem Einschalten wird jedes Secret mit AES-GCM 256 versiegelt; der Schlüssel wird aus Ihrem Passwort abgeleitet (PBKDF2-SHA256, 600.000 Iterationen), liegt nur im Speicher und wird nie geschrieben
- ✅ **Keine Analytik** — Kein Tracking, keine Telemetrie, keine Cookies
- ⚠️ **Minimale, offengelegte Netzwerknutzung** — Kostenlose Funktionen senden **überhaupt keine Netzwerkanfrage**. Mit einer Lizenz kontaktiert die Erweiterung `api.annmax1983.com` zum Aktivieren, zum Nachprüfen (höchstens einmal pro 2 h beim Öffnen des Popups) und zum Freigeben. Diese Anfragen enthalten den Lizenzschlüssel, eine zufällige Installationskennung und Browser-Metadaten (Browsername/-version, Sprachliste, Zeitzone, User-Agent) — **niemals Ihre Secrets oder erzeugten Codes**
- ✅ **Minimale Berechtigungen** — `storage` (zum Speichern deines Lizenzstatus) und Zugriff auf die Lizenzserver-Domain

---

## ⚠️ Sicherheitshinweise

**Bitte vor der Nutzung sorgfältig lesen:**

- **🔑 Verschlüsselung ist optional** — Standardmäßig liegen Secrets **unverschlüsselt** im Erweiterungsspeicher (`chrome.storage.local`); jeder mit Zugriff auf Ihr Browserprofil kann sie lesen. Aktivieren Sie das Master-Passwort in den Einstellungen.
- **🚫 Keine Passwortwiederherstellung** — Das Master-Passwort kann nicht zurückgesetzt werden, und verschlüsselte Einträge sind ohne es nicht wiederherstellbar. Wenn Sie es vergessen, bleibt nur, die Einträge im Sperrbildschirm zu löschen und neu zu beginnen. Exportieren Sie vorher ein Backup — und bewahren Sie es sicher auf, denn es ist unverschlüsselt.
- **💾 Extension entfernen = Datenverlust** — Das Entfernen der Extension oder das Löschen ihrer Daten **löscht dauerhaft** alle gespeicherten Konten. Bitte exportiere vorher eine Backup-Datei.
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
