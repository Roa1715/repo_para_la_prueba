# repo_para_la_prueba
# Guía Completa: HTML5 Semántico + 100% Tailwind CSS (Sin archivos CSS)

Documentación completa de referencia para entender, usar y sustentar cada etiqueta HTML5 y cada clase utilitaria de **Tailwind CSS** aplicada en [`index.html`](index.html), logrando una página responsive, moderna y accesible **sin escribir ningún archivo `.css` externo ni etiquetas `<style>`**.

> También puedes revisar el historial evolutivo del proyecto en [`BITACORA.md`](BITACORA.md).

---

## 1. Estructura del Proyecto

| Archivo | Propósito |
| :--- | :--- |
| [`index.html`](index.html) | Página completa maquetada con HTML5 semántico y 100% utilidades de Tailwind CSS (vía Play CDN) + 12 líneas de JS para el menú móvil. |
| [`README.md`](README.md) | Esta guía completa con la explicación de uso de cada etiqueta y cada clase de Tailwind del proyecto. |
| [`BITACORA.md`](BITACORA.md) | Registro informativo paso a paso de cómo evolucionó el proyecto desde Bootstrap 5 hasta 100% Tailwind CSS sin CSS externo. |

---

## 2. Cómo Funciona Tailwind CSS sin Archivo CSS

En `<head>` de [`index.html`](index.html) cargamos el **Play CDN de Tailwind** y definimos nuestra paleta de colores `brand` directamente en `tailwind.config`:

```html
<script src="https://cdn.tailwindcss.com"></script>
<script>
  tailwind.config = {
    theme: {
      extend: {
        colors: {
          brand: {
            50: '#eff6ff',
            100: '#dbeafe',
            500: '#2563eb',
            600: '#1d4ed8',
            700: '#1e40af',
            900: '#0f172a',
          },
        },
      },
    },
  };
</script>
```

**¿Por qué `theme.extend.colors.brand`?**
- Reemplaza a las variables `:root { --color-principal: ... }` de un archivo CSS tradicional.
- Permite usar `bg-brand-500`, `text-brand-700`, `border-brand-100`, `hover:bg-brand-600`, etc., manteniendo todos los colores nativos de Tailwind (`slate`, `emerald`, `amber`, `violet`).

---

## 3. Explicación de Cada Etiqueta HTML5 Semántica Usada

| Etiqueta | Función | Dónde se usa en `index.html` | Cómo explicarlo en la prueba |
| :--- | :--- | :--- | :--- |
| `<html lang="es">` | Raíz del documento | Envuelve todo el HTML e indica idioma español y `scroll-smooth`. | *"Define el idioma para lectores de pantalla y activa el desplazamiento suave global."* |
| `<header>` | Encabezado principal | Barra superior fija (`sticky`) con logo y menús. | *"Contiene la identidad del sitio y la navegación principal."* |
| `<nav>` | Bloque de navegación | Menú escritorio y menú móvil (`aria-label` distinto en cada uno). | *"Agrupa los enlaces de navegación interna del sitio."* |
| `<main>` | Cuerpo principal único | Envuelve las secciones centrales y la barra lateral (solo hay uno por página). | *"Delimita el contenido principal y único de esta vista."* |
| `<section>` | Bloque temático | Hero (`#inicio`), Catálogo (`#catalogo`) y Arquitectura (`#arquitectura`). | *"Divide el documento en bloques temáticos; cada uno tiene su propio encabezado."* |
| `<article>` | Unidad autónoma | Cada una de las 4 tarjetas del catálogo. | *"Representa una pieza independiente y reutilizable que se entiende por sí sola."* |
| `<aside>` | Contenido complementario | Barra lateral derecha con resumen técnico, categorías y tip. | *"Aporta información de apoyo que complementa el contenido principal sin ser el foco."* |
| `<footer>` | Pie de página | Bloque final (`#contacto`) con descripción, enlaces y tecnologías. | *"Cierra el documento con información institucional y navegación secundaria."* |
| `<h1>`, `<h2>`, `<h3>` | Jerarquía de títulos | Un único `<h1>` en el Hero, `<h2>` por sección/bloque y `<h3>` por tarjeta. | *"Respeto una jerarquía ordenada sin saltar niveles para accesibilidad y SEO."* |
| `<button type="button">` | Acción interactiva | Botón hamburguesa `#menu-btn` en móvil. | *"Uso `<button>` para acciones en pantalla y `<a>` solo para navegar."* |
| `<img>` + `alt` + `loading="lazy"` | Imágenes accesibles | Fondo decorativo (`alt=""` + `aria-hidden="true"`) y fotos de tarjetas con `alt` descriptivo. | *"Diferencio imágenes decorativas de informativas y aplico carga diferida (`lazy`)."* |
| `<ul>` / `<li>` | Listas estructuradas | Enlaces del menú móvil, lista técnica del `<aside>`, categorías y footer. | *"Uso listas reales para conjuntos de ítems o enlaces relacionados."* |

