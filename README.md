# LocalBox2FA

English | [中文](languages/README_zh.md) | [Español](languages/README_es.md) | [Deutsch](languages/README_de.md) | [日本語](languages/README_ja.md) | [Français](languages/README_fr.md)

A lightweight browser extension that generates TOTP two-factor authentication codes. Secrets are created and used on your device — no extension account, no phone app, and no server of ours stores your secrets. If you want the same accounts on another computer, optional encrypted sync can carry them through the browser account you already use.

> Chromium-based · Manifest V3 · Local processing · Privacy first

---

## Features

### Free

| Feature | Description |
|---------|-------------|
| 🔐 **TOTP codes** | RFC 6238. Paste a Base32 secret or a complete `otpauth://totp/...` link. Supports 6–8 digits, a custom period and SHA-1 / SHA-256 / SHA-512 (defaults: 6 digits, 30 s, SHA-1). HOTP is not supported. |
| ⏱️ **Live countdown** | Every saved account shows its own code and countdown, refreshed when the period rolls over |
| 📋 **One-click copy** | Click a row, or the Copy button, to put the current code on the clipboard. The clipboard is cleared 30 seconds after copying while the popup stays open, or immediately when auto-lock engages |
| 💾 **Save & manage** | Name an account when saving, search the list, rename or delete an entry |
| 🔒 **Duplicate guard** | The same secret cannot be saved twice, however it is spelled — case, spaces and padding are normalised before comparison |
| 📱 **QR transfer** | Click **Show QR code** to reveal a scannable code for moving an account to a phone authenticator. The QR stays hidden by default to avoid shoulder surfing |
| 🗑️ **Clear all** | Erase every saved account at once, after confirmation |
| 🛡️ **Master password** | Optional AES-GCM 256 encryption for saved secrets. The key is derived with PBKDF2-SHA256 (600,000 iterations), kept in memory only, and asked for on every popup open |
| 🔁 **Change password** | Re-encrypt every stored secret under a new master password at any time; accounts are kept, and a synced vault is re-keyed too |
| ⏲️ **Idle auto-lock** | With encryption on, optionally lock the vault after 1, 5 or 15 minutes without activity (default: 5). Closing the popup always clears the key from memory |
| 📤 **Export** | Download all secrets as a plaintext `.txt` file, or create a password-encrypted `.lb2fa` backup protected independently of your master password |
| 📥 **Import** | Restore from plaintext files, encrypted `.lb2fa` backups, `otpauth://` links, Google Authenticator migration QR codes or QR images. Duplicate and unsupported entries are skipped |
| 🌙 **Dark mode** | Follows the system light/dark preference |
| 🌍 **6 languages** | English, Chinese, Japanese, Spanish, German, French |

> Export (plaintext or encrypted), import, clear-all and QR display are free. Backing up, restoring, erasing and transferring your own secrets is data hygiene, not a paid feature.

### Premium (license required)

| Feature | Description |
|---------|-------------|
| 🔄 **Cross-device sync** | Optional sync of saved accounts between devices signed into the same browser account. Secrets travel sealed with your master password; sync runs while the popup is open, and only genuine conflicts ask you to choose. A status panel shows the last sync time, local and synced account counts, storage usage, pending conflicts and any paused state |

