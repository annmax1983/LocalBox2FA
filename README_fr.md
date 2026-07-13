# LocalBox2FA

[English](README.md) | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | Français

Une extension légère de navigateur qui génère des codes de vérification TOTP 2FA localement — sans upload, entièrement hors ligne.

> Basé sur Chromium · Manifest V3 · 100% Hors ligne · Confidentialité d'abord

---

## Pourquoi LocalBox2FA ?

La plupart des authentificateurs 2FA nécessitent une application mobile ou une synchronisation cloud. LocalBox2FA s'exécute directement dans votre navigateur — pas de téléphone requis, pas de compte nécessaire, vos données ne quittent jamais votre appareil.

| Avantage | Détail |
|----------|--------|
| 🔒 **100% Local** | Tous les calculs TOTP s'effectuent dans votre navigateur via l'API Web Crypto. Aucun upload. |
| 📱 **Pas de Téléphone** | Générez des codes 2FA directement depuis la barre d'outils du navigateur |
| 🚫 **Pas de Compte** | Sans inscription, sans synchronisation cloud, sans connexion. Installez et utilisez. |
| ⚡ **Instantané** | Codes générés en moins de 10ms. Un clic pour copier. |
| 🌙 **Mode Sombre** | Suit automatiquement la préférence du système |
| 🎯 **Minimal** | Moins de 50 Ko. Sans frameworks, sans dépendances |

---

## Fonctionnalités

| Fonctionnalité | Description |
|----------------|-------------|
| 🔐 **Génération TOTP** | Compatible RFC 6238 — fonctionne avec Google Authenticator, Authy et tous les services TOTP |
| ⏱️ **30s Countdown** | Barre de progression visuelle avec transitions de couleur (bleu → orange → rouge) |
| 📋 **Copie en Un Clic** | Copie le code de vérification dans le presse-papiers instantanément |
| 💾 **Sauvegarder & Gérer** | Sauvegardez les clés secrètes avec des noms personnalisés |
| 📋 **Historique en Direct** | Tous les comptes sauvegardés affichent les codes en temps réel |
| 📤 **Exporter** | Exporte toutes les clés secrètes en fichier texte (format nom:clé) |
| 🗑️ **Suppression Sécurisée** | Dialogue de confirmation avant la suppression |
| 🔒 **Anti-Dupliquats** | Empêche la sauvegarde de la même clé secrète deux fois |
| 🌙 **Mode Sombre** | Thème automatique selon la préférence du système |
| 🌍 **6 Langues** | Anglais, Chinois, Japonais, Espagnol, Allemand, Français |

---

## Navigateurs Supportés

| Navigateur | Statut |
|------------|--------|
| Google Chrome | ✅ Entièrement supporté |
| Microsoft Edge | ✅ Entièrement supporté |
| Autres Chromium | ✅ Devrait fonctionner |

---

## Installation

1. Ouvrez la page des extensions du navigateur :
   - **Chrome** : `chrome://extensions/`
   - **Edge** : `edge://extensions/`
2. Activez le **Mode développeur** (en haut à droite)
3. Cliquez sur **Charger l'extension non empaquetée** et sélectionnez le dossier `local-box2-fa`
4. Cliquez sur l'icône 🔐 LocalBox2FA dans la barre d'outils

---

## Utilisation

### Générer un Code

1. Cliquez sur l'icône LocalBox2FA
2. Collez votre clé secrète TOTP (format Base32) dans le champ de saisie
3. Cliquez sur **Générer** — un code à 6 chiffres apparaît avec un countdown de 30s
4. Cliquez sur **Copier** pour copier le code dans le presse-papiers

### Sauvegarder dans l'Historique

1. Après avoir généré un code, cliquez sur **Sauvegarder**
2. Entrez un nom (ex: « GitHub », « Google »)
3. Le compte apparaît dans votre liste d'historique avec le code en direct

### Utiliser les Comptes Sauvegardés

- Tous les comptes sauvegardés affichent les codes en temps réel
- Cliquez sur un compte pour charger son code
- Les codes se rafraîchissent automatiquement toutes les 30 secondes

---

## Comment ça Marche

```
Entrer la clé secrète (Base32)
       ↓
L'API Web Crypto calcule HMAC-SHA1
       ↓
Génère un code TOTP à 6 chiffres (RFC 6238)
       ↓
30 secondes de countdown avec auto-refresh
       ↓
Un clic pour copier dans le presse-papiers
```

Tous les calculs s'effectuent localement via l'API Web Crypto du navigateur. Aucune requête réseau, aucun upload de données.

---

## Confidentialité

- ✅ **Aucun upload de données** — Tous les calculs TOTP s'effectuent localement
- ✅ **Aucune analyse** — Pas de suivi, pas de télémétrie
- ✅ **Aucune requête réseau** — L'extension fonctionne entièrement hors ligne
- ✅ **Stockage local uniquement** — Secrets sauvegardés dans le localStorage du navigateur
- ✅ **Aucune permission** — Le manifest ne déclare aucune permission

---

## Licence

Copyright © 2026 LocalBox2FA. Tous droits réservés.

---

## ❤️ Soutien

Si LocalBox2FA vous est utile, envisagez de soutenir le projet !

**[👉 Soutenir LocalBox2FA](https://annmax1983.github.io/LocalBox2FA/)**
