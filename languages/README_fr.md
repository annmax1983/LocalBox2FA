# LocalBox2FA

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | Français

Une extension légère qui génère des codes TOTP de double authentification. Vos secrets sont créés et utilisés sur votre appareil — aucun compte pour l'extension, aucune application mobile, aucun serveur de notre part. Si vous voulez les mêmes comptes sur un autre ordinateur, une synchronisation chiffrée facultative peut les transporter via le compte de navigateur que vous utilisez déjà.

> Basée sur Chromium · Manifest V3 · Traitement local · Confidentialité avant tout

---

## Fonctionnalités

### 🆓 Gratuit

| Fonction | Description |
|----------|-------------|
| 🔐 **Codes TOTP** | RFC 6238. Collez un secret Base32 ou un lien `otpauth://totp/...` complet. Prend en charge 6 à 8 chiffres, une période personnalisée et SHA-1 / SHA-256 / SHA-512 (par défaut : 6 chiffres, 30 s, SHA-1). HOTP n'est pas pris en charge. |
| ⏱️ **Compte à rebours en direct** | Chaque compte enregistré affiche son code et son compte à rebours, recalculés à chaque changement de période |
| 📋 **Copie en un clic** | Cliquez sur une ligne ou sur « Copier » pour placer le code courant dans le presse-papiers. Le presse-papiers est vidé 30 secondes après la copie tant que la fenêtre reste ouverte, ou immédiatement lorsque le verrouillage automatique s'active |
| 💾 **Enregistrer et gérer** | Donnez un nom à l'enregistrement, recherchez dans la liste, renommez ou supprimez une entrée |
| 🔒 **Détection des doublons** | Un même secret ne peut pas être enregistré deux fois : casse, espaces et remplissage sont normalisés avant comparaison |
| 📱 **Transfert par QR** | Cliquez sur **Afficher le QR code** pour révéler un code scannable permettant de transférer un compte vers une application d'authentification mobile. Le QR reste masqué par défaut pour éviter les regards indiscrets |
| 🗑️ **Tout effacer** | Supprime tous les comptes enregistrés d'un coup, après confirmation |
| 🛡️ **Mot de passe maître** | Chiffrement AES-GCM 256 facultatif des secrets enregistrés. La clé est dérivée avec PBKDF2-SHA256 (600 000 itérations), reste en mémoire et est demandée à chaque ouverture de la fenêtre |
| 🔁 **Changement de mot de passe** | Re-scellez tous les secrets enregistrés avec un nouveau mot de passe maître à tout moment ; les comptes sont conservés et un coffre synchronisé est également re-chiffré |
| ⏲️ **Verrouillage automatique** | Une fois le chiffrement activé, verrouillez le coffre après 1, 5 ou 15 minutes d'inactivité (par défaut : 5). Fermer la fenêtre efface toujours la clé de la mémoire |
| 📤 **Exporter** | Télécharge tous les secrets dans un fichier `.txt` en clair, ou créez une sauvegarde `.lb2fa` chiffrée par un mot de passe indépendant de votre mot de passe maître |
| 📥 **Importer** | Restaure depuis des fichiers en clair, des sauvegardes `.lb2fa` chiffrées, des liens `otpauth://`, des QR codes de migration Google Authenticator ou des images de QR code. Les entrées en double et non prises en charge sont ignorées |
| 🌙 **Mode sombre** | Suit la préférence claire/sombre du système |
| 🌍 **6 langues** | Anglais, chinois, japonais, espagnol, allemand, français |

> Exporter (en clair ou chiffré), importer, tout effacer et afficher le QR code sont gratuits. Sauvegarder, restaurer, effacer et transférer ses propres secrets relève de la gestion de données, pas d'une fonction payante.

### ⭐ Premium (licence requise)

| Fonction | Description |
|----------|-------------|
| 🔄 **Synchronisation entre appareils** | Synchronisation facultative des comptes enregistrés entre appareils connectés au même compte de navigateur. Les secrets voyagent scellés avec votre mot de passe maître ; la synchronisation s'exécute tant que la fenêtre est ouverte et seuls les vrais conflits vous demandent de choisir. Un panneau d'état affiche l'heure de la dernière synchronisation, le nombre de comptes locaux et synchronisés, l'utilisation du stockage, les conflits en attente et tout état en pause |

