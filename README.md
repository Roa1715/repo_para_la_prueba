# repo_para_la_prueba
# Guía Rápida: HTML5 Semántico + Tailwind CSS + CSS Personalizado

Documentación de referencia para maquetar páginas web semánticas, aplicar diseño responsive con **Tailwind CSS**, complementar con estilos en `style.css` y sustentar la arquitectura del código.

> Para ver el paso a paso completo de cómo se construyó y migró este proyecto desde Bootstrap 5 hacia Tailwind CSS, consulta la bitácora detallada en [`BITACORA.md`](BITACORA.md).

---

## 1. Etiquetas Semánticas (HTML5)

| Etiqueta | Función | Cuándo usarla | Cómo explicarlo en la prueba |
| :--- | :--- | :--- | :--- |
| `<header>` | Encabezado | Logo, identidad del sitio y barra de navegación (`<nav>`). | *"Contiene la identidad visual y la navegación principal fija del sitio."* |
| `<main>` | Cuerpo principal | Contenido central y único de la página (solo debe haber uno por archivo). | *"Envuelve el contenido principal que diferencia esta página de otras."* |
| `<section>` | Bloque temático | Agrupa contenido relacionado bajo un mismo tema. Siempre lleva un título (`<h2>` o `<h1>` en el hero). | *"Divide el documento en bloques temáticos claros (hero, catálogo, arquitectura)."* |
| `<article>` | Pieza independiente | Contenido autónomo con sentido propio (tarjeta de catálogo, noticia, post). | *"Es una unidad reutilizable; si la saco de la página, se entiende por sí sola."* |
| `<aside>` | Contenido de apoyo | Barra lateral, categorías, resúmenes o información extra. | *"Acompaña al contenido principal con datos complementarios."* |
| `<footer>` | Pie de página | Enlaces rápidos, tecnologías, derechos de autor o contacto final. | *"Cierra el documento con información institucional y enlaces secundarios."* |

**Regla clave:** Un `<section>` puede contener varios `<article>` adentro (por ejemplo: la sección `#catalogo` contiene 4 tarjetas `<article>` independientes). Además, se mantiene un único `<h1>` en la portada y jerarquía limpia `h1` → `h2` → `h3`.

---

## 2. Clases Clave de Tailwind CSS (y su equivalencia desde Bootstrap 5)

Tailwind trabaja con un enfoque **utility-first** y **mobile-first** (los estilos base aplican a móvil y los prefijos `sm:`, `md:`, `lg:` aplican a pantallas más grandes).

### Sistema de Grillas (CSS Grid de 12 columnas)

| Tailwind CSS | Equivalente en Bootstrap 5 | Qué hace |
| :--- | :--- | :--- |
| `max-w-6xl mx-auto px-4` | `container` | Limita el ancho máximo, centra el bloque y agrega relleno lateral. |
| `grid grid-cols-1 lg:grid-cols-12 gap-8` | `row g-4` | Activa CSS Grid: 1 columna en móvil y 12 columnas en escritorio con espacio uniforme. |
| `lg:col-span-8` / `lg:col-span-4` | `col-lg-8` / `col-lg-4` | Divide el contenido en 8 columnas (principal) y 4 columnas (barra lateral `<aside>`). |
| `grid-cols-1 md:grid-cols-2 gap-6` | `row g-3` + `col-md-6` | Organiza las tarjetas en 1 columna en móvil y 2 columnas desde tablet (`md:`). |

### Flexbox, Espaciados y Tarjetas
* **Flexbox:** `flex`, `flex-col`, `items-center`, `justify-between`, `mt-auto` (empuja el botón al fondo de la tarjeta).
* **Sticky footer:** `min-h-screen flex flex-col` en `<body>` + `flex-1` en `<main>` + `mt-auto` en `<footer>`.
* **Espaciados:** `p-5` (padding), `px-4` (horizontal), `py-10` (vertical), `mb-6` (margen inferior), `space-y-6` (separación vertical automática entre hijos).
* **Tarjetas:** `bg-white border border-slate-200 rounded-xl overflow-hidden shadow-sm flex flex-col h-full`.
* **Botones:** `rounded-lg bg-brand-500 px-4 py-2 text-sm font-medium text-white hover:bg-brand-600 transition-colors`.
* **Responsive en menú:** `hidden md:flex` (visible solo desde tablet/escritorio) y `md:hidden` (botón visible solo en móvil).

