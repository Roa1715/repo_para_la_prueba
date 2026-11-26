# Bitácora Informativa del Proyecto — Migración a Tailwind CSS

Registro detallado fase por fase de la migración y construcción de **`repo_para_la_prueba`** desde **Bootstrap 5** hacia **Tailwind CSS**, conservando HTML5 semántico, diseño responsive, accesibilidad y CSS personalizado complementario.

---

## Resumen de Fases

| Fase | Componente / Objetivo | Estado |
| :--- | :--- | :--- |
| **Paso 1** | Base HTML5 semántica, Tailwind Play CDN, corrección de `style.css` e inicio de bitácora | ✅ Completado |
| **Paso 2** | Encabezado responsive (`<header>` + `<nav>`) y sección portada (Hero Banner) | ✅ Completado |
| **Paso 3** | Grilla principal de 12 columnas (`<main>`) y catálogo de tarjetas (`<section>` + `<article>`) | ✅ Completado |
| **Paso 4** | Barra lateral informativa (`<aside>`) y sección visual de arquitectura semántica | ✅ Completado |
| **Paso 5** | Pie de página completo (`<footer>`), pulido de `style.css` y revisión de accesibilidad | ✅ Completado |
| **Paso 6** | Actualización completa de `README.md` a Tailwind CSS y cierre de bitácora | ✅ Completado |

---

## Registro Detallado de Avances

### Entrada #1 — Base Tailwind CSS, corrección de hoja de estilos e inicio de bitácora
- **Fecha:** 2026-11-26 (Commit `7bd14db`)
- **Archivos:** `index.html`, `style.css`, `BITACORA.md`

#### ¿Qué se hizo?
1. **Reemplazo de Bootstrap 5 por Tailwind CSS (Play CDN):** se eliminó el CDN de Bootstrap y se agregó `https://cdn.tailwindcss.com` con `tailwind.config` para extender la paleta personalizada `brand`.
2. **Corrección de enlace roto:** `index.html` antes apuntaba a `styles.css`, pero el archivo real es `style.css`. Se corrigió la referencia.
3. **Estructura base vertical:** en `<body>` se usó `min-h-screen flex flex-col bg-slate-50 text-slate-800 antialiased` para garantizar un *sticky footer* y tipografía legible.

#### Cómo explicarlo en la sustentación
> *"Primero migré la base de Bootstrap 5 a Tailwind CSS vía Play CDN, definí una paleta propia `brand` en `tailwind.config` y corregí el enlace a `style.css`."*

---

### Entrada #2 — Encabezado responsive (`<header>` + `<nav>`) y Hero Banner
- **Fecha:** 2026-11-26
- **Archivos:** `index.html`, `style.css`

#### ¿Qué se hizo?
1. **Barra superior fija y semántica:** `<header>` con `sticky top-0 z-40 bg-brand-900/95 backdrop-blur` mantiene la navegación visible al hacer scroll.
2. **Navegación responsive:** en escritorio (`hidden md:flex`) muestra los enlaces horizontales; en móvil aparece un botón accesible (`aria-expanded`, `aria-controls`) que despliega `#menu-movil` con un pequeño script de JavaScript.
3. **Sección Hero (`<section id="inicio" class="hero-banner">`):** se ubicó el único `<h1>` principal de la página sobre una imagen de fondo con degradado oscuro (`linear-gradient`) para asegurar contraste y dos botones de llamada a la acción.

#### Clases clave de Tailwind usadas
- `sticky top-0 z-40 backdrop-blur`: encabezado fijo con leve transparencia.
- `hidden md:flex` / `md:hidden`: alternancia limpia entre menú móvil y escritorio (*mobile-first*).
- `text-3xl sm:text-4xl md:text-5xl font-extrabold`: tipografía escalable según el ancho de pantalla.

#### Cómo explicarlo en la sustentación
> *"Construí un `<header>` fijo y responsive con navegación adaptable a móvil, y reservé el único `<h1>` para la portada `.hero-banner`, combinando Tailwind con un degradado oscuro en `style.css` para garantizar el contraste."*

---

### Entrada #3 — Grilla principal de 12 columnas y tarjetas (`<section>` + `<article>`)
- **Fecha:** 2026-11-26
- **Archivos:** `index.html`

#### ¿Qué se hizo?
1. **Layout principal 8/4 en escritorio:** dentro de `<main>` se aplicó `grid grid-cols-1 lg:grid-cols-12 gap-8`, asignando `lg:col-span-8` al contenido principal y `lg:col-span-4` a la barra lateral. En móvil se apila automáticamente en 1 columna.
2. **Catálogo con 4 tarjetas `<article>`:** dentro de `<section id="catalogo">` se creó una subgrilla `grid-cols-1 md:grid-cols-2 gap-6`.
3. **Imágenes uniformes y botones alineados:** cada tarjeta usa `.img-tarjeta` (`object-fit: cover`, altura fija de `200px`), `loading="lazy"`, `alt` descriptivo, `flex flex-col h-full` y `mt-auto` en el enlace inferior para que todos los botones queden a la misma altura.