---

## 4. Explicación Completa de Uso de Cada Clase de Tailwind CSS

### A. Layout, Contenedor y Scroll
| Clase | Propiedad CSS equivalente | Para qué sirve en `index.html` |
| :--- | :--- | :--- |
| `scroll-smooth` | `scroll-behavior: smooth;` | Suaviza el desplazamiento al hacer clic en enlaces ancla (`#catalogo`, `#arquitectura`, `#contacto`). |
| `scroll-mt-20` | `scroll-margin-top: 5rem;` | Deja espacio superior al saltar a un `#id` para que el `<header>` fijo no tape el título. |
| `min-h-screen` | `min-height: 100vh;` | Hace que `<body>` mida al menos el 100% del alto de la pantalla. |
| `max-w-6xl` | `max-width: 72rem;` (1152px) | Limita el ancho máximo del contenido en pantallas grandes para facilitar la lectura. |
| `mx-auto` | `margin-left: auto; margin-right: auto;` | Centra horizontalmente el contenedor (`max-w-6xl mx-auto` reemplaza a `.container` de Bootstrap). |
| `w-full` / `w-fit` | `width: 100%;` / `width: fit-content;` | `w-full` ocupa todo el ancho disponible; `w-fit` ajusta una etiqueta/badge al tamaño exacto de su texto. |
| `h-full` / `h-8 w-8` / `h-6 w-6` | `height` / `width` | `h-full` iguala la altura de las tarjetas en una fila; `h-8 w-8` y `h-6 w-6` dimensionan el ícono del logo y del botón móvil. |
| `min-h-[340px]` | `min-height: 340px;` | Asegura una altura mínima visual atractiva para la portada Hero. |
| `flex-1` | `flex: 1 1 0%;` | Permite que `<main>` o el cuerpo de una tarjeta crezcan para ocupar el espacio sobrante. |
| `mt-auto` | `margin-top: auto;` | Empuja el `<footer>` al fondo de la pantalla y los botones al fondo de cada tarjeta `<article>`. |

---

### B. Sistema de Grillas (CSS Grid — Responsive Mobile-First)
| Clase | Propiedad CSS equivalente | Para qué sirve en `index.html` |
| :--- | :--- | :--- |
| `grid` | `display: grid;` | Activa CSS Grid en el contenedor. |
| `grid-cols-1` | `grid-template-columns: repeat(1, minmax(0, 1fr));` | En celular (base mobile-first), todo se muestra en 1 sola columna apilada. |
| `sm:grid-cols-2` | 2 columnas desde `640px` | Divide los 4 bloques de la sección `#arquitectura` en 2 columnas desde pantallas pequeñas. |
| `md:grid-cols-2` | 2 columnas desde `768px` | Muestra las tarjetas del `#catalogo` en 2 columnas desde tablet. |
| `md:grid-cols-3` | 3 columnas desde `768px` | Organiza el `<footer>` en 3 columnas (descripción, navegación y tecnologías). |
| `lg:grid-cols-12` | 12 columnas desde `1024px` | Crea la grilla principal de 12 columnas en escritorio. |
| `lg:col-span-8` | `grid-column: span 8 / span 8;` | Asigna 8 de las 12 columnas al contenido principal (catálogo + arquitectura). |
| `lg:col-span-4` | `grid-column: span 4 / span 4;` | Asigna las 4 columnas restantes a la barra lateral `<aside>`. |
| `gap-4` / `gap-6` / `gap-8` | `gap: 1rem` / `1.5rem` / `2rem` | Separación uniforme entre filas y columnas de la grilla o elementos flex. |
| `items-start` | `align-items: flex-start;` | Evita que el `<aside>` se estire verticalmente a la altura total de la columna izquierda. |

