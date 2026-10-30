<p align="center"><b>切换语言 / Language / Langue / Idioma：</b>&nbsp;
<a href="#zh">中文</a> &nbsp;·&nbsp; <a href="#en">English</a> &nbsp;·&nbsp; <a href="#fr">Français</a> &nbsp;·&nbsp; <a href="#es">Español</a></p>

---

<a id="zh"></a>

# Resume Builder · 简历模板工作台

一个**纯前端、自用**的单文件简历工作台：把一份简历模板做成可替换版式、可自动填充的 HTML 页面。所有数据与配置都保存在**你自己浏览器的 localStorage** 里，不依赖任何后端，也不会上传任何内容。

## 特性

- **单文件 HTML**：`index.html` 一个文件即可在浏览器直接打开使用，无需安装、无需服务器。
- **12 套版式一键切换**：土木工程师、建筑经理、联邦政府职员、律师助理、邮政职员、城市经理、电气工程师、人力资源、项目工程师、研发工程师、系统工程师、通用求职模板。
- **上传自动识别并填充**：
  - 支持 **PDF** 与 **Word（.docx）** 简历；
  - 解析库已内置在 `lib/` 目录（本地引用），**离线也能解析**；
  - 解析出的文本调用 **OpenAI 兼容接口**（火山方舟 / DeepSeek / OpenAI / 本地部署等）结构化后，**自动填入模板各栏目**；
  - 简历 / 上传照片均支持头像，照片自动压缩后作为头像。
- **栏目可配置**：可自行决定显示哪些栏目（联系地址 / 技能 / 语言 / References 推荐），并支持把「实习经历」类栏目改为 **Projects** 等自定义标题。
- **自动适配一页**：内容超出 A4 一页时，自动调整字号、行距、间距，合为一页。
- **打印 / 导出 PDF**：页面已内置 A4 打印样式。

## 打开方式

- 本地：直接用浏览器打开 `index.html`（双击即可）。**请连同 `lib/` 文件夹一起下载 / 部署**，解析库依赖该目录。
- 部署到 GitHub Pages 后，访问仓库主页即可使用（根目录为 `index.html`，`lib/` 一并上传）。

## 配置模型 API（用于自动填充）

右侧面板「模型 API · 自动填充分栏」填写：

| 项 | 说明 |
| --- | --- |
| 接口地址 Base URL | 如 `https://ark.cn-beijing.volces.com/api/v3`（OpenAI 兼容格式，以 `/api/v3` 等结尾） |
| API Key | 你自己的密钥 |
| 模型名 | 如 `doubao-seed-1-6-250615`、`deepseek-chat`、`gpt-4o-mini` 等 |

填好后点「测试连接」，再重新上传简历即可自动填入各栏目。

> **隐私说明**：API Key 只写入你自己浏览器的 `localStorage`，**不会写入任何仓库文件**。仓库版 `index.html` 使用**独立的存储命名空间**（`resume_public_*`），与你本机自用版（`resume_data` / `llm_cfg`）完全隔离——即便用同一浏览器打开，也**绝不会加载你本机已保存的个人简历或 API 配置**，始终以干净模板（Neil Burrows 示例）呈现，API 输入框为空。

## 数据都存哪

- 简历内容 → 浏览器 `localStorage["resume_public_data"]`
- 栏目配置 → 浏览器 `localStorage["resume_public_sections"]`
- API 配置 → 浏览器 `localStorage["resume_public_llm_cfg"]`

均在本地浏览器，随清除浏览器数据而清空，不会上传。仓库版使用独立命名空间，与本机其他版本的数据互不影响。

## 开发 / 贡献

本仓库包含一个自包含的 `index.html`（内联 CSS / JS）及解析库 `lib/`（pdfjs-dist、mammoth，本地引用，离线可用）。本地打开即可调试。

---

<a id="en"></a>

# Resume Builder · Resume Template Workbench

A **pure front-end, personal-use** single-file resume workbench: it turns a resume template into an HTML page with switchable layouts and auto-fill. All data and configuration are stored in **your own browser's localStorage** — no backend, nothing is uploaded.

## Features

- **Single-file HTML**: open `index.html` directly in a browser — no install, no server.
- **12 layouts, one-click switching**: Civil Engineer, Construction Manager, Federal Government Employee, Paralegal, Postal Worker, City Manager, Electrical Engineer, HR Generalist, Project Engineer, Research Engineer, Systems Engineer, General Job-Seeker.
- **Upload → auto-recognize → auto-fill**:
  - Supports **PDF** and **Word (.docx)** resumes;
  - The parsing libraries are bundled in `lib/` (local references), so **parsing works offline**;
  - The extracted text is structured via an **OpenAI-compatible API** (Volcano Ark / DeepSeek / OpenAI / local deployments, etc.) and **auto-filled into the template sections**;
  - Both resumes and uploaded photos support avatars; photos are automatically compressed and used as the avatar.
- **Configurable sections**: decide which sections to show (Address / Skills / Languages / References), and rename sections such as "Internships" to a custom title like **Projects**.
- **Auto-fit to one page**: when content exceeds one A4 page, font size, line-height and spacing are automatically adjusted to fit a single page.
- **Print / Export PDF**: built-in A4 print stylesheet.

## How to open

- Local: open `index.html` directly in a browser (double-click). **Download / deploy together with the `lib/` folder** — the parsing libraries depend on it.
- Deployed on GitHub Pages: use the repo homepage (root is `index.html`, upload `lib/` with it).

## Configure the model API (for auto-fill)

