# LocalBox2FA

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | Français

Une extension légère qui génère des codes de vérification TOTP 2FA — vos secrets sont générés et stockés entièrement sur votre appareil.

> Chromium · Manifest V3 · Traitement local · Confidentialité avant tout

---

## Pourquoi LocalBox2FA ?

La plupart des applications d'authentification 2FA nécessitent une application mobile ou une synchronisation cloud. LocalBox2FA fonctionne directement dans votre navigateur — pas besoin de téléphone, pas de compte requis, et vos secrets ne quittent jamais votre machine.

| Avantage | Détail |
|-----------|--------|
| 🔒 **100 % local** | Tout le calcul TOTP se fait dans votre navigateur via le Web Crypto API. Les secrets ne quittent jamais votre appareil. |
| 📱 **Pas besoin de téléphone** | Générez vos codes 2FA directement depuis la barre d'outils — aucune application mobile requise. |
| 🚫 **Pas de compte** | Pas d'inscription, pas de synchronisation cloud, pas de connexion. Installez et utilisez. |
| ⚡ **Instantané** | Les codes se génèrent en moins de 10 ms. Un clic pour copier dans le presse-papiers. |
| 🌙 **Mode sombre** | Suit automatiquement la préférence de mode sombre de votre système. |
| 🎯 **Minimal** | Pas de frameworks, pas de dépendances, pas de superflu. |

---

## Fonctionnalités

### 🆓 Gratuit

| Fonctionnalité | Description |
|---------|-------------|
| 🔐 **Génération de codes TOTP** | Compatible RFC 6238 — accepte les clés secrètes de Google Authenticator, Authy et tous les services TOTP standard |
| ⏱️ **Compte à rebours 30s** | Barre de progression visuelle avec transitions de couleur (bleu → orange → rouge) |
| 📋 **Copie en un clic** | Copiez le code de vérification dans le presse-papiers instantanément |
| 💾 **Sauvegarde et gestion** | Enregistrez les clés secrètes avec des noms personnalisés, cliquez pour recharger à tout moment |
| 📋 **Historique en direct** | Tous les comptes sauvegardés affichent les codes en temps réel et les comptes à rebours |
| 🗑️ **Suppression individuelle** | Supprimez des enregistrements individuels avec une boîte de dialogue de confirmation |
| 🔒 **Anti-doublon** | Empêche l'enregistrement de la même clé secrète deux fois |
| 🌙 **Mode sombre** | Thème sombre/clair automatique basé sur la préférence du système |
| 🌍 **6 langues** | English, 中文, 日本語, Español, Deutsch, Français |

### ⭐ Premium (licence requise)

| Fonctionnalité | Description |
|---------|-------------|
| 📤 **Exporter les enregistrements** | Exportez tous les secrets en fichier texte (format nom:secret) pour sauvegarde |
| 🗑️ **Tout supprimer** | Supprimez en masse tous les enregistrements sauvegardés d'un coup |

> 💡 Achat unique, licence liée à l'appareil. [Obtenir une licence →](https://www.annmax1983.com/checkout.html?plugin=localbox2fa)

---

## Avis de compatibilité

Cette extension est conforme au standard TOTP RFC 6238 et prend en charge les clés secrètes générées par Google Authenticator, Authy et les autres outils 2FA grand public. C'est un outil indépendant sans affiliation officielle avec les marques mentionnées.

---

## Aperçu

<p align="center">
  <img src="images/A02.png" alt="Aperçu LocalBox2FA">
</p>

---

## Navigateurs compatibles

| Navigateur | Statut |
|---------|--------|
| Google Chrome | ✅ Entièrement pris en charge |
| Microsoft Edge | ✅ Entièrement pris en charge |
| Autres navigateurs basés sur Chromium | ✅ Devrait fonctionner |

---

## Installation

1. Ouvrez la page des extensions de votre navigateur :
   - **Chrome** : `chrome://extensions/`
   - **Edge** : `edge://extensions/`
2. Activez le **mode Développeur** (bouton en haut à droite)
3. Cliquez sur **Charger le package décompressé** et sélectionnez le dossier `local-box2-fa`
4. Cliquez sur l'icône 🔐 LocalBox2FA dans votre barre d'outils pour commencer

