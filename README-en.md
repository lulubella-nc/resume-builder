**🌐 Language / Langue / Idioma / 语言：** **English** · [Français](README-fr.md) · [Español](README-es.md) · [中文](README.md)

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
