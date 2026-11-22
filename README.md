# repo_para_la_prueba
# Guía Rápida: HTML5 Semántico + Bootstrap 5

Apuntes de referencia rápida para maquetar con etiquetas semánticas, aplicar diseño responsive con Bootstrap 5 y sustentar la estructura del código.

---

## 1. Etiquetas Semánticas (HTML5)

| Etiqueta | Función | Cuándo usarla | Cómo explicarlo en la prueba |
| :--- | :--- | :--- | :--- |
| `<header>` | Encabezado | Logo, título principal (`<h1>`) y menú (`<nav>`). | *"Contiene la identidad visual y la navegación principal."* |
| `<main>` | Cuerpo principal | Contenido central y único de la página (solo uno por HTML). | *"Envuelve el contenido principal que diferencia esta página."* |
| `<section>` | Bloque temático | Agrupa contenido sobre un mismo tema. Lleva un título (`<h2>`). | *"Divide el `main` en secciones o bloques temáticos."* |
| `<article>` | Pieza independiente | Contenido autónomo (tarjeta de producto, noticia, post). | *"Es una unidad reutilizable; se entiende por sí sola."* |
| `<aside>` | Contenido de apoyo | Barra lateral, filtros, enlaces extra o publicidad. | *"Acompaña al contenido principal con información secundaria."* |
| `<footer>` | Pie de página | Derechos de autor, contacto o enlaces finales. | *"Cierra el documento con datos institucionales o de contacto."* |

**Regla clave:** Un `<section>` puede tener varios `<article>` adentro (por ejemplo: una sección de *Productos* con varias tarjetas, donde cada tarjeta es un `article`).

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

## 3. Guion para Explicar el Diseño (3 pasos)

1. **Estructura:** *"Dividí el documento con etiquetas semánticas: `header` y `footer` en los extremos, y `main` para el cuerpo."*
2. **Distribución:** *"Dentro de `main` usé una fila (`row`) de Bootstrap dividida en `col-lg-8` para el contenido y `col-lg-4` para el `aside`, logrando diseño responsive automático."*
3. **Semántica interna:** *"Agrupé el contenido por temas con `section`, y cada tarjeta individual la puse en un `article` porque es contenido independiente."*