---

### C. Flexbox y Alineación
| Clase | Propiedad CSS equivalente | Para qué sirve en `index.html` |
| :--- | :--- | :--- |
| `flex` / `inline-flex` | `display: flex` / `inline-flex` | Activa Flexbox en bloque o en línea (muy usado en botones, badges y barra superior). |
| `flex-col` | `flex-direction: column;` | Apila elementos verticalmente (en `<body>`, Hero, menú móvil y dentro de cada `<article>`). |
| `flex-wrap` | `flex-wrap: wrap;` | Permite que botones o badges bajen a la siguiente línea si no caben en pantallas estrechas. |
| `items-center` | `align-items: center;` | Centra los elementos en el eje transversal (por ejemplo, logo y enlaces del `<header>`). |
| `justify-between` | `justify-content: space-between;` | Separa los elementos hacia los extremos izquierdo y derecho (logo a la izquierda, menú a la derecha). |
| `justify-center` | `justify-content: center;` | Centra el contenido en el eje principal (texto dentro de botones e ícono `TW`). |
| `block` | `display: block;` | Hace que cada enlace del menú móvil sea clickeable en todo su ancho. |

---

### D. Posicionamiento, Capas y Portada Hero (Sin CSS)
| Clase | Propiedad CSS equivalente | Para qué sirve en `index.html` |
| :--- | :--- | :--- |
| `sticky top-0` | `position: sticky; top: 0;` | Mantiene el `<header>` fijo arriba mientras el usuario hace scroll. |
| `z-40` / `z-10` | `z-index: 40;` / `10;` | Controla qué capa queda encima (`z-40` en header sobre toda la página; `z-10` en el texto del Hero sobre la foto). |
| `backdrop-blur` | `backdrop-filter: blur(8px);` | Aplica efecto vidrio esmerilado suave en el `<header>` semitransparente (`bg-brand-900/95`). |
| `relative` | `position: relative;` | Convierte al Hero en referencia para posicionar la foto y el degradado absoluto dentro de él. |
| `absolute inset-0` | `position: absolute; inset: 0;` | Extiende la imagen de fondo y la capa oscura para cubrir exactamente el 100% del Hero. |
| `overflow-hidden` | `overflow: hidden;` | Recorta esquinas de imágenes dentro de tarjetas (`rounded-xl`) y evita desbordes del Hero. |

---

### E. Imágenes y Recorte Uniforme
| Clase | Propiedad CSS equivalente | Para qué sirve en `index.html` |
| :--- | :--- | :--- |
| `h-52` | `height: 13rem;` (208px) | Fija una altura idéntica en todas las imágenes de tarjetas (`<article>`). |
| `w-full` | `width: 100%;` | Ajusta la imagen al ancho completo de la tarjeta. |
| `object-cover` | `object-fit: cover;` | Recorta proporcionalmente la imagen para llenar el marco sin estirarla ni deformarla. |

---

### F. Espaciados (Padding, Margin y Space)
| Clase | Propiedad CSS equivalente | Para qué sirve en `index.html` |
| :--- | :--- | :--- |
| `p-2` / `p-4` / `p-5` / `p-6` | `padding: 0.5rem` a `1.5rem` | Relleno interno uniforme en botones, bloques de arquitectura, tarjetas y paneles del `<aside>`. |
| `px-*` / `py-*` | `padding-inline` / `padding-block` | Relleno horizontal (`px-4`, `px-5`) y vertical (`py-2`, `py-3.5`, `py-10`, `py-16`). |
| `mt-*` / `mb-*` | `margin-top` / `margin-bottom` | Separación vertical controlada entre títulos, párrafos y grupos de botones (`mt-4`, `mt-8`, `mb-2`, `mb-6`). |
| `pb-3` | `padding-bottom: 0.75rem;` | Espacio inferior antes de la línea divisoria del título de `#catalogo`. |
| `space-y-1.5` / `space-y-2` / `space-y-6` / `space-y-12` | `margin-top` automático entre hijos | Separa verticalmente los bloques hermanos sin tener que añadir márgenes a cada elemento individual. |