---

## Utilisation

### Générer un code

1. Cliquez sur l'icône LocalBox2FA dans votre barre d'outils
2. Collez votre clé secrète TOTP (format Base32) dans le champ de saisie
3. Cliquez sur **Générer** — un code à 6 chiffres apparaît avec un compte à rebours de 30s
4. Cliquez sur **Copier** pour copier le code dans le presse-papiers

### Enregistrer dans l'historique

1. Après avoir généré un code, cliquez sur **Enregistrer**
2. Saisissez un nom (ex. « GitHub », « Google »)
3. Le compte apparaît dans votre historique avec un code en direct

### Utiliser les comptes sauvegardés

- Tous les comptes sauvegardés affichent les codes en temps réel et les comptes à rebours
- Cliquez sur un compte pour charger son code dans l'affichage principal
- Les codes se rafraîchissent automatiquement toutes les 30 secondes

### Exporter et sauvegarder

- Cliquez sur **Exporter** pour télécharger tous les secrets sauvegardés en fichier `.txt`
- Format : `NomDuCompte:CléSecrète` (un par ligne)
- Conservez ce fichier en lieu sûr — il contient vos clés secrètes

---

## Fonctionnement

```
Saisie de la clé secrète (Base32)
       ↓
Le Web Crypto API calcule le HMAC-SHA1
       ↓
Génère un code TOTP à 6 chiffres (RFC 6238)
       ↓
Compte à rebours de 30 secondes avec rafraîchissement automatique
       ↓
Copie en un clic dans le presse-papiers
```

Tous les calculs se font en local via le Web Crypto API du navigateur. Vos secrets ne font jamais de requête réseau.

---

## Confidentialité

LocalBox2FA a été conçu avec la confidentialité comme principe fondamental :

- ✅ **Les secrets restent sur votre appareil** — Tout le calcul TOTP se fait en local ; les secrets sauvegardés ne quittent jamais votre navigateur
- ✅ **Pas d'analytics** — Aucun suivi, aucune télémétrie, aucun cookie
- ✅ **Réseau uniquement pour l'activation de la licence** — Si vous activez une licence Premium, votre clé de licence et un identifiant minimal de l'appareil sont envoyés au serveur de licences pour vérification. Les fonctionnalités gratuites fonctionnent entièrement hors ligne et ne font jamais de requête réseau.
- ✅ **Permissions minimales** — `storage` (pour mémoriser l'état de votre licence) et accès au domaine du serveur de licences uniquement

---

## ⚠️ Notes de sécurité

**Veuillez lire attentivement avant utilisation :**

- **🔑 Stockage en clair** — Les clés secrètes sont stockées dans le `localStorage` du navigateur **sans chiffrement**. Toute personne ayant accès à votre profil de navigateur peut consulter toutes les clés sauvegardées.
- **💾 Effacer les données = perte de données** — L'effacement du cache ou des données de site du navigateur **supprimera définitivement** tous les comptes sauvegardés. Veuillez exporter un fichier de sauvegarde au préalable.
- **📄 Le fichier d'export est non chiffré** — Le fichier `.txt` exporté contient les clés secrètes en clair. Stockez-le de manière sécurisée et évitez le partage public.
- **🛡️ Bonne pratique** — Supprimez les secrets sauvegardés de l'extension après les avoir transférés vers une application d'authentification dédiée.

---

## Avis sur le code source

> ⚠️ **Ce dépôt ne publie pas le code source.** Il contient uniquement la documentation d'utilisation, les notes de version et les ressources d'assistance. L'extension est distribuée exclusivement via le Chrome Web Store. Aucun package d'installation hors ligne ni code source destiné aux utilisateurs finaux n'est fourni.

---

## Licence

Copyright © 2026 LocalBox2FA. Tous droits réservés.

---

## ❤️ Soutenir

Si LocalBox2FA vous est utile, n'hésitez pas à soutenir le projet !

**[👉 Soutenir LocalBox2FA](https://annmax1983.github.io/LocalBox2FA/)**
