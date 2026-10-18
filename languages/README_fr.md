# LocalBox2FA

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | Français

Une extension légère qui génère des codes de vérification TOTP 2FA — vos secrets sont générés et stockés entièrement sur votre appareil.

> Chromium · Manifest V3 · Traitement local · Confidentialité avant tout

---

## Nouveautés de la version 1.3.0

| Changement | Détail |
|-----------|--------|
| 🛡️ **Chiffrement par mot de passe maître** | Chiffrement AES-GCM 256 bits facultatif des secrets enregistrés. La clé est dérivée de votre mot de passe par PBKDF2-SHA256 (600 000 itérations + sel aléatoire) et ne réside qu'en mémoire. Demandée à chaque ouverture de la fenêtre |
| 🔓 **Export / import / tout effacer désormais gratuit** | Sauvegarder, restaurer et effacer ses propres secrets relève de la gestion de ses données, pas d'une fonction payante. Seul le transfert par QR code reste Premium |
| 📄 **Politique de confidentialité corrigée** | Elle indique désormais le vrai support de stockage (`chrome.storage.local`), les vrais moments de connexion (activation, au plus une revérification toutes les 2 h à l'ouverture, désactivation) et la vraie liste des champs |

**Mise à jour depuis la v1.2.x ? Rien à faire.** Les enregistrements créés par les versions précédentes restent en clair et fonctionnent exactement comme avant : liste, codes, compte à rebours, export, import et suppression ne changent pas, et la clé de stockage est identique — rien n'est réécrit lors de la mise à jour. Un enregistrement n'est chiffré qu'à partir du moment où vous définissez un mot de passe maître, et il porte alors le préfixe 🔐. Enregistrements en clair et chiffrés peuvent coexister dans une même liste. Aucune migration, aucune réinitialisation, aucune ressaisie.

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
| 🔎 **Rechercher & renommer** | Trouvez n'importe quel compte instantanément, renommez-les à tout moment |
| 🗑️ **Suppression individuelle** | Supprimez des enregistrements individuels avec une boîte de dialogue de confirmation |
| 🔒 **Anti-doublon** | Empêche l'enregistrement de la même clé secrète deux fois |
| 🌙 **Mode sombre** | Thème sombre/clair automatique basé sur la préférence du système |
| 🌍 **6 langues** | English, 中文, 日本語, Español, Deutsch, Français |
| 🛡️ **Chiffrement par mot de passe maître** | Chiffrement AES-GCM 256 facultatif des secrets enregistrés ; clé dérivée par PBKDF2-SHA256 (600 000 itérations), demandée à chaque ouverture |

### ⭐ Premium (licence requise)

| Fonctionnalité | Description |
|---------|-------------|
| 📱 **Affichage QR code** | QR code scannable pour transférer vos comptes vers l'authentificateur de votre téléphone |

> 💡 Achat unique, licence à vie — 2 activations par plugin. Chaque environnement de navigateur compte pour une ; désactivez à tout moment pour libérer une place. [Obtenir une licence →](https://www.annmax1983.com/checkout.html?plugin=localbox2fa)

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
3. Cliquez sur **Charger le package décompressé** et sélectionnez le dossier `LocalBox2FA`
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

### 🔒 Chiffrer vos secrets

Ouvrez **Paramètres (⚙) → Mot de passe maître** et cliquez sur **Activer le chiffrement** :

1. Choisissez et confirmez un mot de passe maître
2. Les secrets déjà enregistrés sont scellés immédiatement et portent désormais le préfixe 🔐 dans la liste
3. À la prochaine ouverture, l'écran de verrouillage apparaît d'abord ; les codes ne s'affichent qu'après saisie du mot de passe

Remarques :

- Le mot de passe maître **ne peut être ni réinitialisé ni récupéré**. Si vous l'oubliez, la seule issue est d'effacer le contenu depuis l'écran de verrouillage et de recommencer — conservez donc une sauvegarde exportée.
- La clé dérivée ne réside qu'en mémoire et disparaît à la fermeture de la fenêtre : c'est pourquoi le mot de passe est demandé à chaque ouverture.
- **Désactiver le chiffrement** dans le même panneau déchiffre tous les enregistrements en clair.

### Exporter et sauvegarder

- Cliquez sur **Exporter** pour télécharger tous les secrets enregistrés dans un fichier `.txt`
- Format : `NomDuCompte:CléSecrète` (une par ligne) ; avec des chiffres/période/algorithme non standard, `NomDuCompte:otpauth://…`
- Conservez ce fichier en lieu sûr — **il est en clair** et n'est pas protégé par votre mot de passe maître

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
- ✅ **Chiffrement au repos facultatif** — Sans mot de passe maître, les secrets sont en clair. Une fois activé, chaque secret est scellé en AES-GCM 256 ; la clé est dérivée de votre mot de passe (PBKDF2-SHA256, 600 000 itérations), ne réside qu'en mémoire et n'est jamais écrite
- ✅ **Pas d'analytics** — Aucun suivi, aucune télémétrie, aucun cookie
- ⚠️ **Réseau minimal et documenté** — Les fonctions gratuites n'émettent **aucune requête réseau**. Avec une licence, l'extension contacte `api.annmax1983.com` pour l'activer, la revérifier (au plus une fois toutes les 2 h à l'ouverture) et la libérer. Ces requêtes contiennent votre clé de licence, un identifiant d'installation aléatoire et des métadonnées navigateur (nom/version, liste des langues, fuseau horaire, User-Agent) — **jamais vos secrets ni les codes générés**
- ✅ **Permissions minimales** — `storage` (pour mémoriser l'état de votre licence) et accès au domaine du serveur de licences uniquement

---

## ⚠️ Notes de sécurité

**Veuillez lire attentivement avant utilisation :**

- **🔑 Le chiffrement est facultatif** — Par défaut, les secrets sont stockés **sans chiffrement** dans le stockage de l'extension (`chrome.storage.local`) ; toute personne ayant accès à votre profil de navigateur peut les lire. Activez le mot de passe maître dans les Paramètres.
- **🚫 Aucune récupération de mot de passe** — Le mot de passe maître ne peut pas être réinitialisé et les enregistrements chiffrés sont irrécupérables sans lui. Si vous l'oubliez, la seule option est d'effacer les enregistrements depuis l'écran de verrouillage et de recommencer. Exportez d'abord une sauvegarde — et conservez-la en lieu sûr, car elle est en clair.
- **💾 Supprimer l'extension = perte de données** — La désinstallation de l'extension ou l'effacement de ses données **supprimera définitivement** tous les comptes sauvegardés. Veuillez exporter un fichier de sauvegarde au préalable.
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
