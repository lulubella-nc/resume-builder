**🌐 Langue / Language / Idioma / 语言：** [English](README-en.md) · **Français** · [Español](README-es.md) · [中文](README.md)

# Resume Builder · Atelier de modèles de CV

Un **front-end pur, à usage personnel** : un CV modèle en un seul fichier HTML, avec des mises en page interchangeables et un remplissage automatique. Toutes les données et la configuration sont conservées dans le **localStorage de votre propre navigateur** — aucun backend, rien n'est téléchargé.

## Fonctionnalités

- **HTML en un seul fichier** : ouvrez `index.html` directement dans un navigateur — aucune installation, aucun serveur.
- **12 mises en page, commutation en un clic** : Ingénieur civil, Chef de chantier, Fonctionnaire fédéral, Assistant juridique, Employé postal, Gestionnaire municipal, Ingénieur électricien, Généraliste RH, Ingénieur de projet, Ingénieur de recherche, Ingénieur systèmes, Modèle générique de recherche d'emploi.
- **Téléversement → reconnaissance automatique → remplissage automatique** :
  - Prend en charge les CV **PDF** et **Word (.docx)** ;
  - Les bibliothèques d'analyse sont intégrées dans `lib/` (références locales), donc **l'analyse fonctionne hors ligne** ;
  - Le texte extrait est structuré via une **API compatible OpenAI** (Volcano Ark / DeepSeek / OpenAI / déploiements locaux, etc.) puis **automatiquement inséré dans les sections du modèle** ;
  - Les CV et les photos téléversées prennent en charge l'avatar ; les photos sont automatiquement compressées et utilisées comme avatar.
- **Sections configurables** : choisissez les sections à afficher (Adresse / Compétences / Langues / Références) et renommez des sections comme « Stages » en un titre personnalisé, par exemple **Projets**.
- **Ajustement automatique sur une page** : lorsque le contenu dépasse une page A4, la taille de police, l'interligne et les espacements sont automatiquement réduits pour tenir sur une seule page.
- **Impression / Export PDF** : feuille de style A4 intégrée.

## Comment ouvrir

- Local : ouvrez `index.html` directement dans un navigateur (double-clic). **Téléchargez / déployez avec le dossier `lib/`** — les bibliothèques d'analyse en dépendent.
- Déployé sur GitHub Pages : utilisez la page d'accueil du dépôt (la racine est `index.html`, téléversez aussi `lib/`).

## Configurer l'API du modèle (pour le remplissage automatique)

Remplissez la carte « API du modèle · Remplissage automatique » dans le panneau de droite :

| Champ | Description |
| --- | --- |
| URL de base | p. ex. `https://ark.cn-beijing.volces.com/api/v3` (format compatible OpenAI, se terminant par `/api/v3` etc.) |
| Clé API | Votre propre clé |
| Nom du modèle | p. ex. `doubao-seed-1-6-250615`, `deepseek-chat`, `gpt-4o-mini`, etc. |

Cliquez ensuite sur « Tester la connexion » et téléversez à nouveau votre CV pour remplir automatiquement les sections.

> **Note de confidentialité** : la clé API n'est écrite que dans le `localStorage` de votre propre navigateur et n'est **jamais écrite dans un fichier du dépôt**. La version du dépôt de `index.html` utilise un **espace de noms de stockage distinct** (`resume_public_*`), totalement isolé de votre version locale (`resume_data` / `llm_cfg`) — même ouvert dans le même navigateur, elle ne **chargera jamais votre CV personnel ou votre configuration API enregistrés** ; elle présente toujours le modèle propre (exemple Neil Burrows) avec des champs API vides.

## Où les données sont stockées

- Contenu du CV → `localStorage["resume_public_data"]` du navigateur
- Configuration des sections → `localStorage["resume_public_sections"]` du navigateur
- Configuration de l'API → `localStorage["resume_public_llm_cfg"]` du navigateur

Tout est stocké localement dans le navigateur ; effacé lorsque vous effacez les données du navigateur, jamais téléchargé. La version du dépôt utilise un espace de noms distinct et n'interfère pas avec les autres versions locales.

## Développement / Contribution

Ce dépôt contient un `index.html` autonome (CSS / JS intégrés) et les bibliothèques d'analyse dans `lib/` (pdfjs-dist, mammoth — références locales, utilisables hors ligne). Ouvrez-le localement pour déboguer.