---

### G. Colores, Fondos, Degradados y Bordes
| Clase | Qué hace | Dónde se usa |
| :--- | :--- | :--- |
| `bg-slate-50`, `bg-white`, `bg-slate-100`, `bg-slate-800` | Fondos neutros (claro general, tarjetas blancas, códigos y pills oscuros). | `<body>`, tarjetas, `<code>` y tags del footer. |
| `bg-brand-900`, `bg-brand-500`, `bg-brand-50` | Paleta principal azul oscuro, azul acción y azul suave definida en `tailwind.config`. | Header, footer, botones CTA y tarjeta de tip. |
| `bg-brand-900/95`, `bg-white/10`, `bg-brand-500/20` | Fondos con opacidad (`/95`, `/10`, `/20`). | Header translúcido, botón secundario y badge del Hero. |
| `bg-gradient-to-b from-slate-900/75 via-slate-900/80 to-slate-900/90` | Degradado vertical oscuro semitransparente. | Capa sobre la imagen del Hero para asegurar legibilidad del texto blanco. |
| `bg-emerald-50 text-emerald-700`, `bg-amber-50 text-amber-700`, `bg-violet-50 text-violet-700` | Colores semánticos suaves para diferenciar categorías. | Badges de cada tarjeta `<article>` y contadores del `<aside>`. |
| `text-slate-900`, `text-slate-800`, `text-slate-600`, `text-slate-500`, `text-slate-400`, `text-white` | Escala de contraste tipográfico (títulos oscuros, cuerpo legible y textos secundarios suaves). | En toda la página. |
| `border`, `border-b`, `border-t`, `border-slate-200`, `border-slate-800`, `border-brand-100`, `border-white/30` | Bordes finos de `1px` y separadores de sección. | Tarjetas, encabezado, título del catálogo, botón secundario y footer. |
| `divide-y divide-slate-100` | Agrega líneas divisorias solo entre ítems internos de una lista. | Lista de resumen técnico dentro del `<aside>`. |
| `ring-1 ring-inset ring-brand-100` | Borde interior sutil tipo anillo. | Badge `"4 artículos"` del catálogo. |
| `rounded`, `rounded-md`, `rounded-lg`, `rounded-xl`, `rounded-full` | Radios de borde (`4px`, `6px`, `8px`, `12px` y pastilla circular). | Códigos, badges, botones, tarjetas y pills. |

---

### H. Tipografía
| Clase | Qué hace | Dónde se usa |
| :--- | :--- | :--- |
| `text-xs`, `text-sm`, `text-base`, `text-lg`, `text-xl`, `text-3xl`, `sm:text-4xl`, `md:text-5xl` | Escala de tamaños de fuente (con crecimiento responsive en el `<h1>`). | Todos los textos y títulos. |
| `font-medium`, `font-semibold`, `font-bold`, `font-extrabold` | Pesos tipográficos (`500`, `600`, `700`, `800`). | Enlaces, badges, subtítulos y título principal. |
| `font-mono` | Fuente monoespaciada. | Etiquetas HTML y nombres de clases dentro de `<code>` y títulos de `#arquitectura`. |
| `uppercase` + `tracking-wider` | Texto en mayúsculas con mayor espaciado entre letras. | Encabezados pequeños de secciones del `<aside>`, badge del Hero y columnas del footer. |
| `tracking-tight` | Letras ligeramente más juntas para titulares grandes. | Logo y `<h1>` del Hero. |
| `leading-tight` / `leading-relaxed` | Interlineado compacto (títulos) o cómodo (párrafos). | `<h1>` y párrafos descriptivos. |
| `text-center` | Centra el texto horizontalmente. | Barra inferior del `<footer>`. |
| `antialiased` | Suaviza el renderizado de fuentes en pantalla. | `<body>`. |

---