---

## 3. Función del Archivo `style.css` (CSS Personalizado)

Tailwind resuelve la estructura, grilla, colores y diseño responsive rápidamente, mientras que `style.css` aporta detalles globales, accesibilidad y estilos compuestos:

| Selector / Propiedad | Qué hace | Para qué sirve | Cómo explicarlo en la prueba |
| :--- | :--- | :--- | :--- |
| `:root` (Variables CSS) | Centraliza colores y sombras reutilizables. | Facilita cambiar la identidad visual desde un solo punto. | *"Centralicé variables globales en `:root` para mantener coherencia visual."* |
| `html { scroll-behavior: smooth; }` + `scroll-margin-top` | Suaviza el desplazamiento y compensa la altura del `<header>` fijo. | Evita saltos bruscos y que la barra superior tape los títulos al usar anclas (`#`). | *"Activé scroll suave y `scroll-margin-top` para que el menú fijo no cubra los títulos."* |
| `:focus-visible` | Dibuja un contorno visible al navegar con teclado. | Mejora la accesibilidad para usuarios sin mouse. | *"Agregué `:focus-visible` para mantener navegación accesible por teclado."* |
| `.hero-banner` (`linear-gradient` + `background-size: cover`) | Superpone un degradado oscuro sobre la imagen de portada. | Garantiza legibilidad del texto blanco sobre cualquier foto. | *"Apliqué un degradado oscuro sobre el fondo para asegurar el contraste del `<h1>`."* |
| `.img-tarjeta` (`object-fit: cover`) | Fija la altura en `200px` recortando bordes sin deformar la foto. | Mantiene todas las tarjetas alineadas aunque las imágenes tengan distintos tamaños. | *"Uniformé las imágenes con `object-fit: cover` para que no se deformen ni descuadren."* |
| `.tarjeta-animada:hover` + `prefers-reduced-motion` | Eleva suavemente cada tarjeta al pasar el cursor, respetando preferencias de movimiento reducido. | Da retroalimentación visual interactiva sin afectar la accesibilidad. | *"Incluí microinteracciones con `:hover` respetando `prefers-reduced-motion`."* |

---

## 4. Estructura del Proyecto

* [`index.html`](index.html): Maquetación semántica completa con Tailwind CSS (Play CDN) y menú móvil interactivo.
* [`style.css`](style.css): Variables CSS, banner con contraste, recorte uniforme de imágenes, animaciones y accesibilidad.
* [`BITACORA.md`](BITACORA.md): Bitácora informativa paso a paso con decisiones técnicas, clases usadas y notas de sustentación.
* [`README.md`](README.md): Guía rápida de estudio y sustentación.

---

## 5. Guion Rápido de Sustentación

1. **Estructura HTML5:** *"Organicé el documento con etiquetas semánticas claras: `header` fijo con `nav`, una portada con el único `h1`, un `main` dividido en `section` temáticas, cada tarjeta como un `article` independiente, un `aside` para información complementaria y un `footer` de cierre."*
2. **Diseño Responsive (Tailwind CSS):** *"Implementé Tailwind CSS con enfoque mobile-first y CSS Grid de 12 columnas (`grid-cols-1`, `lg:grid-cols-12`, `lg:col-span-8` y `lg:col-span-4`), más un menú adaptable a móvil, para que la interfaz se reorganice según la pantalla sin escribir media queries manuales."*
3. **Estilos Propios y Accesibilidad (`style.css`):** *"Complementé Tailwind con `style.css` para definir variables en `:root`, compensar el encabezado fijo con `scroll-margin-top`, asegurar el contraste del hero con `linear-gradient`, estandarizar imágenes con `object-fit: cover` y respetar accesibilidad con `:focus-visible` y `prefers-reduced-motion`."*
