# LocalBox2FA

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | Deutsch | [日本語](README_ja.md) | [Français](README_fr.md)

Eine schlanke Browser-Erweiterung, die TOTP-Bestätigungscodes für die Zwei-Faktor-Authentifizierung erzeugt. Secrets werden auf deinem Gerät erzeugt und genutzt — kein Erweiterungskonto, keine Handy-App, kein Server von uns. Wenn du dieselben Konten auf einem anderen Rechner brauchst, kann eine optionale verschlüsselte Synchronisierung sie über das Browser-Konto transportieren, das du bereits nutzt.

> Chrome / Edge / Firefox · Manifest V3 · Lokale Verarbeitung · Datenschutz zuerst

---

## Funktionen

### 🆓 Kostenlos

| Funktion | Beschreibung |
|----------|--------------|
| 🔐 **TOTP-Codes** | RFC 6238. Füge ein Base32-Secret oder einen vollständigen `otpauth://totp/...`-Link ein. Unterstützt 6–8 Stellen, eine eigene Periode sowie SHA-1 / SHA-256 / SHA-512 (Standard: 6 Stellen, 30 s, SHA-1). HOTP wird nicht unterstützt. |
| ⏱️ **Live-Countdown** | Jedes gespeicherte Konto zeigt seinen eigenen Code und Countdown, der beim Periodenwechsel neu berechnet wird |
| 📋 **Ein-Klick-Kopieren** | Klicke auf eine Zeile oder auf „Kopieren“, um den aktuellen Code in die Zwischenablage zu legen. Die Zwischenablage wird 30 Sekunden nach dem Kopieren geleert, solange das Popup geöffnet bleibt, und sofort beim automatischen Sperren |
| 💾 **Speichern & Verwalten** | Beim Speichern einen Namen vergeben, die Liste durchsuchen, Einträge umbenennen oder löschen |
| 🔒 **Duplikat-Schutz** | Dasselbe Secret lässt sich nicht zweimal speichern — Groß-/Kleinschreibung, Leerzeichen und Füllzeichen werden vor dem Vergleich normalisiert |
| 📱 **QR-Übertragung** | Klicke auf **QR-Code anzeigen**, um einen scanbaren Code für den Umzug eines Kontos in einen Handy-Authenticator einzublenden. Der QR-Code bleibt standardmäßig verborgen, um Blicke von der Seite zu verhindern |
| 🗑️ **Alles löschen** | Löscht nach Bestätigung alle gespeicherten Konten auf einmal |
| 🛡️ **Master-Passwort** | Optionale AES-GCM-256-Verschlüsselung für gespeicherte Secrets. Der Schlüssel wird mit PBKDF2-SHA256 (600.000 Iterationen) abgeleitet, nur im Speicher gehalten und bei jedem Öffnen des Popups abgefragt |
| 🔁 **Passwort ändern** | Versiegle alle gespeicherten Secrets jederzeit mit einem neuen Master-Passwort neu; die Konten bleiben erhalten, und ein synchronisierter Vault wird ebenfalls neu verschlüsselt |
| ⏲️ **Automatische Sperre** | Bei aktivierter Verschlüsselung optional nach 1, 5 oder 15 Minuten Inaktivität sperren (Standard: 5). Beim Schließen des Popups wird der Schlüssel immer aus dem Speicher entfernt |
| 📤 **Export** | Alle Secrets als Klartext-`.txt`-Datei herunterladen oder eine passwortverschlüsselte `.lb2fa`-Sicherung erstellen, die unabhängig vom Master-Passwort geschützt ist |
| 📥 **Import** | Aus Klartextdateien, verschlüsselten `.lb2fa`-Sicherungen, `otpauth://`-Links, Google-Authenticator-Migrations-QR-Codes oder QR-Bildern wiederherstellen. Doppelte und nicht unterstützte Einträge werden übersprungen |
| 🌙 **Dunkelmodus** | Folgt der hellen/dunklen Systemeinstellung |
| 🌍 **6 Sprachen** | Englisch, Chinesisch, Japanisch, Spanisch, Deutsch, Französisch |

