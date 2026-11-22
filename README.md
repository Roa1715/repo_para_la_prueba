# repo_para_la_prueba
# Guía Rápida: HTML5 Semántico + Bootstrap 5 + CSS

Documentación de referencia para maquetar páginas web semánticas, aplicar diseño responsive con Bootstrap 5, personalizar estilos con CSS y sustentar la arquitectura del código.

---

## 1. Etiquetas Semánticas (HTML5)

| Etiqueta | Función | Cuándo usarla | Cómo explicarlo en la prueba |
| :--- | :--- | :--- | :--- |
| `<header>` | Encabezado | Logo, título principal (`<h1>`) y barra de navegación (`<nav>`). | *"Contiene la identidad visual y la navegación principal del sitio."* |
| `<main>` | Cuerpo principal | Contenido central y único de la página (solo debe haber uno por archivo). | *"Envuelve el contenido principal que diferencia esta página de otras."* |
| `<section>` | Bloque temático | Agrupa contenido relacionado bajo un mismo tema. Siempre lleva un título (`<h2>`). | *"Divide el `main` en capítulos o bloques temáticos."* |
| `<article>` | Pieza independiente | Contenido autónomo con sentido propio (tarjeta de producto, noticia, post). | *"Es una unidad reutilizable; si la saco de la página, se entiende sola."* |
| `<aside>` | Contenido de apoyo | Barra lateral, filtros, enlaces relacionados o información extra. | *"Acompaña al contenido principal con datos complementarios."* |
| `<footer>` | Pie de página | Derechos de autor, enlaces legales o contacto final. | *"Cierra el documento con información institucional o de contacto."* |

**Regla clave:** Un `<section>` puede contener varios `<article>` adentro (por ejemplo: una sección de *Productos* con varias tarjetas, donde cada tarjeta es un `article`).

---

## 2. Clases Clave de Bootstrap 5

### Sistema de Grillas (12 columnas)
* `container`: Centra el contenido y agrega márgenes laterales automáticos.
* `row`: Crea una fila horizontal para organizar columnas.
* `col-12`: Ocupa las 12 columnas (100% del ancho en celular).
* `col-md-6`: Ocupa 6 columnas (50% del ancho en tablet).
* `col-lg-8` / `col-lg-4`: Divide la fila en 8 columnas (principal) y 4 columnas (lateral) en escritorio.
* `g-3` / `g-4`: Espacio (*gap*) uniforme entre columnas y filas.

### Flexbox y Alineación
* `d-flex`: Activa Flexbox en el contenedor.
* `justify-content-between`: Separa los elementos hacia los extremos.
* `align-items-center`: Centra los elementos verticalmente.

### Espaciados y Componentes
* **Márgenes y rellenos:** `m` (margin), `p` (padding), `t` (arriba), `b` (abajo), `x` (lados), `y` (arriba y abajo). Ejemplo: `my-4`, `py-3`, `mb-3`.
* **Tarjetas:** `card`, `card-body`, `card-title`, `card-text`, `h-100` (misma altura).
* **Botones:** `btn btn-primary` (principal), `btn btn-outline-dark` (borde), `btn-sm` (pequeño).

---

## 3. Función del Archivo `styles.css` (CSS Personalizado)

Bootstrap resuelve la estructura y el diseño responsive rápido, mientras que `styles.css` aporta identidad visual y soluciona detalles específicos que Bootstrap no cubre por defecto:

| Selector / Propiedad | Qué hace | Para qué sirve en cualquier página | Cómo explicarlo en la prueba |
| :--- | :--- | :--- | :--- |
| `:root` (Variables CSS) | Guarda colores y sombras reutilizables en un solo lugar. | Permite cambiar la paleta de colores de todo el sitio según el tema de la prueba. | *"Usé variables en `:root` para centralizar los colores y mantener consistencia visual."* |
| `html { scroll-behavior: smooth; }` | Suaviza el desplazamiento al navegar con enlaces internos (`#`). | Evita saltos bruscos al hacer clic en los enlaces del menú. | *"Activé el desplazamiento suave para mejorar la navegación entre secciones."* |
| `.hero-banner` (`linear-gradient` + `background-size: cover`) | Combina una imagen de fondo ajustada con una capa oscura semitransparente. | Garantiza que el texto blanco de la portada siempre sea legible sin importar la foto. | *"Apliqué un degradado oscuro sobre la imagen de fondo para asegurar el contraste del texto."* |
| `.img-tarjeta` (`object-fit: cover`) | Fuerza una altura fija en las fotos recortando los bordes sin deformarlas. | Evita que las tarjetas (`article`) queden desalineadas cuando las imágenes tienen distinto tamaño. | *"Estandaricé el tamaño de las imágenes con `object-fit: cover` para que no se estiren ni descuadren las tarjetas."* |
| `.tarjeta-animada:hover` + `transition` | Eleva ligeramente la tarjeta y aumenta su sombra al pasar el cursor. | Da retroalimentación visual interactiva en catálogos, blogs o portafolios. | *"Agregué transiciones y la pseudoclase `:hover` para dar respuesta visual al pasar el cursor."* |

---

## 4. Guion Rápido de Sustentación

1. **Estructura HTML:** *"Dividí el documento con etiquetas semánticas: `header` y `footer` en los extremos, y `main` para el cuerpo. Dentro usé `section` para agrupar por temas, `article` para cada tarjeta independiente y `aside` para la información secundaria."*
2. **Diseño Responsive (Bootstrap):** *"Implementé el sistema de grillas de 12 columnas (`container`, `row`, `col-lg-8` y `col-lg-4`) para que en escritorio se vea a dos columnas y en celular se apile automáticamente."*
3. **Estilos Propios (CSS):** *"Complementé Bootstrap con `styles.css` para definir la paleta con variables en `:root`, asegurar la lectura en el banner con `linear-gradient`, uniformar las imágenes con `object-fit: cover` y añadir microinteracciones con `:hover`."*