Fill in the "Model API · Auto-Fill" card in the right panel:

| Field | Description |
| --- | --- |
| Base URL | e.g. `https://ark.cn-beijing.volces.com/api/v3` (OpenAI-compatible format, ending with `/api/v3` etc.) |
| API Key | Your own key |
| Model name | e.g. `doubao-seed-1-6-250615`, `deepseek-chat`, `gpt-4o-mini`, etc. |

Then click "Test connection" and re-upload your resume to auto-fill the sections.

> **Privacy note**: The API Key is written only to your own browser's `localStorage` and is **never written to any repository file**. The repo version of `index.html` uses a **separate storage namespace** (`resume_public_*`), fully isolated from your local self-use version (`resume_data` / `llm_cfg`) — even when opened in the same browser, it will **never load your saved personal resume or API configuration**; it always presents the clean template (Neil Burrows sample) with empty API fields.

## Where the data is stored

- Resume content → browser `localStorage["resume_public_data"]`
- Section configuration → browser `localStorage["resume_public_sections"]`
- API configuration → browser `localStorage["resume_public_llm_cfg"]`

All stored locally in the browser; cleared when you clear browser data, never uploaded. The repo version uses a separate namespace and does not interfere with other local versions.

## Development / Contribution

This repo contains a self-contained `index.html` (inline CSS / JS) and the parsing libraries in `lib/` (pdfjs-dist, mammoth — local references, offline-capable). Open it locally to debug.

---

<a id="fr"></a>

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

---

<a id="es"></a>

# Resume Builder · Banco de plantillas de currículum

Un **front-end puro, de uso personal** : un currículum en un único archivo HTML con diseños intercambiables y autocompletado. Todos los datos y la configuración se guardan en el **localStorage de tu propio navegador** — sin backend, nada se sube.

## Características

- **HTML de un solo archivo** : abre `index.html` directamente en un navegador — sin instalación, sin servidor.
- **12 diseños, cambio con un clic** : Ingeniero civil, Director de obra, Empleado del gobierno federal, Asistente legal, Empleado postal, Gerente municipal, Ingeniero eléctrico, Generalista de RR. HH., Ingeniero de proyectos, Ingeniero de investigación, Ingeniero de sistemas, Plantilla general de búsqueda de empleo.
- **Subir → reconocimiento automático → autocompletado** :
  - Compatible con currículums en **PDF** y **Word (.docx)** ;
  - Las librerías de análisis están incluidas en `lib/` (referencias locales), por lo que **el análisis funciona sin conexión** ;
  - El texto extraído se estructura mediante una **API compatible con OpenAI** (Volcano Ark / DeepSeek / OpenAI / despliegues locales, etc.) y se **autocompletan las secciones del modelo** ;
  - Los currículums y las fotos subidas admiten avatar ; las fotos se comprimen automáticamente y se usan como avatar.
- **Secciones configurables** : decide qué secciones mostrar (Dirección / Habilidades / Idiomas / Referencias) y renombra secciones como « Prácticas » a un título personalizado, por ejemplo **Proyectos**.
- **Ajuste automático a una página** : cuando el contenido supera una página A4, el tamaño de letra, el interlineado y los espacios se ajustan automáticamente para caber en una sola página.
- **Imprimir / Exportar PDF** : hoja de estilos A4 integrada.

## Cómo abrir

- Local : abre `index.html` directamente en un navegador (doble clic). **Descarga / despliega junto con la carpeta `lib/`** — las librerías de análisis dependen de ella.
- Desplegado en GitHub Pages : usa la página de inicio del repositorio (la raíz es `index.html`, sube también `lib/`).

## Configurar la API del modelo (para autocompletar)

Rellena la tarjeta « API del modelo · Autocompletado » en el panel derecho :

| Campo | Descripción |
| --- | --- |
| URL base | p. ej. `https://ark.cn-beijing.volces.com/api/v3` (formato compatible con OpenAI, terminando en `/api/v3` etc.) |
| Clave API | Tu propia clave |
| Nombre del modelo | p. ej. `doubao-seed-1-6-250615`, `deepseek-chat`, `gpt-4o-mini`, etc. |

Luego haz clic en « Probar conexión » y vuelve a subir tu currículum para autocompletar las secciones.

> **Nota de privacidad** : la clave API solo se escribe en el `localStorage` de tu propio navegador y **nunca se escribe en ningún archivo del repositorio**. La versión del repositorio de `index.html` usa un **espacio de nombres de almacenamiento separado** (`resume_public_*`), totalmente aislado de tu versión local (`resume_data` / `llm_cfg`) — incluso abierto en el mismo navegador, **nunca cargará tu currículum personal o tu configuración de API guardados** ; siempre presenta la plantilla limpia (ejemplo Neil Burrows) con campos API vacíos.

## Dónde se guardan los datos

- Contenido del currículum → `localStorage["resume_public_data"]` del navegador
- Configuración de secciones → `localStorage["resume_public_sections"]` del navegador
- Configuración de la API → `localStorage["resume_public_llm_cfg"]` del navegador

Todo se guarda localmente en el navegador ; se borra al limpiar los datos del navegador, nunca se sube. La versión del repositorio usa un espacio de nombres separado y no interfiere con otras versiones locales.

## Desarrollo / Contribución

Este repositorio contiene un `index.html` autónomo (CSS / JS integrados) y las librerías de análisis en `lib/` (pdfjs-dist, mammoth — referencias locales, utilizables sin conexión). Ábrelo localmente para depurar.
