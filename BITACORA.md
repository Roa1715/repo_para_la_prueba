# Bitácora Informativa del Proyecto — Migración a Tailwind CSS

Registro incremental paso a paso de la construcción y migración de **`repo_para_la_prueba`** desde **Bootstrap 5** hacia **Tailwind CSS**, manteniendo HTML5 semántico, diseño responsive y CSS complementario limpio.

---

## Plan de Construcción Incremental

| Fase | Componente / Objetivo | Estado |
| :--- | :--- | :--- |
| **Paso 1** | Base HTML5 semántica, Tailwind Play CDN, corrección de `style.css` e inicio de bitácora | ✅ Completado |
| **Paso 2** | Encabezado responsive (`<header>` + `<nav>`) y sección portada (Hero Banner) | ⏳ Pendiente |
| **Paso 3** | Grilla principal de 12 columnas (`<main>`) y catálogo de tarjetas (`<section>` + `<article>`) | ⏳ Pendiente |
| **Paso 4** | Barra lateral informativa (`<aside>`) y sección visual de arquitectura semántica | ⏳ Pendiente |
| **Paso 5** | Pie de página completo (`<footer>`), pulido de `style.css` y revisión de accesibilidad | ⏳ Pendiente |
| **Paso 6** | Actualización completa de `README.md` a Tailwind CSS y cierre de bitácora | ⏳ Pendiente |

---

## Registro de Avances

### Entrada #1 — Base Tailwind CSS, corrección de hoja de estilos e inicio de bitácora
- **Fecha y hora:** 2026-11-26 15:46 (-05:00)
- **Archivos modificados / creados:**
  - `index.html`
  - `style.css`
  - `BITACORA.md`

#### ¿Qué se hizo?
1. **Reemplazo de Bootstrap 5 por Tailwind CSS (Play CDN):**
   - Se eliminó `<link href="...bootstrap.min.css">` en `index.html`.
   - Se incorporó `<script src="https://cdn.tailwindcss.com"></script>` junto con una configuración `tailwind.config` personalizada para definir la paleta corporativa `brand` (`50`, `100`, `500`, `600`, `700`, `900`).
2. **Corrección de enlace roto al CSS personalizado:**
   - En la versión original, `index.html` apuntaba a `styles.css`, mientras que el archivo real del repositorio es `style.css`. Se corrigió la referencia a `<link rel="stylesheet" href="style.css">`.
3. **Esqueleto semántico con clases utilitarias de Tailwind:**
   - Se configuró `<body>` con `min-h-screen flex flex-col bg-slate-50 text-slate-800 antialiased` para garantizar que el `<footer>` siempre quede al fondo (sticky footer) y el texto tenga buen contraste.
   - Se dejaron las tres regiones base (`<header>`, `<main>`, `<footer>`) usando contenedores centrados (`max-w-6xl mx-auto px-4`).
4. **Alineación de `style.css` con la paleta de Tailwind (`slate` y `blue`):**
   - Se actualizaron las variables en `:root` (`--color-principal: #2563eb`, `--color-oscuro: #0f172a`) y el degradado de `.hero-banner` para mantener armonía visual con Tailwind.

#### Clases clave de Tailwind introducidas en este paso
- `min-h-screen flex flex-col` + `flex-1` en `<main>` + `mt-auto` en `<footer>`: estructura vertical de pantalla completa sin desbordes.
- `max-w-6xl mx-auto px-4`: reemplaza a `.container` de Bootstrap para centrar el contenido con relleno lateral.
- `bg-slate-50 text-slate-800 antialiased`: fondo neutro suave, tipografía legible y suavizado de fuentes.
- `border border-slate-200 rounded-xl p-6 shadow-sm`: estilo base limpio para contenedores y tarjetas.

#### Cómo explicarlo en la sustentación
> *"Primero migré la base del proyecto de Bootstrap 5 a Tailwind CSS mediante Play CDN, configuré una paleta `brand` en `tailwind.config` y corregí el enlace a `style.css` que antes apuntaba a un nombre inexistente (`styles.css`). Sobre esa base dejé montada la estructura semántica (`header`, `main` y `footer`) usando Flexbox vertical para asegurar un pie de página fijo en la parte inferior."*