### I. Sombras, Microinteracciones, Responsive y Accesibilidad
| Clase | Qué hace | Para qué sirve en `index.html` |
| :--- | :--- | :--- |
| `shadow-sm` / `hover:shadow-lg` | Sombra suave en reposo que crece al pasar el cursor. | Da profundidad a tarjetas y retroalimentación visual en `:hover`. |
| `transition` / `transition-colors` / `duration-200` / `ease-out` | Suaviza cambios de color, sombra y posición en `200ms`. | Botones, enlaces y tarjetas animadas. |
| `hover:-translate-y-1` | Eleva `4px` la tarjeta al pasar el cursor. | Reemplaza `.tarjeta-animada:hover { transform: translateY(-4px); }` sin archivo CSS. |
| `hover:bg-*` / `hover:text-*` | Cambia color de fondo o texto al pasar el cursor. | Enlaces de navegación, botones y lista de categorías. |
| `hidden md:flex` | Oculta el menú horizontal en móvil y lo muestra desde `768px`. | Navegación responsive en `<header>`. |
| `md:hidden` | Muestra el botón hamburguesa y el menú móvil solo debajo de `768px`. | Navegación móvil en `<header>`. |
| `focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-brand-500 focus-visible:ring-offset-2` | Dibuja un anillo de foco accesible solo cuando se navega con teclado (`Tab`). | Accesibilidad en todos los enlaces y botones sin CSS externo. |
| `motion-reduce:transition-none motion-reduce:hover:translate-y-0` | Desactiva animaciones si el usuario configuró "reducir movimiento" en su sistema. | Reemplaza `@media (prefers-reduced-motion: reduce)` usando solo Tailwind. |

---

## 5. Comparativa: Cómo se Eliminó `style.css`

| Regla que antes estaba en `style.css` | Reemplazo 100% Tailwind en `index.html` |
| :--- | :--- |
| `:root { --color-principal: ... }` | `tailwind.config` → `theme.extend.colors.brand` |
| `html { scroll-behavior: smooth; }` | `<html lang="es" class="scroll-smooth">` |
| `section[id] { scroll-margin-top: 5rem; }` | `scroll-mt-20` en cada `<section>` y `<footer>` |
| `:focus-visible { outline: 2px solid ... }` | `focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-brand-500` |
| `.hero-banner` (`linear-gradient` + `background-size: cover`) | `relative overflow-hidden` + `<img>` con `absolute inset-0 h-full w-full object-cover` + capa `bg-gradient-to-b from-slate-900/75 via-slate-900/80 to-slate-900/90` |
| `.img-tarjeta { height: 200px; width: 100%; object-fit: cover; }` | `h-52 w-full object-cover` en cada `<img>` |
| `.tarjeta-animada:hover { transform: translateY(-4px); box-shadow: ... }` | `transition duration-200 ease-out hover:-translate-y-1 hover:shadow-lg` |
| `@media (prefers-reduced-motion: reduce)` | `motion-reduce:transition-none motion-reduce:hover:translate-y-0` |

---

## 6. Script Mínimo del Menú Móvil

Al final de [`index.html`](index.html) hay 12 líneas de JavaScript que:
1. Escuchan el clic en `#menu-btn` y alternan la clase `hidden` de Tailwind en `#menu-movil`.
2. Actualizan `aria-expanded` (`true` / `false`) para accesibilidad con lectores de pantalla.
3. Cierran automáticamente el menú al hacer clic en cualquiera de sus enlaces internos.

---

## 7. Guion Rápido de Sustentación

1. **HTML5 Semántico:** *"Estructuré toda la página con etiquetas semánticas claras: `header` fijo con `nav`, una portada con el único `h1`, un `main` dividido en `section` temáticas, 4 tarjetas `article` independientes, un `aside` complementario y un `footer` de cierre."*
2. **100% Tailwind CSS sin archivo `.css`:** *"Eliminé por completo la hoja de estilos externa porque Tailwind cubre todo de forma nativa: paleta personalizada en `tailwind.config`, grilla responsive de 12 columnas (`lg:grid-cols-12`, `lg:col-span-8`, `lg:col-span-4`), `scroll-smooth`, `scroll-mt-20`, recorte uniforme con `object-cover` y elevación con `hover:-translate-y-1`."*
3. **Responsive y Accesibilidad:** *"Apliqué enfoque mobile-first (`grid-cols-1` → `md:grid-cols-2` → `lg:grid-cols-12`), menú adaptable con `hidden md:flex` y `md:hidden`, foco visible para teclado con `focus-visible:ring-2` y respeto a movimiento reducido con `motion-reduce:`."*
