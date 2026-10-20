# LocalBox2FA

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | Deutsch | [日本語](README_ja.md) | [Français](README_fr.md)

Eine schlanke Browser-Erweiterung, die TOTP-Bestätigungscodes für die Zwei-Faktor-Authentifizierung erzeugt. Secrets werden auf deinem Gerät erzeugt und genutzt — kein Erweiterungskonto, keine Handy-App, kein Server von uns. Wenn du dieselben Konten auf einem anderen Rechner brauchst, kann eine optionale verschlüsselte Synchronisierung sie über das Browser-Konto transportieren, das du bereits nutzt.

> Chromium-basiert · Manifest V3 · Lokale Verarbeitung · Datenschutz zuerst

---

## Funktionen

### 🆓 Kostenlos

| Funktion | Beschreibung |
|----------|--------------|
| 🔐 **TOTP-Codes** | RFC 6238. Füge ein Base32-Secret oder einen vollständigen `otpauth://totp/...`-Link ein. Unterstützt 6–8 Stellen, eine eigene Periode sowie SHA-1 / SHA-256 / SHA-512 (Standard: 6 Stellen, 30 s, SHA-1). HOTP wird nicht unterstützt. |
| ⏱️ **Live-Countdown** | Jedes gespeicherte Konto zeigt seinen eigenen Code und Countdown, der beim Periodenwechsel neu berechnet wird |
| 📋 **Ein-Klick-Kopieren** | Klicke auf eine Zeile oder auf „Kopieren“, um den aktuellen Code in die Zwischenablage zu legen |
| 💾 **Speichern & Verwalten** | Beim Speichern einen Namen vergeben, die Liste durchsuchen, Einträge umbenennen oder löschen |
| 🔒 **Duplikat-Schutz** | Dasselbe Secret lässt sich nicht zweimal speichern — Groß-/Kleinschreibung, Leerzeichen und Füllzeichen werden vor dem Vergleich normalisiert |
| 📱 **QR-Übertragung** | Zeigt einen scanbaren QR-Code, um ein Konto in einen Handy-Authenticator zu übernehmen |
| 🗑️ **Alles löschen** | Löscht nach Bestätigung alle gespeicherten Konten auf einmal |
| 🛡️ **Master-Passwort** | Optionale AES-GCM-256-Verschlüsselung für gespeicherte Secrets. Der Schlüssel wird mit PBKDF2-SHA256 (600.000 Iterationen) abgeleitet, nur im Speicher gehalten und bei jedem Öffnen des Popups abgefragt |
| 📤 **Export** | Alle Secrets als Klartext-`.txt`-Datei herunterladen |
| 📥 **Import** | Konten aus einer Sicherungsdatei wiederherstellen, ein Konto pro Zeile |
| 🌙 **Dunkelmodus** | Folgt der hellen/dunklen Systemeinstellung |
| 🌍 **6 Sprachen** | Englisch, Chinesisch, Japanisch, Spanisch, Deutsch, Französisch |

> Export, Import, „Alles löschen“ und die QR-Anzeige sind kostenlos. Sichern, Wiederherstellen, Löschen und Übertragen der eigenen Secrets ist Datenpflege, kein Bezahlfeature.

### ⭐ Premium (Lizenz erforderlich)

| Funktion | Beschreibung |
|----------|--------------|
| 🔄 **Geräteübergreifende Synchronisierung** | Optionale Synchronisierung gespeicherter Konten zwischen Geräten, die im selben Browser-Konto angemeldet sind. Secrets werden mit deinem Master-Passwort versiegelt übertragen; die Synchronisierung läuft, solange das Popup offen ist, und nur echte Konflikte verlangen eine Entscheidung |