> Export (Klartext oder verschlüsselt), Import, „Alles löschen“ und die QR-Anzeige sind kostenlos. Sichern, Wiederherstellen, Löschen und Übertragen der eigenen Secrets ist Datenpflege, kein Bezahlfeature.

### ⭐ Premium (Lizenz erforderlich)

| Funktion | Beschreibung |
|----------|--------------|
| 🔄 **Geräteübergreifende Synchronisierung** | Optionale Synchronisierung gespeicherter Konten zwischen Geräten, die im selben Browser-Konto angemeldet sind. Secrets werden mit deinem Master-Passwort versiegelt übertragen; die Synchronisierung läuft, solange das Popup offen ist, und nur echte Konflikte verlangen eine Entscheidung. Ein Statusbereich zeigt den letzten Sync-Zeitpunkt, die Anzahl lokaler und synchronisierter Konten, die Speichernutzung, ausstehende Konflikte und einen pausierten Zustand |

> Einmaliger Kauf, lebenslange Lizenz — 2 Aktivierungen pro Plugin. Jede Browser-Umgebung zählt als eine; jederzeit deaktivierbar, um einen Platz freizugeben. [Lizenz holen →](https://www.annmax1983.com/checkout.html?plugin=localbox2fa)

---

## Vorschau

<p align="center">
  <img src="../screenshots/A02.png" alt="LocalBox2FA Vorschau">
</p>

---

## Unterstützte Browser

| Browser | Status |
|---------|--------|
| Google Chrome | ✅ Vollständig unterstützt |
| Microsoft Edge | ✅ Vollständig unterstützt |
| Mozilla Firefox | ✅ Vollständig unterstützt |
| Andere Chromium-basierte Browser | ✅ Sollten funktionieren |

> **Firefox-Hinweis:** Die geräteübergreifende Synchronisierung läuft über Firefox Sync (Mozilla-Konto). Die übrigen Funktionen verhalten sich wie unter Chrome / Edge.

---

## Installation

| Store | Link |
|---|---|
| Chrome Web Store | [In Chrome installieren](https://chromewebstore.google.com/detail/hhhfdioecpkgnplkcdbcdabjodjpimem) |
| Microsoft Edge Add-ons | [In Edge installieren](https://microsoftedge.microsoft.com/addons/detail/mgmcahbcekbibbldnmgpeajnkphlnpin) |
| Firefox-Add-ons (AMO) | 🔜 In Prüfung – Link folgt nach der Freigabe |

> Installieren Sie nur über die offiziellen Stores oben – meiden Sie Download-Seiten Dritter.

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

Klicke bei einem gespeicherten Konto auf das ▣-Symbol und dann auf **QR-Code anzeigen**. Der QR-Code bleibt verborgen, bis du ihn anforderst, damit er nicht sichtbar ist, wenn das Popup auf einem geteilten Bildschirm geöffnet wird. Scanne ihn mit einem Handy-Authenticator, um das Konto dort zu importieren; beim Schließen des Dialogs wird der QR-Code verworfen.

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
- **Automatische Sperre** ist verfügbar, sobald die Verschlüsselung aktiv ist. Wähle unter **Einstellungen → Sicherheit** **Aus**, **1 Minute**, **5 Minuten** (Standard) oder **15 Minuten**; nach dieser Zeit ohne Aktivität wird der Vault gesperrt, sensible Dialoge werden geschlossen und die Zwischenablage geleert.

**Master-Passwort ändern**

Öffne **Einstellungen (⚙) → Master-Passwort → Master-Passwort ändern**, gib das aktuelle Passwort und danach zweimal das neue ein. Alle gespeicherten Secrets werden auf diesem Gerät neu verschlüsselt; die Konten bleiben erhalten. Bei aktiver Synchronisierung wird auch die Cloud-Kopie neu verschlüsselt. Andere Geräte melden danach eine Vault-Abweichung: Sie können die Cloud-Kopie übernehmen, indem sie das neue Passwort eingeben (ihre lokalen Konten werden vorher gelöscht), oder die Cloud-Kopie durch ihren eigenen Vault mit dem alten Passwort ersetzen. Beides geschieht nie automatisch. Die Änderung wird abgelehnt, solange ein Sync-Konflikt besteht oder eine Neuverschlüsselung noch aussteht. Eine unterbrochene Neuverschlüsselung wird bei einer späteren Synchronisierung erneut versucht; bis sie abgeschlossen ist, ist keine weitere Passwortänderung möglich.

### Zwischen Geräten synchronisieren (Premium)

Die Synchronisierung überträgt gespeicherte Konten zwischen Computern, die im selben Browser-Konto angemeldet sind. Sie bleibt **aus, bis du sie einschaltest**, benötigt ein Master-Passwort und eine aktive Lizenz.

**Erstes Gerät**

1. Öffne **Einstellungen (⚙) → Geräteübergreifende Synchronisierung** und klicke auf **Synchronisierung einschalten**
2. Prüfe den Zustimmungsdialog — er zeigt, wie viele Konten hochgeladen werden und was der Browser-Anbieter sehen kann
3. Bestätige. Die Datensätze werden versiegelt und in `storage.sync` geschrieben

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
- Bei der Zusammenführung überschreibt ein Gerät mit einem **anderen Master-Passwort** niemals den synchronisierten Vault; es meldet eine Vault-Abweichung und wartet auf eine ausdrückliche Entscheidung
- Alle Geräte, die denselben Vault teilen, sollten dieselbe Erweiterungsversion verwenden; eine ältere Version erkennt das aktuelle versiegelte Format möglicherweise nicht und kann Datensätze durch ältere Kopien ersetzen

**Hinweise**

- Der Sync-Bereich zeigt den letzten erfolgreichen Abgleich, die Anzahl lokaler und synchronisierter Konten, einen Speicherbalken für das Sync-Kontingent des Browsers (Bytes und Anzahl der Einträge), ausstehende Konflikte und einen pausierten/fehlerhaften Zustand. Ein Pausiert-Abzeichen bedeutet, dass die Synchronisierung erst weiterläuft, wenn du auf die Meldung darunter reagierst.
- Die Synchronisierung läuft beim Öffnen des Popups (nach dem Entsperren) und wenn ein anderes Gerät die Daten ändert; einen Button „Jetzt synchronisieren“ gibt es nicht
- Ausschalten behält die Cloud-Kopie für deine anderen Geräte. Mit **Synchronisierte Daten löschen** im selben Bereich entfernst du sie aus dem Browser-Konto; andere Geräte behalten ihre lokalen Konten und schalten die Synchronisierung aus, sobald sie das Fehlen der Cloud-Kopie bemerken
- Die Verschlüsselung lässt sich nicht deaktivieren, solange die Synchronisierung läuft, da Klartext-Datensätze niemals hochgeladen werden
- Der Lizenzschlüssel wird nicht synchronisiert; jedes Gerät aktiviert separat
- Die Daten werden vom Sync-Dienst des Browser-Kontos (Google oder Microsoft, je nach Browser) transportiert. Kontonamen und TOTP-Einstellungen sind für diesen Dienst lesbar; Secrets sind mit AES-GCM und deinem Master-Passwort versiegelt. Wenn du auch den Transport Ende-zu-Ende verschlüsseln willst, aktiviere die Sync-Passphrase des Browsers (Chrome: *Synchronisierung und Google-Dienste → Verschlüsselungsoptionen*)
- Es gelten die Sync-Kontingente des Browsers (insgesamt etwa 100 KB, 8 KB pro Eintrag); die Erweiterung meldet einen Kontingentfehler, statt Datensätze stillschweigend zu verwerfen

### Exportieren und importieren

**Export**

Klicke auf **Export** und wähle eines von zwei Formaten:

- **Verschlüsselte Sicherung** — lädt eine mit AES-GCM 256 verschlüsselte `.lb2fa`-Datei herunter. Das Sicherungspasswort wählst du hier; es ist unabhängig vom Master-Passwort und der einzige Weg, die Datei wiederherzustellen. Die Datei ist in sich abgeschlossen und stellt Konten auch wieder her, nachdem das Vault-Passwort geändert oder vergessen wurde.
- **Klartext** — lädt eine `.txt`-Datei mit einer Zeile `Kontoname:Secret` pro Konto herunter, bzw. `Kontoname:otpauth://…`, wenn Stellen, Periode oder Algorithmus vom Standard abweichen. Jeder, der die Datei öffnet, kann sie lesen; sie ist nicht durch dein Master-Passwort geschützt.

**Import**

Klicke auf **Import** und wähle eine der folgenden Quellen:

- eine Klartext-Sicherung `.txt`;
- eine verschlüsselte Sicherung `.lb2fa` — die Erweiterung erkennt das Format und fragt nach dem Sicherungspasswort;
- eine Datei oder ein Bild mit einem `otpauth://`-QR-Code, einem Google-Authenticator-Migrations-QR-Code (`otpauth-migration://offline?data=…`) oder eine Textzeile mit einem Base32-Secret oder `otpauth://`-Link.

Bereits gespeicherte Secrets werden übersprungen. HOTP- und nicht unterstützte Einträge werden übersprungen und gezählt. Bei einem mehrteiligen Google-Authenticator-Export importiere jedes QR-Bild einzeln; bereits importierte Konten werden übersprungen.

---

## So funktioniert es

1. Gib ein Base32-Secret oder einen `otpauth://`-Link ein.
2. Der Code wird auf deinem Gerät mit der eingebauten Kryptografie des Browsers erzeugt.
3. Ein 6–8-stelliger Code erscheint mit Countdown und aktualisiert sich von selbst.
4. Ein Klick kopiert ihn in die Zwischenablage.

Alle Berechnungen laufen lokal über die Web Crypto API des Browsers. Das Generieren eines Codes löst keine Netzwerkanfrage aus. Gespeicherte Daten verlassen das Gerät nur, wenn du die verschlüsselte geräteübergreifende Synchronisierung ausdrücklich einschaltest.

---

## Datenschutz und Berechtigungen

- **Standardmäßig lokal** — gespeicherte Secrets liegen in `storage.local` und verlassen das Gerät nicht, solange du die Synchronisierung nicht einschaltest
- **Optionale Verschlüsselung** — ohne Master-Passwort sind gespeicherte Secrets Klartext. Nach dem Aktivieren wird jedes Secret mit AES-GCM 256 versiegelt; der Schlüssel wird aus deinem Passwort abgeleitet (PBKDF2-SHA256, 600k Iterationen) und nur im Speicher gehalten
- **Synchronisierung nur nach Zustimmung** — versiegelte Datensätze, Kontonamen, TOTP-Einstellungen sowie Salt/Iterationen/Prüfwert des Vaults werden in `storage.sync` geschrieben und vom Browser-Konto transportiert. Master-Passwort und Lizenzschlüssel sind nie enthalten
- **Keine Analyse** — kein Tracking, keine Telemetrie, keine Cookies, keine Skripte Dritter
- **Kein Seitenzugriff** — keine Content-Scripts, kein Zugriff auf Verlauf, Tabs oder Lesezeichen
- **Minimale Netzwerknutzung** — ohne Lizenz macht die Erweiterung keine Netzwerkanfrage, außer dem erneuten Versuch einer Freigabe, die offline eingereiht wurde. Mit Lizenz kontaktiert sie `api.annmax1983.com` zum Aktivieren, zum erneuten Prüfen (beim Öffnen des Popups höchstens alle 2 Stunden) und zum Freigeben der Lizenz. Diese Anfragen enthalten den Lizenzschlüssel, eine zufällige Installations-ID und Browser-Metadaten (Browser-Name/-Version, Sprachen, Zeitzone, User-Agent); Secrets und generierte Codes sind nie enthalten
- **Minimale Berechtigungen** — `storage` und `clipboardWrite` sowie Zugriff auf die Domain des Lizenzservers. `clipboardWrite` ermöglicht dem Popup, einen Code zu kopieren und ihn wieder zu löschen; es kann die Zwischenablage nicht lesen und gewährt keinen Seitenzugriff. Die Synchronisierung fügt keine Berechtigung hinzu und nutzt keinen Server von uns

Die feldgenaue Aufstellung steht in [privacy-policy.html](../privacy-policy.html).

---

## ⚠️ Sicherheitshinweise

- **Verschlüsselung ist optional** — ohne Master-Passwort liegen Secrets unverschlüsselt im lokalen Speicher der Erweiterung. Wer Zugriff auf dein Browserprofil hat, kann sie lesen. Aktiviere das Master-Passwort, um sie zu versiegeln.
- **Keine Passwort-Wiederherstellung** — das Master-Passwort lässt sich nicht zurücksetzen, und versiegelte Datensätze sind ohne es nicht wiederherstellbar. Wenn du es vergisst, bleibt nur das Löschen über den Sperrbildschirm. Halte einen exportierten Backup bereit; wähle das verschlüsselte Format und verwahre dessen Sicherungspasswort getrennt auf, denn auch das Sicherungspasswort lässt sich nicht wiederherstellen.
- **Erweiterung entfernen löscht lokale Daten** — Deinstallieren oder Leeren des lokalen Speichers löscht alle auf diesem Gerät gespeicherten Konten dauerhaft. Bei aktiver Synchronisierung bleibt eine Kopie im Browser-Konto und lässt sich nach Neuinstallation durch erneutes Aktivieren der Lizenz und Beitreten zur bestehenden Synchronisierung mit demselben Master-Passwort wiederherstellen; nutze zuerst **Synchronisierte Daten löschen**, wenn sie verschwinden soll.
- **Synchronisierung ist kein Backup** — Löschungen werden übertragen: Löschst du ein Konto auf einem Gerät, verschwindet es auch auf den anderen. Halte für alles, was du nicht neu anlegen kannst, einen exportierten Backup.
- **Vertrauen ins Browser-Konto** — synchronisierte Daten werden vom Sync-Dienst deines Browser-Anbieters transportiert. Secrets sind mit deinem Master-Passwort versiegelt, Kontonamen und TOTP-Einstellungen nicht. Wer Zugriff auf dein Browser-Konto *und* dein Master-Passwort hat, kann die Secrets lesen; aktiviere die Sync-Passphrase des Browsers, um auch den Transport zu verschlüsseln.
- **Das Exportformat zählt** — eine Klartext-Sicherung `.txt` kann jeder lesen, der sie öffnet; behandle sie wie ein Geheimnis und teile sie nicht. Eine verschlüsselte Sicherung `.lb2fa` ist mit dem beim Export gewählten Passwort versiegelt, das unabhängig vom Master-Passwort ist.
- **Bildschirme und Zwischenablagen verraten viel** — QR-Codes bleiben verborgen, bis du auf **QR-Code anzeigen** klickst, kopierte Codes werden 30 Sekunden nach dem Kopieren (oder beim automatischen Sperren) aus der Zwischenablage entfernt, und die automatische Sperre begrenzt, wie lange ein entsperrter Vault auf dem Bildschirm bleibt. Das Schließen des Popups vernichtet den abgeleiteten Schlüssel, aber ein unmittelbar davor kopierter Code bleibt wie jede andere Kopie in der System-Zwischenablage. Nichts davon schützt einen kompromittierten Computer.
- **Best Practice** — lösche ein Secret in der Erweiterung, sobald es in einer dedizierten Authenticator-App liegt.

---

## Kompatibilität

LocalBox2FA implementiert RFC 6238 TOTP und akzeptiert Secrets von Google Authenticator, Authy und anderen gängigen 2FA-Tools. Es ist ein unabhängiges Werkzeug und steht in keiner offiziellen Verbindung zu diesen Marken.

---

## Quellcode-Hinweis

> ⚠️ **Dieses Repository veröffentlicht keinen Quellcode.** Es enthält ausschließlich Nutzungsdokumentation, Versionshinweise und Support-Ressourcen. Die Erweiterung wird ausschließlich über den Chrome Web Store, Microsoft Edge Add-ons und Firefox-Add-ons (AMO) verteilt; es gibt kein Offline-Installationspaket und keinen Endnutzer-Quellcode.

---

## Lizenz

Copyright © 2026 LocalBox2FA. Alle Rechte vorbehalten.

---

## ❤️ Unterstützen

Wenn dir LocalBox2FA hilft, kannst du das Projekt unterstützen!

**[👉 LocalBox2FA unterstützen](https://annmax1983.github.io/LocalBox2FA/)**