> One-time purchase, lifetime license — 2 activations per plugin. Each browser environment counts as one; deactivate anytime to free a slot. [Get a license →](https://www.annmax1983.com/checkout.html?plugin=localbox2fa)

---

## Preview

<p align="center">
  <img src="images/A02.png" alt="LocalBox2FA Preview">
</p>

---

## Supported browsers

| Browser | Status |
|---------|--------|
| Google Chrome | ✅ Fully supported |
| Microsoft Edge | ✅ Fully supported |
| Other Chromium-based browsers | ✅ Expected to work |

---

## Installation

1. Open your browser's extension page:
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
2. Enable **Developer mode** (top-right toggle)
3. Click **Load unpacked** and select the `LocalBox2FA` folder
4. Click the 🔐 LocalBox2FA icon in the toolbar

---

## Usage

### Generate a code

1. Click the LocalBox2FA icon in the toolbar
2. Paste either a Base32 secret or a full `otpauth://totp/...` link into the input field
3. Click **Generate** — the code appears with its countdown
4. Click **Copy** to put it on the clipboard

A bare Base32 secret uses the defaults (6 digits, 30 s, SHA-1). A full `otpauth://` link carries its own digits, period and algorithm, which is what you need for services that do not use the defaults.

### Save an account

1. After generating a code, click **Save**
2. Enter a name (for example "GitHub" or "Google")
3. The account appears in the list with a live code and countdown

### Use saved accounts

- Click any account to copy its current code
- Use the search box to filter a long list
- The pencil icon renames an account; the ✕ icon deletes it after confirmation
- **Clear all** in the footer erases every saved record

### Move an account to a phone

Click the ▣ icon on a saved account, then click **Show QR code**. The QR is hidden until you ask for it, so it is not exposed when the popup opens on a shared screen. Scan it with a phone authenticator to import the account there; the QR dialog closes when you leave it.

### Encrypt your secrets

Open **Settings (⚙) → Master password** and click **Enable encryption**:

1. Choose a master password and confirm it
2. Every saved secret is sealed immediately; only metadata (name, digits, period, algorithm, timestamps and random record/device IDs) stays readable
3. From then on the lock screen asks for the password before any code is shown

Notes:

- The password **cannot be reset or recovered**. If you forget it, the lock screen offers to erase everything and start over, so keep an exported backup.
- The derived key lives in memory only and dies when the popup closes — that is why the password is asked for on every open.
- A sealed secret is bound to its record: a ciphertext copied onto a different account cannot be opened, so a tampered sync copy cannot silently point a familiar name at another secret.
- **Turn off encryption** decrypts every record back to plaintext. If any record cannot be decrypted, the operation is refused, the affected accounts are listed and nothing is changed — delete those accounts first and retry.
- Sealed records show a 🔐 prefix in the list; a record that cannot be decrypted shows 🔐 instead of a code.
- **Idle auto-lock** is available once encryption is on. Choose **Off**, **1 minute**, **5 minutes** (default) or **15 minutes** in **Settings → Security**; after that much inactivity the vault locks, sensitive dialogs close and the clipboard is cleared.

**Change master password**

Open **Settings (⚙) → Master password → Change master password**, enter the current password, then the new one twice. Every saved secret is re-encrypted on this device; accounts are kept. If sync is on, the synced copy is re-keyed as well. Other devices then report a vault mismatch: they can adopt the cloud copy by entering the new password, which erases their local accounts first, or replace the cloud copy with their own vault under the old password. Neither choice happens automatically. The change is refused while a sync conflict exists or a re-key is still pending. An interrupted re-key is retried on a later sync, and another password change is blocked until it completes.

### Sync across devices (Premium)

Sync carries saved accounts between computers signed into the same browser account. It stays **off until you turn it on**, requires a master password, and requires an active license.

**First device**

1. Open **Settings (⚙) → Cross-device sync** and click **Turn on sync**
2. Review the consent screen — it shows how many accounts will be uploaded and what the browser vendor can see
3. Confirm. Records are sealed and written to `chrome.storage.sync`

**Second device**

1. Sign the browser into the same account and install LocalBox2FA
2. Open **Settings → Cross-device sync → Join existing sync**
3. Enter the **same master password** used on the first device

The extension never syncs the password or a derived key. The second device receives only the vault's salt, iteration count and verifier, checks the password against it, and seals any local plaintext records with the same key. A wrong password is rejected before anything is merged.

**How merging stays safe**

- Each record has its own sync-storage key and stable ID, plus an explicit tombstone when deleted — a missing key never means "deleted", and one device cannot wipe another's additions by writing a whole list
- Before overwriting a record, the extension re-reads the latest cloud copy; if another device changed or deleted it in the meantime, the upload is deferred and the difference is raised as a real conflict
- A three-way comparison (last synced state / local / remote) applies non-conflicting changes automatically
- If the same account was genuinely changed on two devices, a dialog asks you to keep **this device**, **the other device**, or **both** — nothing is overwritten without your choice
- During a merge, a device with a **different master password** never overwrites the synced vault; it reports a vault mismatch and waits for an explicit choice
- Keep every device that shares a synced vault on the same extension version; an older version may not recognise the current sealed format and can replace records with older copies

**Notes**

- The sync panel shows the last successful sync, the number of local and synced accounts, a storage bar for the browser's sync quota (bytes and item count), pending conflicts and any paused/error state. A paused badge means sync cannot make progress until you act on the message below it.
- Sync runs when the popup opens (after unlock) and when another device changes the synced data; there is no manual "Sync now" button
- Turning sync off keeps the cloud copy for your other devices. Use **Delete synced data** in the same panel to remove it from the browser account; other devices keep their local accounts and switch sync off once they notice the cloud copy is gone
- Encryption cannot be turned off while sync is on, because plaintext records are never uploaded
- The license key is not synced; each device activates separately
- The browser account's sync service (Google or Microsoft, depending on the browser) transports the data. Account names and TOTP settings are readable by that service; secrets are sealed with AES-GCM and your master password. If you want the transport itself encrypted end-to-end, enable your browser's sync passphrase (Chrome: *Sync and Google services → Encryption options*)
- Browser sync quotas apply (roughly 100 KB total, 8 KB per item); the extension reports a quota error instead of silently dropping records

### Export and import

**Export**

Click **Export** and choose one of two formats:

- **Encrypted backup** — downloads a `.lb2fa` file encrypted with AES-GCM 256. You choose a backup password here; it is independent of your master password and is the only way to restore the file. The envelope is self-contained and also restores accounts after the vault password was changed or forgotten.
- **Plain text** — downloads a `.txt` file with one `AccountName:SecretKey` line per account, or `AccountName:otpauth://…` when digits, period or algorithm are non-default. The file is readable by anyone who opens it and is not protected by your master password.

**Import**

Click **Import** and pick any of the following:

- a plaintext `.txt` backup;
- an encrypted `.lb2fa` backup — the extension detects the format and asks for the backup password;
- a file or image containing an `otpauth://` QR code, a Google Authenticator migration QR code (`otpauth-migration://offline?data=…`), or a line of text with a Base32 secret or `otpauth://` link.

Already-saved secrets are skipped. HOTP or unsupported entries are skipped and counted. For a multi-part Google Authenticator export, import each QR image separately; accounts already imported are skipped.

---

## How it works

```
Enter a Base32 secret or an otpauth:// link
       ↓
Web Crypto API computes HMAC (SHA-1 by default)
       ↓
6–8 digit TOTP code (RFC 6238)
       ↓
Countdown with automatic refresh
       ↓
One-click copy to clipboard
```

All computation happens locally with the browser's Web Crypto API. Generating a code never makes a network request. Saved data leaves the device only when you explicitly turn on encrypted cross-device sync.

---

## Privacy and permissions

- **Local by default** — saved secrets live in `chrome.storage.local` and never leave the device unless you turn on sync
- **Optional encryption** — without a master password, saved secrets are plaintext. Once enabled, every secret is sealed with AES-GCM 256; the key is derived from your password (PBKDF2-SHA256, 600k iterations) and kept in memory only
- **Opt-in sync** — sealed records, account names, TOTP settings and the vault's salt/iterations/verifier are written to `chrome.storage.sync` and carried by your browser account. The master password and the license key are never included
- **No analytics** — no tracking, telemetry, cookies or third-party scripts
- **No page access** — no content scripts, no access to history, tabs, bookmarks or page content
- **Minimal networking** — without a license the extension makes no network request, apart from retrying a license release that was queued while offline. With a license it contacts `api.annmax1983.com` to activate, to re-verify (at most once every 2 hours when the popup opens) and to release the license. Those requests carry the license key, a random install identifier and browser metadata (browser name/version, languages, time zone, User-Agent); secrets and generated codes are never included
- **Minimal permissions** — `storage` and `clipboardWrite`, plus access to the license server domain. `clipboardWrite` lets the popup copy a code and clear it again; it cannot read the clipboard, and it grants no page access. Sync adds no permission and uses no server of ours

See [privacy-policy.html](privacy-policy.html) for the field-by-field breakdown.

---

## ⚠️ Security notes

- **Encryption is opt-in** — out of the box, secrets are stored unencrypted in the extension's local storage. Anyone with access to your browser profile can read them. Turn on the master password to seal them.
- **No password recovery** — the master password cannot be reset, and sealed records cannot be recovered without it. If you forget it, the only option is to erase everything from the lock screen. Keep an exported backup; choose the encrypted format and store its backup password separately, because the backup password cannot be recovered either.
- **Removing the extension erases local data** — uninstalling the extension or clearing its local storage permanently deletes every account stored on this device. With sync on, a copy remains in your browser account and can be restored by reactivating the license and joining the existing sync with the same master password; use **Delete synced data** first if you want it gone.
- **Sync is not a backup** — deletions propagate. If you delete an account on one device it is deleted on the others. Keep an exported backup of anything you cannot recreate.
- **Browser account trust** — synced data is carried by your browser vendor's sync service. Secrets are sealed with your master password, but account names and TOTP settings are not. Anyone with access to your browser account *and* your master password can read the secrets; enable the browser's sync passphrase to encrypt the transport itself.
- **Export format matters** — a plaintext `.txt` backup is readable by anyone who opens it; treat it as a secret and avoid sharing it. An encrypted `.lb2fa` backup is sealed with the password you chose at export time, which is independent of the master password.
- **Screens and clipboards leak** — QR codes are hidden until you click **Show QR code**, copied codes clear from the clipboard 30 seconds after copying (or when auto-lock engages), and idle auto-lock limits how long an unlocked vault stays on screen. Closing the popup destroys the derived key, but a code copied just before closing stays on the system clipboard like any other copy. None of this protects a compromised computer.
- **Best practice** — delete a secret from the extension once it is in a dedicated authenticator app.

---

## Compatibility

LocalBox2FA implements RFC 6238 TOTP and accepts secrets generated by Google Authenticator, Authy and other mainstream 2FA tools. It is an independent tool and has no official affiliation with those brands.

---

## Source code notice

> ⚠️ **This repository does not publish source code.** It contains usage documentation, release notes and support resources only. The extension is distributed exclusively through the Chrome Web Store; no offline installation package or end-user source code is provided.

---

## License

Copyright © 2026 LocalBox2FA. All rights reserved.

---

## ❤️ Support

If you find LocalBox2FA helpful, consider supporting the project!

**[👉 Support LocalBox2FA](https://annmax1983.github.io/LocalBox2FA/)**