> Einmaliger Kauf, lebenslange Lizenz — 2 Aktivierungen pro Plugin. Jede Browser-Umgebung zählt als eine; jederzeit deaktivierbar, um einen Platz freizugeben. [Lizenz holen →](https://www.annmax1983.com/checkout.html?plugin=localbox2fa)

---

## Vorschau

<p align="center">
  <img src="../images/A02.png" alt="LocalBox2FA Vorschau">
</p>

---

## Unterstützte Browser

| Browser | Status |
|---------|--------|
| Google Chrome | ✅ Vollständig unterstützt |
| Microsoft Edge | ✅ Vollständig unterstützt |
| Andere Chromium-basierte Browser | ✅ Sollten funktionieren |

---

## Installation

1. Öffne die Erweiterungsseite deines Browsers:
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
2. Aktiviere den **Entwicklermodus** (Schalter oben rechts)
3. Klicke auf **Entpackte Erweiterung laden** und wähle den Ordner `LocalBox2FA`
4. Klicke auf das 🔐-Symbol in der Symbolleiste

---

## Verwendung

### Einen Code generieren

1. Klicke auf das LocalBox2FA-Symbol in der Symbolleiste
2. Füge ein Base32-Secret oder einen vollständigen `otpauth://totp/...`-Link in das Eingabefeld ein
3. Klicke auf **Generieren** — der Code erscheint mit Countdown
4. Klicke auf **Kopieren**, um ihn in die Zwischenablage zu legen

Ein reines Base32-Secret nutzt die Standardwerte (6 Stellen, 30 s, SHA-1). Ein vollständiger `otpauth://`-Link bringt eigene Stellen, Periode und Algorithmus mit — nötig für Dienste, die nicht die Standardwerte verwenden.

### Ein Konto speichern

1. Nach dem Generieren eines Codes auf **Speichern** klicken
2. Einen Namen eingeben (zum Beispiel „GitHub“ oder „Google“)
3. Das Konto erscheint mit laufendem Code und Countdown in der Liste

### Gespeicherte Konten verwenden

- Klicke auf ein Konto, um den aktuellen Code zu kopieren
- Nutze das Suchfeld, um eine lange Liste zu filtern
- Das Stift-Symbol benennt ein Konto um, das ✕-Symbol löscht es nach Bestätigung
- **Alles löschen** am unteren Rand entfernt alle gespeicherten Einträge

### Ein Konto aufs Handy übertragen

Klicke bei einem gespeicherten Konto auf das ▣-Symbol, um einen QR-Code mit dem `otpauth://`-Link anzuzeigen. Scanne ihn mit einem Handy-Authenticator, um das Konto dort zu importieren.

### Secrets verschlüsseln

Öffne **Einstellungen (⚙) → Master-Passwort** und klicke auf **Verschlüsselung aktivieren**:

1. Wähle ein Master-Passwort und bestätige es
2. Alle gespeicherten Secrets werden sofort versiegelt; nur Metadaten (Name, Stellen, Periode, Algorithmus, Zeitstempel und zufällige Datensatz-/Geräte-IDs) bleiben lesbar
3. Ab dann fragt der Sperrbildschirm bei jedem Öffnen nach dem Passwort, bevor ein Code erscheint

Hinweise:

- Das Passwort **lässt sich nicht zurücksetzen oder wiederherstellen**. Wenn du es vergisst, bietet der Sperrbildschirm an, alles zu löschen und neu zu beginnen — halte deshalb einen exportierten Backup bereit.
- Der abgeleitete Schlüssel liegt nur im Speicher und verschwindet beim Schließen des Popups — deshalb wird bei jedem Öffnen danach gefragt.
- Ein versiegeltes Secret ist an seinen Datensatz gebunden: Ein auf ein anderes Konto kopierter Geheimtext lässt sich nicht öffnen, eine manipulierte Synchronisierungskopie kann also keinen vertrauten Namen auf ein fremdes Secret umlenken.
- **Verschlüsselung deaktivieren** entschlüsselt alle Datensätze wieder in Klartext. Lässt sich auch nur ein Datensatz nicht entschlüsseln, wird der Vorgang abgelehnt, die betroffenen Konten werden aufgelistet und nichts wird geändert — lösche diese Konten zuerst und versuche es erneut.
- Versiegelte Einträge tragen ein 🔐-Präfix in der Liste; ein nicht entschlüsselbarer Datensatz zeigt 🔐 statt eines Codes.

### Zwischen Geräten synchronisieren (Premium)

Die Synchronisierung überträgt gespeicherte Konten zwischen Computern, die im selben Browser-Konto angemeldet sind. Sie bleibt **aus, bis du sie einschaltest**, benötigt ein Master-Passwort und eine aktive Lizenz.

**Erstes Gerät**

1. Öffne **Einstellungen (⚙) → Geräteübergreifende Synchronisierung** und klicke auf **Synchronisierung einschalten**
2. Prüfe den Zustimmungsdialog — er zeigt, wie viele Konten hochgeladen werden und was der Browser-Anbieter sehen kann
3. Bestätige. Die Datensätze werden versiegelt und in `chrome.storage.sync` geschrieben

**Zweites Gerät**

1. Melde den Browser im selben Konto an und installiere LocalBox2FA
2. Öffne **Einstellungen → Geräteübergreifende Synchronisierung → Bestehender Synchronisierung beitreten**
3. Gib dasselbe **Master-Passwort** wie auf dem ersten Gerät ein

Die Erweiterung synchronisiert niemals das Passwort oder einen abgeleiteten Schlüssel. Das zweite Gerät erhält nur Salt, Iterationszahl und Prüfwert des Vaults, prüft das Passwort daran und versiegelt lokale Klartext-Datensätze mit demselben Schlüssel. Ein falsches Passwort wird abgelehnt, bevor irgendetwas zusammengeführt wird.

**Warum das Zusammenführen sicher bleibt**

- Jeder Datensatz hat einen eigenen Sync-Speicherschlüssel und eine stabile ID sowie beim Löschen einen ausdrücklichen Grabstein — ein fehlender Schlüssel bedeutet nie „gelöscht“, und ein Gerät kann die Ergänzungen eines anderen nicht durch Schreiben einer ganzen Liste auslöschen
- Vor dem Überschreiben liest die Erweiterung die neueste Cloud-Kopie erneut; hat ein anderes Gerät den Datensatz inzwischen geändert oder gelöscht, wird der Upload zurückgestellt und die Abweichung als echter Konflikt gemeldet
- Ein Drei-Wege-Vergleich (letzter Sync-Stand / lokal / remote) übernimmt konfliktfreie Änderungen automatisch
- Wurde dasselbe Konto auf zwei Geräten wirklich geändert, fragt ein Dialog, ob **dieses Gerät**, **das andere Gerät** oder **beide** behalten werden sollen — ohne deine Entscheidung wird nichts überschrieben
- Ein Gerät mit einem **anderen Master-Passwort** darf den synchronisierten Vault niemals überschreiben; es meldet stattdessen eine Vault-Abweichung
- Alle Geräte, die denselben Vault teilen, sollten dieselbe Erweiterungsversion verwenden; eine ältere Version erkennt das aktuelle versiegelte Format möglicherweise nicht und kann Datensätze durch ältere Kopien ersetzen

**Hinweise**

- Die Synchronisierung läuft beim Öffnen des Popups (nach dem Entsperren) und wenn ein anderes Gerät die Daten ändert; einen Button „Jetzt synchronisieren“ gibt es nicht
- Ausschalten behält die Cloud-Kopie für deine anderen Geräte. Mit **Synchronisierte Daten löschen** im selben Bereich entfernst du sie aus dem Browser-Konto; andere Geräte behalten ihre lokalen Konten und schalten die Synchronisierung aus, sobald sie das Fehlen der Cloud-Kopie bemerken
- Die Verschlüsselung lässt sich nicht deaktivieren, solange die Synchronisierung läuft, da Klartext-Datensätze niemals hochgeladen werden
- Der Lizenzschlüssel wird nicht synchronisiert; jedes Gerät aktiviert separat
- Die Daten werden vom Sync-Dienst des Browser-Kontos (Google oder Microsoft, je nach Browser) transportiert. Kontonamen und TOTP-Einstellungen sind für diesen Dienst lesbar; Secrets sind mit AES-GCM und deinem Master-Passwort versiegelt. Wenn du auch den Transport Ende-zu-Ende verschlüsseln willst, aktiviere die Sync-Passphrase des Browsers (Chrome: *Synchronisierung und Google-Dienste → Verschlüsselungsoptionen*)
- Es gelten die Sync-Kontingente des Browsers (insgesamt etwa 100 KB, 8 KB pro Eintrag); die Erweiterung meldet einen Kontingentfehler, statt Datensätze stillschweigend zu verwerfen

### Exportieren und importieren

- Klicke auf **Export**, um alle gespeicherten Secrets als `.txt`-Datei herunterzuladen
- Jede Zeile lautet `Kontoname:Secret` oder `Kontoname:otpauth://…` bei Konten mit abweichenden Stellen, Periode oder Algorithmus
- Klicke auf **Import** und wähle eine solche Datei, um Konten wiederherzustellen; bereits gespeicherte Zeilen werden übersprungen
- Die Exportdatei ist **Klartext** und nicht durch dein Master-Passwort geschützt

---

## So funktioniert es

```
Base32-Secret oder otpauth://-Link eingeben
       ↓
Web Crypto API berechnet HMAC (standardmäßig SHA-1)
       ↓
TOTP-Code mit 6–8 Stellen (RFC 6238)
       ↓
Countdown mit automatischer Aktualisierung
       ↓
Ein-Klick-Kopieren in die Zwischenablage
```

Alle Berechnungen laufen lokal über die Web Crypto API des Browsers. Das Generieren eines Codes löst keine Netzwerkanfrage aus. Gespeicherte Daten verlassen das Gerät nur, wenn du die verschlüsselte geräteübergreifende Synchronisierung ausdrücklich einschaltest.

---

## Datenschutz und Berechtigungen

- **Standardmäßig lokal** — gespeicherte Secrets liegen in `chrome.storage.local` und verlassen das Gerät nicht, solange du die Synchronisierung nicht einschaltest
- **Optionale Verschlüsselung** — ohne Master-Passwort sind gespeicherte Secrets Klartext. Nach dem Aktivieren wird jedes Secret mit AES-GCM 256 versiegelt; der Schlüssel wird aus deinem Passwort abgeleitet (PBKDF2-SHA256, 600k Iterationen) und nur im Speicher gehalten
- **Synchronisierung nur nach Zustimmung** — versiegelte Datensätze, Kontonamen, TOTP-Einstellungen sowie Salt/Iterationen/Prüfwert des Vaults werden in `chrome.storage.sync` geschrieben und vom Browser-Konto transportiert. Master-Passwort und Lizenzschlüssel sind nie enthalten
- **Keine Analyse** — kein Tracking, keine Telemetrie, keine Cookies, keine Skripte Dritter
- **Kein Seitenzugriff** — keine Content-Scripts, kein Zugriff auf Verlauf, Tabs oder Lesezeichen
- **Minimale Netzwerknutzung** — ohne Lizenz macht die Erweiterung keine Netzwerkanfrage, außer dem erneuten Versuch einer Freigabe, die offline eingereiht wurde. Mit Lizenz kontaktiert sie `api.annmax1983.com` zum Aktivieren, zum erneuten Prüfen (beim Öffnen des Popups höchstens alle 2 Stunden) und zum Freigeben der Lizenz. Diese Anfragen enthalten den Lizenzschlüssel, eine zufällige Installations-ID und Browser-Metadaten (Browser-Name/-Version, Sprachen, Zeitzone, User-Agent); Secrets und generierte Codes sind nie enthalten
- **Minimale Berechtigungen** — nur `storage` plus Zugriff auf die Domain des Lizenzservers. Die Synchronisierung fügt keine Berechtigung hinzu und nutzt keinen Server von uns

Die feldgenaue Aufstellung steht in [privacy-policy.html](../privacy-policy.html).

---

## ⚠️ Sicherheitshinweise

- **Verschlüsselung ist optional** — ohne Master-Passwort liegen Secrets unverschlüsselt im lokalen Speicher der Erweiterung. Wer Zugriff auf dein Browserprofil hat, kann sie lesen. Aktiviere das Master-Passwort, um sie zu versiegeln.
- **Keine Passwort-Wiederherstellung** — das Master-Passwort lässt sich nicht zurücksetzen, und versiegelte Datensätze sind ohne es nicht wiederherstellbar. Wenn du es vergisst, bleibt nur das Löschen über den Sperrbildschirm. Halte einen exportierten Backup bereit — und verwahre ihn sicher, denn er ist Klartext.
- **Erweiterung entfernen löscht lokale Daten** — Deinstallieren oder Leeren des lokalen Speichers löscht alle auf diesem Gerät gespeicherten Konten dauerhaft. Bei aktiver Synchronisierung bleibt eine Kopie im Browser-Konto und lässt sich nach Neuinstallation durch erneutes Aktivieren der Lizenz und Beitreten zur bestehenden Synchronisierung mit demselben Master-Passwort wiederherstellen; nutze zuerst **Synchronisierte Daten löschen**, wenn sie verschwinden soll.
- **Synchronisierung ist kein Backup** — Löschungen werden übertragen: Löschst du ein Konto auf einem Gerät, verschwindet es auch auf den anderen. Halte für alles, was du nicht neu anlegen kannst, einen exportierten Backup.
- **Vertrauen ins Browser-Konto** — synchronisierte Daten werden vom Sync-Dienst deines Browser-Anbieters transportiert. Secrets sind mit deinem Master-Passwort versiegelt, Kontonamen und TOTP-Einstellungen nicht. Wer Zugriff auf dein Browser-Konto *und* dein Master-Passwort hat, kann die Secrets lesen; aktiviere die Sync-Passphrase des Browsers, um auch den Transport zu verschlüsseln.
- **Exportdateien sind unverschlüsselt** — behandle die `.txt`-Sicherung wie ein Geheimnis und teile sie nicht.
- **Best Practice** — lösche ein Secret in der Erweiterung, sobald es in einer dedizierten Authenticator-App liegt.

---

## Kompatibilität

LocalBox2FA implementiert RFC 6238 TOTP und akzeptiert Secrets von Google Authenticator, Authy und anderen gängigen 2FA-Tools. Es ist ein unabhängiges Werkzeug und steht in keiner offiziellen Verbindung zu diesen Marken.

---

## Quellcode-Hinweis

> ⚠️ **Dieses Repository veröffentlicht keinen Quellcode.** Es enthält ausschließlich Nutzungsdokumentation, Versionshinweise und Support-Ressourcen. Die Erweiterung wird ausschließlich über den Chrome Web Store verteilt; es gibt kein Offline-Installationspaket und keinen Endnutzer-Quellcode.

---

## Lizenz

Copyright © 2026 LocalBox2FA. Alle Rechte vorbehalten.

---

## ❤️ Unterstützen

Wenn dir LocalBox2FA hilft, kannst du das Projekt unterstützen!

**[👉 LocalBox2FA unterstützen](https://annmax1983.github.io/LocalBox2FA/)**
