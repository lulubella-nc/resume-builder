**🌐 Idioma / Language / Langue / 语言：** [English](README-en.md) · [Français](README-fr.md) · **Español** · [中文](README.md)

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