> Achat unique, licence à vie — 2 activations par extension. Chaque environnement de navigateur compte pour une ; désactivez à tout moment pour libérer une place. [Obtenir une licence →](https://www.annmax1983.com/checkout.html?plugin=localbox2fa)

---

## Aperçu

<p align="center">
  <img src="../screenshots/A02.png" alt="Aperçu de LocalBox2FA">
</p>

---

## Navigateurs compatibles

| Navigateur | État |
|-----------|------|
| Google Chrome | ✅ Entièrement pris en charge |
| Microsoft Edge | ✅ Entièrement pris en charge |
| Autres navigateurs basés sur Chromium | ✅ Devraient fonctionner |

---

## Installation

| Store | Lien |
|---|---|
| Chrome Web Store | [Installer dans Chrome](https://chromewebstore.google.com/detail/hhhfdioecpkgnplkcdbcdabjodjpimem) |
| Microsoft Edge Add-ons | [Installer dans Edge](https://microsoftedge.microsoft.com/addons/detail/mgmcahbcekbibbldnmgpeajnkphlnpin) |

> Installez uniquement depuis les boutiques officielles ci-dessus — évitez les sites de téléchargement tiers.

---

## Utilisation

### Générer un code

1. Cliquez sur l'icône LocalBox2FA dans la barre d'outils
2. Collez un secret Base32 ou un lien `otpauth://totp/...` complet dans le champ
3. Cliquez sur **Générer** : le code apparaît avec son compte à rebours
4. Cliquez sur **Copier** pour le placer dans le presse-papiers

Un secret Base32 seul utilise les valeurs par défaut (6 chiffres, 30 s, SHA-1). Un lien `otpauth://` complet apporte ses propres chiffres, période et algorithme, ce qui est nécessaire pour les services qui n'utilisent pas les valeurs par défaut.

### Enregistrer un compte

1. Après avoir généré un code, cliquez sur **Enregistrer**
2. Saisissez un nom (par exemple « GitHub » ou « Google »)
3. Le compte apparaît dans la liste avec son code et son compte à rebours en direct

### Utiliser les comptes enregistrés

- Cliquez sur un compte pour copier son code courant
- Utilisez le champ de recherche pour filtrer une longue liste
- L'icône crayon renomme, l'icône ✕ supprime après confirmation
- **Tout effacer**, en bas, supprime tous les enregistrements

### Transférer un compte sur mobile

Cliquez sur l'icône ▣ d'un compte enregistré, puis sur **Afficher le QR code**. Le QR reste masqué jusqu'à ce que vous le demandiez, pour ne pas être exposé lorsque la fenêtre s'ouvre sur un écran partagé. Scannez-le avec une application d'authentification mobile pour y importer le compte ; le QR est abandonné à la fermeture de la boîte de dialogue.

### Chiffrer vos secrets

Ouvrez **Paramètres (⚙) → Mot de passe maître** et cliquez sur **Activer le chiffrement** :

1. Choisissez un mot de passe maître et confirmez-le
2. Tous les secrets enregistrés sont immédiatement scellés ; seules les métadonnées (nom, chiffres, période, algorithme, horodatages et identifiants aléatoires d'enregistrement/appareil) restent lisibles
3. Dès lors, l'écran de verrouillage demande le mot de passe avant d'afficher le moindre code

Remarques :

- Le mot de passe **ne peut être ni réinitialisé ni récupéré**. Si vous l'oubliez, l'écran de verrouillage propose de tout effacer et de recommencer : gardez donc une sauvegarde exportée.
- La clé dérivée ne vit qu'en mémoire et disparaît à la fermeture de la fenêtre — c'est pourquoi le mot de passe est demandé à chaque ouverture.
- Chaque secret scellé est lié à son enregistrement : un texte chiffré copié sur un autre compte ne peut pas être ouvert, une copie synchronisée falsifiée ne peut donc pas faire pointer un nom familier vers un autre secret.
- **Désactiver le chiffrement** déchiffre tous les enregistrements en clair. Si un seul enregistrement ne peut pas être déchiffré, l'opération est refusée, les comptes concernés sont listés et rien n'est modifié : supprimez-les d'abord et réessayez.
- Les enregistrements scellés portent le préfixe 🔐 dans la liste ; un enregistrement indéchiffrable affiche aussi 🔐 à la place d'un code.
- **Verrouillage automatique** est disponible dès que le chiffrement est actif. Choisissez **Désactivé**, **1 minute**, **5 minutes** (par défaut) ou **15 minutes** dans **Paramètres → Sécurité** ; après ce délai d'inactivité, le coffre se verrouille, les boîtes de dialogue sensibles se ferment et le presse-papiers est vidé.

**Changer le mot de passe maître**

Ouvrez **Paramètres (⚙) → Mot de passe maître → Changer le mot de passe maître**, saisissez le mot de passe actuel, puis deux fois le nouveau. Tous les secrets enregistrés sont re-chiffrés sur cet appareil ; les comptes sont conservés. Si la synchronisation est active, la copie cloud est également re-scellée. Les autres appareils signalent alors une incohérence de coffre : ils peuvent adopter la copie cloud en saisissant le nouveau mot de passe (leurs comptes locaux sont d'abord effacés) ou remplacer la copie cloud par leur propre coffre avec l'ancien mot de passe. Aucun des deux choix ne se fait automatiquement. Le changement est refusé tant qu'un conflit de synchronisation existe ou qu'un re-scellement est encore en attente. Un re-scellement interrompu est retenté lors d'une synchronisation ultérieure ; tant qu'il n'est pas terminé, aucun autre changement de mot de passe n'est possible.

### Synchroniser entre appareils (Premium)

La synchronisation transporte les comptes enregistrés entre ordinateurs connectés au même compte de navigateur. Elle reste **désactivée tant que vous ne l'activez pas**, exige un mot de passe maître et une licence active.

**Premier appareil**

1. Ouvrez **Paramètres (⚙) → Synchronisation entre appareils** et cliquez sur **Activer la synchronisation**
2. Consultez l'écran de consentement : il indique combien de comptes seront envoyés et ce que le fournisseur du navigateur peut voir
3. Confirmez. Les enregistrements sont scellés et écrits dans `chrome.storage.sync`

**Second appareil**

1. Connectez le navigateur au même compte et installez LocalBox2FA
2. Ouvrez **Paramètres → Synchronisation entre appareils → Rejoindre une synchronisation existante**
3. Saisissez le **même mot de passe maître** que sur le premier appareil

L'extension ne synchronise jamais le mot de passe ni une clé dérivée. Le second appareil ne reçoit que le sel, le nombre d'itérations et le vérificateur du coffre, vérifie le mot de passe avec eux et scelle les enregistrements locaux en clair avec la même clé. Un mot de passe erroné est refusé avant toute fusion.

**Pourquoi la fusion reste sûre**

- Chaque enregistrement possède sa propre clé de stockage et un identifiant stable, plus un marqueur de suppression explicite (tombstone) : une clé absente ne signifie jamais « supprimé », et un appareil ne peut pas effacer les ajouts d'un autre en réécrivant toute la liste
- Avant d'écraser un enregistrement, l'extension relit la dernière copie du cloud ; si un autre appareil l'a modifié ou supprimé entre-temps, l'envoi est reporté et l'écart est signalé comme un vrai conflit
- Une comparaison à trois voies (dernier état synchronisé / local / distant) applique automatiquement les changements sans conflit
- Si le même compte a réellement été modifié sur deux appareils, une boîte de dialogue vous demande de garder **cet appareil**, **l'autre appareil** ou **les deux** : rien n'est écrasé sans votre choix
- Lors d'une fusion, un appareil doté d'un **mot de passe maître différent** n'écrase jamais le coffre synchronisé ; il signale une incohérence de coffre et attend un choix explicite
- Gardez tous les appareils partageant un coffre sur la même version de l'extension ; une version antérieure peut ne pas reconnaître le format scellé actuel et remplacer des enregistrements par des copies plus anciennes

**Remarques**

- Le panneau de synchronisation affiche la dernière synchronisation réussie, le nombre de comptes locaux et synchronisés, une barre d'utilisation du quota de synchronisation du navigateur (octets et nombre d'éléments), les conflits en attente et tout état en pause ou en erreur. Un badge de pause signifie que la synchronisation ne progressera pas tant que vous n'aurez pas traité le message affiché en dessous.
- La synchronisation s'exécute à l'ouverture de la fenêtre (après déverrouillage) et lorsqu'un autre appareil modifie les données ; il n'y a pas de bouton « Synchroniser maintenant »
- La désactiver conserve la copie cloud pour vos autres appareils. Utilisez **Supprimer les données synchronisées** dans le même panneau pour la retirer du compte du navigateur ; les autres appareils conservent leurs comptes locaux et désactivent la synchronisation dès qu'ils constatent la disparition de la copie cloud
- Le chiffrement ne peut pas être désactivé tant que la synchronisation est active, car les enregistrements en clair ne sont jamais envoyés
- La clé de licence n'est pas synchronisée ; chaque appareil s'active séparément
- Les données sont transportées par le service de synchronisation de votre compte de navigateur (Google ou Microsoft, selon le navigateur). Les noms de compte et les réglages TOTP sont lisibles par ce service ; les secrets sont scellés avec AES-GCM et votre mot de passe maître. Pour chiffrer aussi le transport de bout en bout, activez la phrase secrète de synchronisation du navigateur (Chrome : *Synchronisation et services Google → Options de chiffrement*)
- Les quotas de synchronisation du navigateur s'appliquent (environ 100 Ko au total, 8 Ko par élément) ; l'extension signale une erreur de quota plutôt que de supprimer silencieusement des enregistrements

### Exporter et importer

**Exporter**

Cliquez sur **Exporter** et choisissez l'un des deux formats :

- **Sauvegarde chiffrée** — télécharge un fichier `.lb2fa` chiffré en AES-GCM 256. Vous choisissez ici un mot de passe de sauvegarde ; il est indépendant de votre mot de passe maître et constitue le seul moyen de restaurer le fichier. L'enveloppe est autonome et restaure aussi les comptes après un changement ou un oubli du mot de passe du coffre.
- **Texte en clair** — télécharge un fichier `.txt` avec une ligne `NomDuCompte:Secret` par compte, ou `NomDuCompte:otpauth://…` lorsque les chiffres, la période ou l'algorithme ne sont pas ceux par défaut. Quiconque l'ouvre peut le lire ; il n'est pas protégé par votre mot de passe maître.

**Importer**

Cliquez sur **Importer** et choisissez l'une des sources suivantes :

- une sauvegarde `.txt` en clair ;
- une sauvegarde `.lb2fa` chiffrée — l'extension détecte le format et demande le mot de passe de sauvegarde ;
- un fichier ou une image contenant un QR code `otpauth://`, un QR code de migration Google Authenticator (`otpauth-migration://offline?data=…`), ou une ligne de texte avec un secret Base32 ou un lien `otpauth://`.

Les secrets déjà enregistrés sont ignorés. Les entrées HOTP ou non prises en charge sont ignorées et comptées. Pour une exportation Google Authenticator en plusieurs parties, importez chaque image QR séparément ; les comptes déjà importés sont ignorés.

---

## Fonctionnement

1. Saisissez une clé de configuration ou collez un lien otpauth:// complet.
2. Le code est généré sur votre appareil avec le chiffrement intégré au navigateur.
3. Un code de 6 à 8 chiffres s'affiche avec son compte à rebours et se renouvelle de lui-même.
4. Un seul clic le copie dans votre presse-papiers.

Tous les calculs sont effectués localement via l'API Web Crypto du navigateur. Générer un code ne déclenche aucune requête réseau. Les données enregistrées ne quittent l'appareil que si vous activez explicitement la synchronisation chiffrée.

---

## Confidentialité et autorisations

- **Local par défaut** — les secrets enregistrés résident dans `chrome.storage.local` et ne quittent pas l'appareil sauf si vous activez la synchronisation
- **Chiffrement facultatif** — sans mot de passe maître, les secrets sont en clair. Une fois activé, chaque secret est scellé en AES-GCM 256 ; la clé est dérivée de votre mot de passe (PBKDF2-SHA256, 600k itérations) et conservée uniquement en mémoire
- **Synchronisation sur consentement** — les enregistrements scellés, les noms de compte, les réglages TOTP et le sel/itérations/vérificateur du coffre sont écrits dans `chrome.storage.sync` et transportés par votre compte de navigateur. Le mot de passe maître et la clé de licence n'y figurent jamais
- **Aucune analyse** — pas de pistage, de télémétrie, de cookies ni de scripts tiers
- **Aucun accès aux pages** — pas de content scripts, pas d'accès à l'historique, aux onglets ou aux favoris
- **Réseau minimal** — sans licence, l'extension n'effectue aucune requête réseau, hormis la nouvelle tentative de libération d'une licence mise en file hors ligne. Avec une licence, elle contacte `api.annmax1983.com` pour l'activer, la revérifier (au plus une fois toutes les 2 heures à l'ouverture de la fenêtre) et la libérer. Ces requêtes contiennent la clé de licence, un identifiant d'installation aléatoire et des métadonnées de navigateur (nom/version, langues, fuseau horaire, User-Agent) ; les secrets et les codes générés n'y figurent jamais
- **Autorisations minimales** — `storage` et `clipboardWrite`, plus l'accès au domaine du serveur de licences. `clipboardWrite` permet à la fenêtre de copier un code puis de l'effacer ; elle ne peut pas lire le presse-papiers et n'obtient aucun accès aux pages. La synchronisation n'ajoute aucune autorisation et n'utilise aucun serveur de notre part

Le détail champ par champ figure dans [privacy-policy.html](../privacy-policy.html).

---

## ⚠️ Notes de sécurité

- **Le chiffrement est facultatif** — par défaut, les secrets sont stockés sans chiffrement dans le stockage local de l'extension. Quiconque a accès à votre profil de navigateur peut les lire. Activez le mot de passe maître pour les sceller.
- **Aucune récupération de mot de passe** — le mot de passe maître ne peut pas être réinitialisé et les enregistrements scellés sont irrécupérables sans lui. Si vous l'oubliez, la seule option est de tout effacer depuis l'écran de verrouillage. Gardez une sauvegarde exportée ; choisissez le format chiffré et conservez son mot de passe de sauvegarde séparément, car ce mot de passe non plus ne peut pas être récupéré.
- **Retirer l'extension efface les données locales** — la désinstallation ou l'effacement du stockage local supprime définitivement tous les comptes de cet appareil. Si la synchronisation est active, une copie reste dans votre compte de navigateur et peut être restaurée en réactivant la licence et en rejoignant la synchronisation existante avec le même mot de passe maître ; utilisez d'abord **Supprimer les données synchronisées** si vous voulez qu'elle disparaisse.
- **La synchronisation n'est pas une sauvegarde** — les suppressions se propagent : supprimer un compte sur un appareil le supprime sur les autres. Gardez une sauvegarde exportée de tout ce que vous ne pouvez pas recréer.
- **Confiance dans le compte du navigateur** — les données synchronisées sont transportées par le service de synchronisation de votre fournisseur de navigateur. Les secrets sont scellés avec votre mot de passe maître, mais pas les noms de compte ni les réglages TOTP. Quiconque a accès à votre compte de navigateur *et* à votre mot de passe maître peut lire les secrets ; activez la phrase secrète de synchronisation pour chiffrer aussi le transport.
- **Le format d'export compte** — une sauvegarde `.txt` en clair est lisible par quiconque l'ouvre ; traitez-la comme un secret et ne la partagez pas. Une sauvegarde `.lb2fa` chiffrée est scellée avec le mot de passe choisi au moment de l'export, indépendant du mot de passe maître.
- **Les écrans et les presse-papiers fuient** — les QR codes restent masqués jusqu'à ce que vous cliquiez sur **Afficher le QR code**, les codes copiés sont effacés du presse-papiers 30 secondes après la copie (ou lorsque le verrouillage automatique s'active), et le verrouillage automatique limite la durée pendant laquelle un coffre déverrouillé reste à l'écran. La fermeture de la fenêtre détruit la clé dérivée, mais un code copié juste avant reste dans le presse-papiers du système comme n'importe quelle autre copie. Rien de tout cela ne protège un ordinateur compromis.
- **Bonne pratique** — supprimez un secret de l'extension une fois qu'il est dans une application d'authentification dédiée.

---

## Compatibilité

LocalBox2FA implémente RFC 6238 TOTP et accepte les secrets générés par Google Authenticator, Authy et d'autres outils 2FA courants. C'est un outil indépendant, sans affiliation officielle avec ces marques.

---

## Avis sur le code source

> ⚠️ **Ce dépôt ne publie pas de code source.** Il contient uniquement la documentation d'utilisation, les notes de version et les ressources de support. L'extension est distribuée exclusivement via le Chrome Web Store ; aucun paquet d'installation hors ligne ni code source utilisateur n'est fourni.

---

## Licence

Copyright © 2026 LocalBox2FA. Tous droits réservés.

---

## ❤️ Soutenir

Si LocalBox2FA vous est utile, vous pouvez soutenir le projet !

**[👉 Soutenir LocalBox2FA](https://annmax1983.github.io/LocalBox2FA/)**
