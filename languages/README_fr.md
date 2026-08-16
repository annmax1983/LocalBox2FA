# LocalBox2FA
[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | Français

Une extension légère de navigateur qui génère des codes de vérification TOTP 2FA localement — vos secrets restent entièrement sur votre appareil.

> Basé sur Chromium · Manifest V3 · Traitement local · Confidentialité d'abord

---

## Pourquoi LocalBox2FA ?

La plupart des authentificateurs 2FA nécessitent une application mobile ou une synchronisation cloud. LocalBox2FA s'exécute directement dans votre navigateur — pas de téléphone requis, pas de compte nécessaire, vos données ne quittent jamais votre appareil.

| Avantage | Détail |
|----------|--------|
| 🔒 **Entièrement local** | Tous les calculs TOTP s'effectuent dans votre navigateur via l'API Web Crypto. Vos secrets ne quittent jamais votre appareil. |
| 📱 **Pas de Téléphone** | Générez des codes 2FA directement depuis la barre d'outils du navigateur |
| 🚫 **Pas de Compte** | Sans inscription, sans synchronisation cloud, sans connexion. Installez et utilisez. |
| ⚡ **Instantané** | Codes générés en moins de 10ms. Un clic pour copier. |
| 🌙 **Mode Sombre** | Suit automatiquement la préférence du système |
| 🎯 **Minimal** | Moins de 50 Ko. Sans frameworks, sans dépendances |

---

## Fonctionnalités

### 🆓 Fonctionnalités Gratuites

| Fonctionnalité | Description |
|----------------|-------------|
| 🔐 **Génération TOTP** | Compatible RFC 6238 — fonctionne avec Google Authenticator, Authy et tous les services TOTP |
| ⏱️ **30s Countdown** | Barre de progression visuelle avec transitions de couleur (bleu → orange → rouge) |
| 📋 **Copie en Un Clic** | Copie le code de vérification dans le presse-papiers instantanément |
| 💾 **Sauvegarder & Gérer** | Sauvegardez les clés secrètes avec des noms personnalisés |
| 📋 **Historique en Direct** | Tous les comptes sauvegardés affichent les codes en temps réel |
| 🗑️ **Supprimer un Enregistrement** | Dialogue de confirmation avant la suppression |
| 🔒 **Anti-Dupliquats** | Empêche la sauvegarde de la même clé secrète deux fois |
| 🌙 **Mode Sombre** | Thème automatique selon la préférence du système |
| 🌍 **6 Langues** | Anglais, Chinois, Japonais, Espagnol, Allemand, Français |

### ⭐ Fonctionnalités Premium (Licence Requise)

| Fonctionnalité | Description |
|----------------|-------------|
| 📤 **Exporter les Enregistrements** | Exporte toutes les clés secrètes en fichier texte pour sauvegarde |
| 🗑️ **Effacer Tous les Enregistrements** | Supprimer tous les enregistrements sauvegardés en une fois |

> 💡 Achat unique, licence liée à l'appareil. [Obtenir une Licence →](https://www.annmax1983.com/checkout.html?plugin=localbox2fa)

---



## Preview

<p align="center">
  <img src="images/A02.png" alt="LocalBox2FA Preview">
</p>



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

Tous les calculs s'effectuent localement via l'API Web Crypto du navigateur. Vos secrets ne sont jamais envoyés sur le réseau.

---

## Confidentialité

- ✅ **Les secrets restent sur votre appareil** — Tous les calculs TOTP s'effectuent localement ; les secrets enregistrés ne quittent jamais votre navigateur
- ✅ **Aucune analyse** — Pas de suivi, pas de télémétrie, pas de cookies
- ✅ **Réseau uniquement pour l'activation de la licence** — Si vous activez une licence Premium, votre clé de licence et un identifiant d'appareil minimal sont envoyés au serveur de licence pour vérification. Les fonctions gratuites fonctionnent entièrement hors ligne et n'effectuent aucune requête réseau
- ✅ **Permissions minimales** — `storage` (pour mémoriser l'état de la licence) et accès uniquement au domaine du serveur de licence

---

## Licence

Copyright © 2026 LocalBox2FA. Tous droits réservés.

---

## ❤️ Soutien

Si LocalBox2FA vous est utile, envisagez de soutenir le projet !

**[👉 Soutenir LocalBox2FA](https://annmax1983.github.io/LocalBox2FA/)**