#### Equivalencias clave (Bootstrap 5 → Tailwind CSS)
- `row g-4` → `grid gap-8`
- `col-lg-8` / `col-lg-4` → `lg:col-span-8` / `lg:col-span-4`
- `col-md-6` → `md:grid-cols-2` (definido en el contenedor padre)
- `card h-100 shadow-sm` → `bg-white border border-slate-200 rounded-xl shadow-sm flex flex-col h-full`

#### Cómo explicarlo en la sustentación
> *"Reemplacé el sistema de grillas de Bootstrap por CSS Grid en Tailwind (`lg:grid-cols-12`, `lg:col-span-8` y `md:grid-cols-2`), organizando cada tarjeta como un `<article>` autónomo con imágenes recortadas uniformemente (`object-fit: cover`) y botones alineados mediante `mt-auto`."*

---

### Entrada #4 — Barra lateral informativa (`<aside>`) y sección de arquitectura
- **Fecha:** 2026-11-26
- **Archivos:** `index.html`

#### ¿Qué se hizo?
1. **Panel lateral `<aside class="lg:col-span-4 space-y-6">`:** agrupa información complementaria en 3 bloques diferenciados:
   - Resumen técnico con lista dividida (`divide-y divide-slate-100`).
   - Navegación por categorías con efecto `hover:bg-slate-50 hover:text-brand-600`.
   - Tarjeta destacada de tip para sustentación (`bg-brand-50 border-brand-100`).
2. **Sección `<section id="arquitectura">`:** explica visualmente en una grilla `sm:grid-cols-2` qué papel cumple cada etiqueta HTML5 de la misma página.

#### Cómo explicarlo en la sustentación
> *"Usé `<aside>` para la información de apoyo (resumen técnico, categorías y notas), evitando mezclarla con el catálogo principal, y agregué una sección `<section id="arquitectura">` que documenta visualmente la semántica del documento."*

---

### Entrada #5 — Pie de página (`<footer>`), pulido de `style.css` y accesibilidad
- **Fecha:** 2026-11-26
- **Archivos:** `index.html`, `style.css`

#### ¿Qué se hizo?
1. **`<footer id="contacto">` estructurado:** grilla `grid-cols-1 md:grid-cols-3 gap-8` con descripción del proyecto, enlaces rápidos, etiquetas de tecnologías y barra inferior de cierre.
2. **Mejoras en `style.css`:**
   - `scroll-margin-top: 5rem` en secciones con `id` para que el encabezado fijo (`sticky`) no tape los títulos al navegar por anclas (`#catalogo`, `#arquitectura`, `#contacto`).
   - `:focus-visible` con borde de alto contraste para navegación por teclado.
   - `@media (prefers-reduced-motion: reduce)` para desactivar animaciones si el usuario tiene activada esa preferencia en su sistema operativo.
3. **Revisión de accesibilidad:** jerarquía estricta `h1` → `h2` → `h3`, `aria-label` en navegaciones y `<aside>`, `aria-labelledby` en secciones, y `alt` descriptivo en todas las imágenes.

#### Cómo explicarlo en la sustentación
> *"Cerré el documento con un `<footer>` de 3 columnas responsive y refiné `style.css` pensando en experiencia real y accesibilidad: `scroll-margin-top` para el header fijo, foco visible con teclado y soporte para `prefers-reduced-motion`."*

---

### Entrada #6 (Cierre) — Actualización de `README.md` a Tailwind CSS y verificación final
- **Fecha:** 2026-11-26
- **Archivos:** `README.md`, `BITACORA.md`

#### ¿Qué se hizo?
1. Se reescribió `README.md` para reflejar el proyecto actual en **HTML5 Semántico + Tailwind CSS + CSS Personalizado** (en lugar de Bootstrap 5).
2. Se incluyó una tabla de equivalencias **Bootstrap 5 → Tailwind CSS**, explicación actualizada de `style.css`, referencia directa a `BITACORA.md` y un guion de sustentación actualizado.
3. Se consolidó esta bitácora marcando todas las fases como completadas.

#### Resumen de la migración
- **Antes:** Bootstrap 5 CDN + `styles.css` roto + 2 tarjetas simples sin imágenes ni menú móvil.
- **Después:** Tailwind CSS (Play CDN) + `style.css` corregido y accesible + menú responsive + Hero Banner + 4 tarjetas con imágenes uniformes + sección de arquitectura + `<aside>` enriquecido + `<footer>` de 3 columnas + `BITACORA.md` + `README.md` actualizado.
