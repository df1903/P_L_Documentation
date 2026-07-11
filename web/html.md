# Guía Rápida de HTML

Documento de referencia para entender **qué es HTML**, **para qué sirve** y **cómo se estructura** un documento HTML moderno. El enfoque es práctico: partes claras, explicación breve y código base listo para usar.

## Tabla de contenidos

- [¿Qué es HTML?](#qué-es-html)
- [Estructura básica de un documento HTML](#estructura-básica-de-un-documento-html)
- [Partes del documento HTML](#partes-del-documento-html)
- [Comentarios en HTML](#comentarios-en-html)
- [Reglas básicas de HTML](#reglas-básicas-de-html)
- [Flujo básico del navegador](#flujo-básico-del-navegador)
- [Relación con CSS y JavaScript](#relación-con-css-y-javascript)
- [Atributos globales](#atributos-globales)
- [Elementos obsoletos (evitar)](#elementos-obsoletos-evitar)
- [Títulos (Headings)](#títulos-headings)
- [Etiquetas de texto (Text Content)](#etiquetas-de-texto-text-content)
- [Listas](#listas)
  - [Listas no ordenadas (`<ul>`)](#listas-no-ordenadas-ul)
  - [Listas ordenadas (`<ol>`)](#listas-ordenadas-ol)
  - [Listas de definición (`<dl>`)](#listas-de-definición-dl)
- [Enlaces (`<a>`)](#enlaces-a)
  - [Atributos importantes de `<a>`](#atributos-importantes-de-a)
  - [Buenas prácticas de enlaces](#buenas-prácticas-de-enlaces)
- [Etiquetas semánticas (estructura de página)](#etiquetas-semánticas-estructura-de-página)
  - [Jerarquía recomendada (layout típico)](#jerarquía-recomendada-layout-típico)
  - [Estructura completa recomendada](#estructura-completa-recomendada)
  - [¿Cuándo usar cada etiqueta?](#cuándo-usar-cada-etiqueta)
- [`<div>` (contenedor genérico)](#div-contenedor-genérico)
  - [Uso básico](#uso-básico)
  - [`<div>` como contenedor de layout](#div-como-contenedor-de-layout)
  - [`<div>` vs etiquetas semánticas](#div-vs-etiquetas-semánticas)
  - [`<div>` con clases e IDs](#div-con-clases-e-ids)
  - [`<div>` como agrupador visual](#div-como-agrupador-visual)
  - [`<div>` y accesibilidad](#div-y-accesibilidad)
  - [Cuándo usar `<div>`](#cuándo-usar-div)
  - [Ejemplo recomendado (uso correcto)](#ejemplo-recomendado-uso-correcto)
  - [Resumen rápido](#resumen-rápido)
- [Buenas prácticas de HTML semántico](#buenas-prácticas-de-html-semántico)
- [Formularios (Forms)](#formularios-forms)
  - [`<form>` (contenedor del formulario)](#form-contenedor-del-formulario)
  - [`<label>` (etiqueta asociada al campo)](#label-etiqueta-asociada-al-campo)
  - [`<input>` (tipos y atributos)](#input-tipos-y-atributos)
  - [Tipos de `<input>` más usados](#tipos-de-input-más-usados)
  - [`<textarea>` (texto largo)](#textarea-texto-largo)
  - [`<select>` + `<option>` (lista desplegable)](#select-option-lista-desplegable)
  - [`<datalist>` (sugerencias de autocompletado)](#datalist-sugerencias-de-autocompletado)
  - [`<progress>` (progreso de una tarea)](#progress-progreso-de-una-tarea)
  - [`<meter>` (valor dentro de un rango conocido)](#meter-valor-dentro-de-un-rango-conocido)
  - [`<output>` (resultado de un cálculo)](#output-resultado-de-un-cálculo)
  - [Botones (`button` e inputs tipo botón)](#botones-button-e-inputs-tipo-botón)
  - [`fieldset` y `legend` (agrupar campos)](#fieldset-y-legend-agrupar-campos)
  - [Validaciones HTML (inputs)](#validaciones-html-inputs)
  - [Ejemplo completo (formulario recomendado)](#ejemplo-completo-formulario-recomendado)
- [Contenido multimedia: imágenes](#contenido-multimedia-imágenes)
  - [`<img>`](#img)
  - [Tamaño explícito (layout estable)](#tamaño-explícito-layout-estable)
  - [Accesibilidad (`alt`)](#accesibilidad-alt)
  - [`<figure>` y `<figcaption>`](#figure-y-figcaption)
  - [Imagen como enlace](#imagen-como-enlace)
  - [Imágenes responsive (`srcset` + `sizes`)](#imágenes-responsive-srcset-sizes)
  - [Condiciones de tamaño (`sizes`)](#condiciones-de-tamaño-sizes)
  - [`<picture>` con condiciones (breakpoints reales)](#picture-con-condiciones-breakpoints-reales)
  - [`<picture>` combinando formatos + condiciones](#picture-combinando-formatos-condiciones)
  - [Carga diferida (lazy loading)](#carga-diferida-lazy-loading)
  - [Decodificación de imágenes (`decoding`)](#decodificación-de-imágenes-decoding)
  - [Imágenes decorativas](#imágenes-decorativas)
  - [SVG como imagen](#svg-como-imagen)
  - [Rutas de imágenes](#rutas-de-imágenes)
  - [Formatos de imagen recomendados](#formatos-de-imagen-recomendados)
  - [Errores comunes](#errores-comunes)
- [Video (`<video>`)](#video-video)
  - [Estructura base](#estructura-base)
  - [Video con tamaño (`width` / `height`)](#video-con-tamaño-width-height)
  - [Video con múltiples fuentes (`<source>`)](#video-con-múltiples-fuentes-source)
  - [Atributo `type` en `<source>`](#atributo-type-en-source)
  - [`poster` (imagen previa)](#poster-imagen-previa)
  - [`preload` (carga anticipada)](#preload-carga-anticipada)
  - [`autoplay`, `muted`, `loop`](#autoplay-muted-loop)
  - [`controlslist` (opcional, soporte parcial)](#controlslist-opcional-soporte-parcial)
  - [`disablepictureinpicture` (opcional)](#disablepictureinpicture-opcional)
  - [Texto fallback dentro de `<video>`](#texto-fallback-dentro-de-video)
  - [Ejemplo recomendado (completo)](#ejemplo-recomendado-completo)
- [Audio (`<audio>`)](#audio-audio)
  - [Estructura base](#estructura-base-1)
  - [Audio con múltiples fuentes (`<source>`)](#audio-con-múltiples-fuentes-source)
  - [Atributo `type` en `<source>`](#atributo-type-en-source-1)
  - [`preload` (carga anticipada)](#preload-carga-anticipada-1)
  - [`autoplay`, `muted`, `loop`](#autoplay-muted-loop-1)
  - [`controlslist` (soporte parcial)](#controlslist-soporte-parcial)
  - [Texto fallback dentro de `<audio>`](#texto-fallback-dentro-de-audio)
  - [Ejemplo completo recomendado](#ejemplo-completo-recomendado)
- [Buenas prácticas de audio y video](#buenas-prácticas-de-audio-y-video)
- [`<iframe>` (documento anidado)](#iframe-documento-anidado)
- [`<embed>` y `<object>` (contenido externo/plugins)](#embed-y-object-contenido-externo-plugins)
- [Tablas](#tablas)
  - [Estructura básica de una tabla](#estructura-básica-de-una-tabla)
  - [`<table>`](#table)
  - [`<caption>` (título de la tabla)](#caption-título-de-la-tabla)
  - [`<thead>`](#thead)
  - [`<tr>` (fila)](#tr-fila)
  - [`<th>` (celda de encabezado)](#th-celda-de-encabezado)
  - [`<tbody>`](#tbody)
  - [`<td>` (celda de datos)](#td-celda-de-datos)
  - [`<tfoot>`](#tfoot)
  - [`colspan` (combinar columnas)](#colspan-combinar-columnas)
  - [`rowspan` (combinar filas)](#rowspan-combinar-filas)
  - [Tabla con encabezados de fila y columna](#tabla-con-encabezados-de-fila-y-columna)
  - [Accesibilidad en tablas](#accesibilidad-en-tablas)
  - [Ejemplo completo recomendado](#ejemplo-completo-recomendado-1)
- [`<details>` y `<summary>` (contenido plegable)](#details-y-summary-contenido-plegable)
- [`<dialog>` (cuadro de diálogo nativo)](#dialog-cuadro-de-diálogo-nativo)
- [Accesibilidad (A11y) y ARIA](#accesibilidad-a11y-y-aria)
  - [¿Qué es ARIA?](#qué-es-aria)
  - [Atributos ARIA más usados](#atributos-aria-más-usados)
  - [`role`](#role)
  - [Ejemplos comunes de ARIA bien aplicado](#ejemplos-comunes-de-aria-bien-aplicado)
  - [Buenas prácticas de accesibilidad (general)](#buenas-prácticas-de-accesibilidad-general)
  - [Errores comunes](#errores-comunes-1)
  - [Resumen rápido](#resumen-rápido-1)
- [`<script>` (JavaScript en HTML)](#script-javascript-en-html)
- [`<noscript>` (contenido alternativo sin JavaScript)](#noscript-contenido-alternativo-sin-javascript)
- [`<template>` (marcado reutilizable no renderizado)](#template-marcado-reutilizable-no-renderizado)
- [`<canvas>` (gráficos vía JavaScript)](#canvas-gráficos-vía-javascript)
- [SEO y metadatos del documento HTML](#seo-y-metadatos-del-documento-html)
  - [Idioma del documento (`lang`)](#idioma-del-documento-lang)
  - [Codificación de caracteres (`UTF-8`)](#codificación-de-caracteres-utf-8)
  - [Viewport (responsive)](#viewport-responsive)
  - [`<title>` (título del documento)](#title-título-del-documento)
  - [Meta description](#meta-description)
  - [Otras meta etiquetas comunes](#otras-meta-etiquetas-comunes)
  - [Open Graph (redes sociales)](#open-graph-redes-sociales)
  - [Favicon](#favicon)
  - [`<base>` (URL base del documento)](#base-url-base-del-documento)
  - [`<body>` (contenido visible)](#body-contenido-visible)
  - [Estructura SEO recomendada (completa)](#estructura-seo-recomendada-completa)
  - [Buenas prácticas SEO](#buenas-prácticas-seo)

---

## ¿Qué es HTML?

HTML (**HyperText Markup Language**) es el lenguaje de marcado que define la **estructura y el contenido** de una página web.  
No es un lenguaje de programación: describe **qué es cada cosa** (títulos, párrafos, enlaces, imágenes), no cómo se comporta.

El navegador interpreta el HTML y, junto con CSS y JavaScript, construye la página visible.

---

## Estructura básica de un documento HTML

Todo documento HTML sigue una estructura mínima obligatoria.  
Esta estructura permite al navegador interpretar correctamente el contenido.

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Documento HTML Base</title>
  </head>
  <body>
    <h1>Hola mundo</h1>
    <p>Este es mi primer documento HTML.</p>
  </body>
</html>
```

---

## Partes del documento HTML

### `<!DOCTYPE html>`

```html
<!DOCTYPE html>
```

- Indica que el documento usa **HTML5**.
- No es una etiqueta HTML, es una instrucción para el navegador.
- Evita el _quirks mode_ (modo de compatibilidad antiguo).

---

### `<html>`

```html
<html lang="es"></html>
```

- Elemento raíz del documento.
- Encapsula **todo** el contenido HTML.
- El atributo `lang` indica el idioma del contenido (accesibilidad y SEO).

---

### `<head>`

```html
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Documento HTML Base</title>
</head>
```

- Contiene **metadatos**.
- No se renderiza visualmente.
- Define información para el navegador, buscadores y dispositivos.

---

### `<meta charset="UTF-8">`

```html
<meta charset="UTF-8" />
```

- Define la codificación de caracteres.
- Permite usar tildes, ñ y símbolos correctamente.

---

### `<meta name="viewport">`

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

- Controla cómo se adapta la página a dispositivos móviles.
- Esencial para diseño **responsive**.

---

### `<title>`

```html
<title>Documento HTML Base</title>
```

- Define el título de la pestaña del navegador.
- Usado por motores de búsqueda y marcadores.

---

### `<body>`

```html
<body>
  <h1>Hola mundo</h1>
  <p>Este es mi primer documento HTML.</p>
</body>
```

- Contiene **todo el contenido visible** de la página.
- Aquí van textos, imágenes, enlaces, formularios, etc.

---

## Comentarios en HTML

```html
<!-- Este es un comentario en HTML -->
```

- No se muestran en la página.
- Útiles para documentar estructura o secciones.

---

## Reglas básicas de HTML

- La mayoría de elementos abren y cierran: `<p>...</p>`.
- Los **elementos vacíos** (_void elements_) no llevan etiqueta de cierre: `<img>`, `<br>`, `<meta>`, `<input>`, `<link>`, `<source>`, etc.
- En HTML5 el `/` de autocierre es opcional: `<img />` funciona, pero normalmente se escribe `<img>`.
- HTML no distingue mayúsculas/minúsculas en nombres de etiquetas/atributos, pero se recomienda usar **minúsculas**.
- Usa comillas (idealmente dobles) en valores de atributos: `href="..."`.
- La indentación consistente mejora la legibilidad (2 o 4 espacios).

---

## Flujo básico del navegador

1. El navegador solicita el HTML al servidor.
2. Lee el documento de arriba hacia abajo.
3. Construye el DOM.
4. Aplica CSS.
5. Ejecuta JavaScript.
6. Renderiza la página.

---

## Relación con CSS y JavaScript

- **HTML**: estructura y semántica.
- **CSS**: estilos (presentación).
- **JavaScript**: comportamiento e interactividad.

Ejemplo común (recomendado) para cargar CSS y JS sin bloquear el parseo del HTML:

```html
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <link rel="stylesheet" href="/styles.css" />
  <script defer src="/app.js"></script>
</head>
```

- `defer` descarga el script en paralelo y lo ejecuta cuando el HTML ya fue parseado.
- Alternativa: colocar `<script src="..."></script>` al final del `<body>`.

---

## Atributos globales

Se aplican a (casi) cualquier elemento HTML, sin importar su etiqueta.

- **`id`**: identificador único en todo el documento.

```html
<div id="main-content">Contenido</div>
```

- **`class`**: lista de clases separadas por espacio, para CSS/JS.

```html
<div class="tarjeta destacada">Contenido</div>
```

- **`style`**: CSS inline (usar con moderación; preferir hojas de estilo).

```html
<p style="color: blue;">Texto azul</p>
```

- **`title`**: texto de ayuda (tooltip) al pasar el cursor.

```html
<abbr title="Cascading Style Sheets">CSS</abbr>
```

- **`hidden`**: oculta el elemento del renderizado.

```html
<div hidden>No se muestra</div>
```

- **`tabindex`**: incluye el elemento en la navegación por teclado y define su orden.

```html
<div tabindex="0">Enfocable con Tab (orden natural)</div>
<div tabindex="-1">Enfocable solo por JavaScript, no con Tab</div>
```

- **`contenteditable`**: hace el contenido editable directamente por el usuario.

```html
<div contenteditable="true">Este texto se puede editar</div>
```

- **`draggable`**: habilita arrastrar el elemento (Drag and Drop API).

```html
<img src="logo.png" alt="Logo" draggable="true" />
```

- **`data-*`**: atributos personalizados, accesibles desde JS vía `dataset`.

```html
<li data-user-id="42" data-role="admin">Ana</li>
<!-- JS: elemento.dataset.userId -> "42" | elemento.dataset.role -> "admin" -->
```

- **`lang`** / **`dir`**: idioma y direccionalidad del texto.

```html
<p lang="en">This paragraph is in English</p>
<p dir="rtl">نص من اليمين لليسار</p>
```

- **`spellcheck`** / **`translate`**: corrección ortográfica y traducción automática.

```html
<textarea spellcheck="false"></textarea>
<span translate="no">NombreDeMarca</span>
```

- **`accesskey`**: sugiere un atajo de teclado para el elemento.

```html
<a href="/" accesskey="i">Inicio</a>
```

- **`inert`**: desactiva foco, clics y selección en el elemento y sus descendientes.

```html
<div inert>Contenido temporalmente inactivo</div>
```

Otros atributos globales frecuentes:

| Atributo | Uso |
| --- | --- |
| `autofocus` | enfoca el elemento automáticamente al cargar la página |
| `autocapitalize` | controla la capitalización automática (teclados móviles) |
| `inputmode` | sugiere el tipo de teclado virtual a mostrar |
| `role` / `aria-*` | accesibilidad (ver [Accesibilidad y ARIA](#accesibilidad-a11y-y-aria)) |
| `nonce` | habilita scripts/estilos bajo una política CSP |
| `popover` | declara el elemento como popover nativo |
| `slot` / `part` | integración con Shadow DOM / Web Components |

---

## Elementos obsoletos (evitar)

Etiquetas presentacionales o de arquitecturas antiguas. HTML describe contenido; el estilo va en CSS.

| Obsoleto | Alternativa |
| --- | --- |
| `<center>` | CSS `text-align` / `margin: auto` |
| `<font>` | CSS `font-*`, `color` |
| `<big>`, `<tt>`, `<strike>` | CSS o `<s>`, `<code>` |
| `<acronym>` | `<abbr>` |
| `<marquee>`, `<blink>` | CSS `animation` |
| `<frame>`, `<frameset>` | `<iframe>` |
| `<applet>` | sin alternativa moderna; evitar |

---

## Títulos (Headings)

Los títulos definen la **jerarquía del contenido**.  
Van desde `<h1>` (más importante) hasta `<h6>` (menos importante).

```html
<h1>Título principal</h1>
<h2>Sección</h2>
<h3>Subsección</h3>
<h4>Detalle</h4>
<h5>Nota</h5>
<h6>Comentario</h6>
```

- Se recomienda **un solo `<h1>` por documento**.
- Los títulos ayudan a la **accesibilidad y SEO**.
- No deben usarse solo por tamaño visual (eso es tarea de CSS).

---

## Etiquetas de texto (Text Content)

### Párrafos

```html
<p>Este es un párrafo de texto.</p>
```

- Agrupa texto en bloques.
- Es un elemento de bloque.

---

### Énfasis semántico

- **`<strong>`**: importancia semántica (énfasis fuerte)
- **`<em>`**: énfasis semántico leve

```html
<p>
  Este texto es <strong>importante</strong> y este está <em>enfatizado</em>.
</p>
```

> Usa `<strong>` y `<em>` en lugar de `<b>` y `<i>` cuando el significado importe.

---

### Estilo sin semántica

- **`<b>`**: negrita visual
- **`<i>`**: cursiva visual

```html
<p>Texto en <b>negrita</b> y texto en <i>cursiva</i>.</p>
```

---

### Texto pequeño

```html
<small>Texto secundario o aclaración.</small>
```

- Usado para notas legales, disclaimers, etc.

---

### Texto resaltado

```html
<p>Esto es un <mark>texto resaltado</mark>.</p>
```

---

### Texto eliminado e insertado

```html
<p>
  Precio anterior: <del>$100</del><br />
  Precio nuevo: <ins>$80</ins>
</p>
```

---

### Subíndices y superíndices

```html
<p>H<sub>2</sub>O</p>
<p>x<sup>2</sup></p>
```

---

### Código en línea

```html
<p>Usa el comando <code>npm install</code> para instalar.</p>
```

---

### Bloque de código

```html
<pre>
<code>
function saludar() {
  console.log("Hola mundo");
}
</code>
</pre>
```

- `<pre>` conserva espacios y saltos de línea.
- `<code>` representa código fuente.

---

### Citas

- **Cita en bloque**

```html
<blockquote>La simplicidad es la máxima sofisticación.</blockquote>
```

- **Cita en línea**

```html
<p>Como dijo Einstein: <q>Dios no juega a los dados</q>.</p>
```

---

### Saltos y separadores

- **Salto de línea**

```html
Texto línea 1<br />
Texto línea 2
```

- **Separador horizontal**

```html
<hr />
```

---

### Contenedor de texto genérico

```html
<span>Texto dentro de un span</span>
```

- Elemento en línea.
- Muy usado junto con CSS.

---

### Abreviaturas

```html
<abbr title="HyperText Markup Language">HTML</abbr>
```

- Mejora accesibilidad y comprensión.

---

### Referencias y citas de obras

```html
<cite>El Quijote</cite>
```

---

### Fechas y tiempo

```html
<time datetime="2025-01-10">10 de enero de 2025</time>
```

- Útil para eventos, artículos y SEO.

---

## Listas

Las listas permiten agrupar información relacionada.  
Existen **listas no ordenadas**, **ordenadas** y **de definición**.

---

## Listas no ordenadas (`<ul>`)

Se usan cuando el orden **no importa**.

```html
<ul>
  <li>HTML</li>
  <li>CSS</li>
  <li>JavaScript</li>
</ul>
```

- `<ul>`: contenedor de la lista.
- `<li>`: elemento de la lista.

---

### Listas no ordenadas anidadas

```html
<ul>
  <li>
    Frontend
    <ul>
      <li>HTML</li>
      <li>CSS</li>
    </ul>
  </li>
  <li>Backend</li>
</ul>
```

---

## Listas ordenadas (`<ol>`)

Se usan cuando el **orden es relevante**.

```html
<ol>
  <li>Instalar dependencias</li>
  <li>Configurar proyecto</li>
  <li>Ejecutar aplicación</li>
</ol>
```

---

### Tipo de numeración

```html
<ol type="A">
  <li>Opción A</li>
  <li>Opción B</li>
</ol>
```

Valores comunes de `type`:

- `1` (default)
- `A`, `a`
- `I`, `i`

---

### Inicio personalizado

```html
<ol start="5">
  <li>Paso cinco</li>
  <li>Paso seis</li>
</ol>
```

---

### Orden inverso

```html
<ol reversed>
  <li>Último</li>
  <li>Primero</li>
</ol>
```

---

## Listas de definición (`<dl>`)

Se usan para términos y descripciones.

```html
<dl>
  <dt>HTML</dt>
  <dd>Lenguaje de marcado para la web</dd>

  <dt>CSS</dt>
  <dd>Lenguaje de estilos</dd>
</dl>
```

- `<dt>`: término.
- `<dd>`: definición.

---

## Enlaces (`<a>`)

Permiten navegar entre páginas, recursos o acciones.

```html
<a href="https://example.com">Ir a Example</a>
```

---

### Enlace externo en nueva pestaña

```html
<a href="https://example.com" target="_blank" rel="noopener noreferrer">
  Abrir Example
</a>
```

- `target="_blank"`: abre en nueva pestaña.
- `rel="noopener noreferrer"`: seguridad y rendimiento.

---

### Enlace interno

```html
<a href="/contacto.html">Contacto</a>
```

---

### Enlace a sección de la misma página

```html
<a href="#seccion-html">Ir a HTML</a>

<h2 id="seccion-html">HTML</h2>
```

---

### Enlace de correo (`mailto`)

```html
<a href="mailto:correo@ejemplo.com">Enviar correo</a>
```

Con asunto y cuerpo:

```html
<a
  href="mailto:correo@ejemplo.com?subject=Consulta&body=Hola%20quiero%20información"
>
  Contactar
</a>
```

---

### Enlace telefónico

```html
<a href="tel:+573001234567">Llamar</a>
```

---

### Enlace de descarga

```html
<a href="archivo.pdf" download>Descargar PDF</a>
```

---

### Enlace con imagen

```html
<a href="https://example.com">
  <img src="logo.png" alt="Ir a Example" />
</a>
```

---

## Atributos importantes de `<a>`

- `href`: destino del enlace.
- `target`: dónde se abre.
- `rel`: relación y seguridad.
- `download`: fuerza descarga.
- `title`: texto informativo adicional.

```html
<a
  href="https://example.com"
  title="Sitio oficial"
  target="_blank"
  rel="noopener noreferrer"
>
  Example
</a>
```

---

## Buenas prácticas de enlaces

- Usa texto descriptivo ("Ver documentación", "Ir al inicio", "Descargar PDF").
- Evita "haz clic aquí".
- Si usas `target="_blank"`, añade `rel="noopener noreferrer"`.
- No enlaces texto que no sea interactivo.

---

## Etiquetas semánticas (estructura de página)

Las etiquetas semánticas describen **qué es cada bloque** de la página.  
Mejoran accesibilidad, SEO y mantenibilidad.

---

## Jerarquía recomendada (layout típico)

```html
<body>
  <header>...</header>

  <main>
    <section>...</section>
    <section>...</section>
  </main>

  <footer>...</footer>
</body>
```

- `header`: cabecera del sitio o de una sección.
- `main`: contenido principal (único por página).
- `footer`: pie del sitio o de una sección.

---

## Estructura completa recomendada

```html
<body>
  <!-- Cabecera global del sitio -->
  <header>
    <nav aria-label="Navegación principal">
      <a href="/">Inicio</a>
      <a href="/blog.html">Blog</a>
      <a href="/contacto.html">Contacto</a>
    </nav>
  </header>

  <!-- Contenido principal (solo 1 main por página) -->
  <main>
    <!-- Bloque temático dentro del main -->
    <section aria-labelledby="titulo-bienvenida">
      <h1 id="titulo-bienvenida">Bienvenido</h1>
      <p>Contenido principal de la página.</p>
    </section>

    <!-- Artículos independientes (por ejemplo: posts, cards, noticias) -->
    <section aria-labelledby="titulo-articulos">
      <h2 id="titulo-articulos">Últimos artículos</h2>

      <article>
        <header>
          <h3>Título del artículo 1</h3>
          <p><time datetime="2025-12-15">15 dic 2025</time></p>
        </header>

        <p>Resumen del artículo...</p>

        <footer>
          <a href="/articulo-1.html">Leer más</a>
        </footer>
      </article>

      <article>
        <header>
          <h3>Título del artículo 2</h3>
          <p><time datetime="2025-12-10">10 dic 2025</time></p>
        </header>

        <p>Resumen del artículo...</p>

        <footer>
          <a href="/articulo-2.html">Leer más</a>
        </footer>
      </article>
    </section>

    <!-- Contenido complementario del main -->
    <aside aria-label="Contenido relacionado">
      <h2>Recursos</h2>
      <ul>
        <li><a href="/docs.html">Documentación</a></li>
        <li><a href="/faq.html">Preguntas frecuentes</a></li>
      </ul>
    </aside>
  </main>

  <!-- Pie de página global -->
  <footer>
    <p>© 2025 Mi Sitio</p>
  </footer>
</body>
```

---

## ¿Cuándo usar cada etiqueta?

### `<header>`

- Cabecera del sitio (logo, navegación, búsqueda).
- También puede existir dentro de `article` o `section` como cabecera local.

```html
<header>
  <h1>Mi Sitio</h1>
</header>
```

---

### `<nav>`

- Bloque de navegación principal o secundaria.

```html
<nav aria-label="Navegación principal">
  <a href="/">Inicio</a>
  <a href="/blog.html">Blog</a>
</nav>
```

---

### `<main>`

- Contenido principal.
- Debe existir **una sola vez** por documento.

```html
<main>
  <h1>Título principal de la página</h1>
</main>
```

---

### `<section>`

- Agrupa contenido por tema.
- Ideal cuando el bloque tiene **título** (`h2`, `h3`, etc.).

```html
<section aria-labelledby="titulo-servicios">
  <h2 id="titulo-servicios">Servicios</h2>
  <p>Contenido de servicios...</p>
</section>
```

---

### `<article>`

- Contenido independiente y reutilizable:
  - post, noticia, card, comentario, producto, publicación.

```html
<article>
  <h2>Noticia</h2>
  <p>Contenido...</p>
</article>
```

---

### `<aside>`

- Contenido complementario:
  - sidebar, enlaces relacionados, anuncios, widgets.

```html
<aside>
  <h2>Relacionado</h2>
  <p>Contenido adicional...</p>
</aside>
```

---

### `<footer>`

- Pie de página global o de una sección/artículo.
- Puede incluir autor, links legales, contacto, etc.

```html
<footer>
  <p>© 2025</p>
</footer>
```

---

## `<div>` (contenedor genérico)

La etiqueta `<div>` es un contenedor **no semántico**.  
No aporta significado al contenido: solo agrupa elementos.

Se usa cuando **no existe una etiqueta semántica adecuada**.

---

## Uso básico

```html
<div>
  <p>Contenido dentro de un div</p>
</div>
```

- Es un elemento de **bloque**.
- No tiene significado por sí mismo.
- Muy usado para estructura y estilos con CSS.

---

## `<div>` como contenedor de layout

```html
<div class="card">
  <h3>Título</h3>
  <p>Descripción del contenido.</p>
</div>
```

- Útil para componentes visuales (cards, modales, grids).
- El significado lo aporta el **contexto** y las clases, no la etiqueta.

---

## `<div>` vs etiquetas semánticas

❌ Uso incorrecto (cuando existe semántica):

```html
<div class="header">
  <h1>Mi sitio</h1>
</div>
```

✅ Uso correcto:

```html
<header>
  <h1>Mi sitio</h1>
</header>
```

Regla:

- **Primero** intenta usar: `header`, `main`, `section`, `article`, `aside`, `footer`.
- Usa `<div>` **solo si ninguna encaja**.

---

## `<div>` con clases e IDs

```html
<div id="contenedor" class="wrapper principal">Contenido</div>
```

- `id`: identificador único.
- `class`: estilos reutilizables.
- Muy usado para CSS y JavaScript.

---

## `<div>` como agrupador visual

```html
<form>
  <div class="campo">
    <label for="email">Correo</label>
    <input id="email" type="email" />
  </div>

  <div class="campo">
    <label for="pass">Contraseña</label>
    <input id="pass" type="password" />
  </div>
</form>
```

- Agrupa visualmente campos relacionados.
- No reemplaza `fieldset` cuando hay relación semántica.

---

## `<div>` y accesibilidad

- `<div>` **no comunica significado** a lectores de pantalla.
- Si cumple un rol específico, considera:
  - Etiquetas semánticas.
  - O atributos ARIA (solo si es necesario).

Ejemplo con ARIA:

```html
<div role="alert">Error al enviar el formulario</div>
```

---

## Cuándo usar `<div>`

✔️ Componentes visuales  
✔️ Layout con CSS Grid / Flexbox  
✔️ Wrappers para estilos o JS  
✔️ Cuando no hay alternativa semántica

❌ Para encabezados, navegación, artículos, secciones

---

## Ejemplo recomendado (uso correcto)

```html
<main>
  <section>
    <h2>Productos</h2>

    <div class="grid-productos">
      <div class="producto">
        <h3>Producto A</h3>
        <p>$50</p>
      </div>

      <div class="producto">
        <h3>Producto B</h3>
        <p>$70</p>
      </div>
    </div>
  </section>
</main>
```

---

## Resumen rápido

- `<div>` es genérico y no semántico.
- Úsalo como **último recurso**.
- El significado debe venir del HTML semántico, no del CSS.
- Ideal para estructura visual y componentes.

---

## Buenas prácticas de HTML semántico

- No uses `section` si no tiene un propósito temático claro.
- Usa `article` cuando el bloque tenga sentido por sí mismo.
- Mantén una jerarquía de títulos coherente (`h1` → `h2` → `h3`...).
- Usa `aria-label` o `aria-labelledby` cuando el bloque no tenga un título visible.
- No uses `<div>` si existe una etiqueta semántica adecuada.

---

## Formularios (Forms)

Los formularios permiten capturar datos del usuario y enviarlos a un servidor o manejarlos con JavaScript.

Buenas prácticas clave:

- Siempre usa `<label>` asociado a cada control.
- Usa `name` en los campos que quieras enviar.
- Prefiere tipos adecuados (`email`, `date`, `number`, etc.) para validación nativa y mejor UX.
- Usa validación HTML como primera capa (`required`, `min`, `max`, `pattern`).

---

## `<form>` (contenedor del formulario)

```html
<form action="/registro" method="post" autocomplete="on" novalidate>
  <!-- campos -->
</form>
```

Atributos comunes:

- `action`: URL destino donde se envían los datos.
- `method`: `get` o `post`.
  - `get`: datos en la URL (búsquedas, filtros).
  - `post`: datos en el body (registro, login).
- `autocomplete`: `on` / `off`.
- `novalidate`: desactiva validación nativa del navegador (si la manejarás con JS).

---

## `<label>` (etiqueta asociada al campo)

### Recomendado: `for` + `id`

```html
<label for="email">Correo</label> <input id="email" name="email" type="email" />
```

- `for` debe coincidir con el `id` del input.
- Mejora accesibilidad y hace clicable el texto.

### Alternativa: input dentro del label

```html
<label>
  Correo
  <input name="email" type="email" />
</label>
```

---

## `<input>` (tipos y atributos)

Atributos base importantes:

- `type`: tipo de input.
- `name`: clave con la que se envía el dato.
- `value`: valor actual o valor por defecto.
- `placeholder`: texto guía.
- `required`: obligatorio.
- `disabled`: deshabilitado (no se envía).
- `readonly`: solo lectura (sí se envía).
- `autocomplete`: sugerencias del navegador.

---

## Tipos de `<input>` más usados

### Texto

```html
<label for="nombre">Nombre</label>
<input id="nombre" name="nombre" type="text" placeholder="Tu nombre" required />
```

---

### Email

```html
<label for="correo">Correo</label>
<input
  id="correo"
  name="correo"
  type="email"
  placeholder="correo@dominio.com"
  required
/>
```

---

### Password

```html
<label for="pass">Contraseña</label>
<input id="pass" name="password" type="password" minlength="8" required />
```

---

### Número (`min`, `max`, `step`)

```html
<label for="edad">Edad</label>
<input
  id="edad"
  name="edad"
  type="number"
  min="1"
  max="120"
  step="1"
  required
/>
```

---

### Fecha (`min`, `max`)

```html
<label for="fecha">Fecha de nacimiento</label>
<input
  id="fecha"
  name="fecha_nacimiento"
  type="date"
  min="1900-01-01"
  max="2025-12-31"
  required
/>
```

---

### Hora

```html
<label for="hora">Hora</label>
<input id="hora" name="hora" type="time" required />
```

---

### Fecha y hora local

```html
<label for="cita">Cita</label>
<input id="cita" name="cita" type="datetime-local" required />
```

---

### Mes / Semana

```html
<label for="mes">Mes</label>
<input id="mes" name="mes" type="month" />

<label for="semana">Semana</label>
<input id="semana" name="semana" type="week" />
```

---

### Color

```html
<label for="color">Color favorito</label>
<input id="color" name="color" type="color" value="#5395c1" />
```

---

### Teléfono

```html
<label for="tel">Teléfono</label>
<input id="tel" name="telefono" type="tel" placeholder="+57 300 123 4567" />
```

---

### URL

```html
<label for="url">Sitio web</label>
<input id="url" name="sitio" type="url" placeholder="https://..." />
```

---

### Búsqueda

```html
<label for="q">Buscar</label>
<input id="q" name="q" type="search" placeholder="Buscar..." />
```

---

### Archivo

```html
<label for="archivo">Subir archivo</label>
<input id="archivo" name="archivo" type="file" accept=".pdf,image/*" />
```

> Para subir archivos a servidor normalmente se requiere: `enctype="multipart/form-data"` en `<form>`.

---

### Rango (`min`, `max`, `step`)

```html
<label for="nivel">Nivel</label>
<input
  id="nivel"
  name="nivel"
  type="range"
  min="0"
  max="10"
  step="1"
  value="5"
/>
```

---

### Checkbox (booleano)

```html
<label>
  <input name="terminos" type="checkbox" required />
  Acepto términos y condiciones
</label>
```

- Si está marcado, se envía el `value` (por defecto suele ser `"on"`).
- Puedes definirlo explícito:

```html
<label>
  <input name="suscripcion" type="checkbox" value="si" />
  Quiero suscribirme
</label>
```

---

### Radio (selección única)

```html
<p>Género</p>

<label>
  <input type="radio" name="genero" value="m" required />
  Masculino
</label>

<label>
  <input type="radio" name="genero" value="f" />
  Femenino
</label>

<label>
  <input type="radio" name="genero" value="otro" />
  Otro
</label>
```

- Los radios comparten el mismo `name` para que sea selección única.

---

### Hidden (dato invisible)

```html
<input type="hidden" name="origen" value="landing_01" />
```

---

## `<textarea>` (texto largo)

```html
<label for="bio">Biografía</label>
<textarea
  id="bio"
  name="bio"
  rows="4"
  placeholder="Escribe algo sobre ti..."
  required
></textarea>
```

Atributos útiles:

- `rows`, `cols`
- `maxlength`, `minlength`
- `placeholder`, `required`

---

## `<select>` + `<option>` (lista desplegable)

```html
<label for="pais">País</label>
<select id="pais" name="pais" required>
  <option value="" selected disabled>Selecciona un país</option>
  <option value="co">Colombia</option>
  <option value="pe">Perú</option>
  <option value="mx">México</option>
</select>
```

- `option value=""` + `disabled` ayuda a forzar elección real.
- `selected` marca el valor por defecto.

### Select múltiple

```html
<label for="tags">Intereses</label>
<select id="tags" name="tags" multiple>
  <option value="frontend">Frontend</option>
  <option value="backend">Backend</option>
  <option value="devops">DevOps</option>
</select>
```

---

## `<datalist>` (sugerencias de autocompletado)

```html
<label for="navegador">Navegador favorito</label>
<input list="navegadores" id="navegador" name="navegador" />

<datalist id="navegadores">
  <option value="Chrome"></option>
  <option value="Firefox"></option>
  <option value="Safari"></option>
</datalist>
```

- El atributo `list` del `<input>` referencia el `id` del `<datalist>`.
- A diferencia de `<select>`, el usuario puede escribir un valor distinto a las opciones sugeridas.

---

## `<progress>` (progreso de una tarea)

```html
<progress value="70" max="100">70%</progress>
```

- `value`: progreso actual. `max`: valor total (por defecto `1`).
- Sin `value` se muestra en estado indeterminado (cargando).

---

## `<meter>` (valor dentro de un rango conocido)

```html
<label for="disco">Uso de disco</label>
<meter id="disco" value="6" min="0" max="10" low="3" high="8" optimum="2">
  6 de 10
</meter>
```

- Representa una **medición escalar** (uso de disco, puntuación, votos), no una tarea en curso.
- `low` / `high` / `optimum` matizan qué rango del valor se considera bueno o malo.

---

## `<output>` (resultado de un cálculo)

```html
<form oninput="resultado.value = Number(a.value) + Number(b.value)">
  <input id="a" name="a" type="number" value="0" />
  +
  <input id="b" name="b" type="number" value="0" />
  =
  <output id="resultado" name="resultado" for="a b">0</output>
</form>
```

- `for`: ids de los controles que participan en el resultado.
- Se comporta como un campo más del formulario (participa en `FormData`).

---

## Botones (`button` e inputs tipo botón)

### `button` recomendado

```html
<button type="submit">Enviar</button>
<button type="reset">Limpiar</button>
<button type="button">Acción JS</button>
```

- `type="submit"`: envía el formulario.
- `type="reset"`: restaura valores iniciales.
- `type="button"`: no envía, útil para JS.

### Inputs tipo botón

```html
<input type="submit" value="Enviar" />
<input type="reset" value="Limpiar" />
<input type="button" value="Acción JS" />
```

---

## `fieldset` y `legend` (agrupar campos)

```html
<fieldset>
  <legend>Datos de acceso</legend>

  <label for="user">Usuario</label>
  <input id="user" name="user" type="text" required />

  <label for="pass2">Contraseña</label>
  <input id="pass2" name="pass2" type="password" required />
</fieldset>
```

- Agrupa campos relacionados.
- `legend` describe el grupo (accesibilidad).

---

## Validaciones HTML (inputs)

### `required`

```html
<input name="nombre" type="text" required />
```

---

### `placeholder`

```html
<input name="correo" type="email" placeholder="correo@dominio.com" />
```

---

### `pattern` (regex)

```html
<label for="codigo">Código (3 letras + 3 números)</label>
<input
  id="codigo"
  name="codigo"
  type="text"
  pattern="[A-Za-z]{3}[0-9]{3}"
  placeholder="ABC123"
  required
/>
```

> `pattern` aplica en `text`, `tel`, `email`, etc. No aplica en `number`.

---

### `min` / `max`

- En números:

```html
<input name="cantidad" type="number" min="1" max="50" />
```

- En fechas:

```html
<input name="inicio" type="date" min="2025-01-01" max="2025-12-31" />
```

- En rango:

```html
<input name="nivel" type="range" min="0" max="100" />
```

---

### `step` (saltos permitidos)

- Números decimales:

```html
<input name="precio" type="number" min="0" step="0.01" />
```

- Rango:

```html
<input name="progreso" type="range" min="0" max="10" step="2" />
```

- Fechas (en `date`, step = días):

```html
<input name="fecha" type="date" step="7" />
```

---

### `minlength` / `maxlength`

```html
<input name="usuario" type="text" minlength="3" maxlength="20" required />
<textarea name="comentario" minlength="10" maxlength="200"></textarea>
```

---

## Ejemplo completo (formulario recomendado)

```html
<form action="/registro" method="post" autocomplete="on">
  <fieldset>
    <legend>Registro</legend>

    <label for="nombre">Nombre</label>
    <input
      id="nombre"
      name="nombre"
      type="text"
      placeholder="Juan Pérez"
      required
    />

    <label for="email">Correo</label>
    <input
      id="email"
      name="email"
      type="email"
      placeholder="correo@dominio.com"
      required
    />

    <label for="password">Contraseña</label>
    <input
      id="password"
      name="password"
      type="password"
      minlength="8"
      required
    />

    <label for="fecha">Fecha de nacimiento</label>
    <input
      id="fecha"
      name="fecha_nacimiento"
      type="date"
      min="1900-01-01"
      max="2025-12-31"
      required
    />

    <p>Rol</p>
    <label
      ><input type="radio" name="rol" value="student" required />
      Estudiante</label
    >
    <label><input type="radio" name="rol" value="teacher" /> Docente</label>

    <label for="pais">País</label>
    <select id="pais" name="pais" required>
      <option value="" selected disabled>Selecciona un país</option>
      <option value="co">Colombia</option>
      <option value="mx">México</option>
      <option value="pe">Perú</option>
    </select>

    <label for="bio">Biografía</label>
    <textarea
      id="bio"
      name="bio"
      rows="4"
      placeholder="Cuéntanos sobre ti..."
    ></textarea>

    <label>
      <input name="terminos" type="checkbox" required />
      Acepto términos y condiciones
    </label>

    <button type="submit">Enviar</button>
    <button type="reset">Limpiar</button>
  </fieldset>
</form>
```

## Contenido multimedia: imágenes

Las imágenes son parte del **contenido multimedia** del HTML.  
Su correcta implementación impacta directamente en **rendimiento**, **accesibilidad**, **SEO** y **experiencia de usuario**.

HTML define **qué imagen usar y en qué contexto**; CSS define **cómo se ve**.

---

## `<img>`

Etiqueta base para insertar imágenes.

```html
<img src="imagen.jpg" alt="Descripción de la imagen" />
```

Atributos esenciales:

- `src`: ruta o URL de la imagen.
- `alt`: descripción textual (obligatorio).
- `width` / `height`: dimensiones intrínsecas (recomendado).

---

## Tamaño explícito (layout estable)

```html
<img src="logo.png" alt="Logo del sitio" width="200" height="100" />
```

- Permite al navegador **reservar espacio** antes de cargar la imagen.
- Reduce _layout shift_ (CLS).

---

## Accesibilidad (`alt`)

```html
<img src="grafica.png" alt="Gráfica de ventas del año 2024" />
```

Buenas prácticas:

- Describe el **significado**, no solo lo visual.
- Si la imagen es decorativa → `alt=""`.
- Nunca omitas `alt`.

---

## `<figure>` y `<figcaption>`

Para contenido visual con **significado semántico propio**.

```html
<figure>
  <img src="arquitectura.png" alt="Diagrama de arquitectura del sistema" />
  <figcaption>Arquitectura general de la aplicación</figcaption>
</figure>
```

- `<figure>` agrupa el contenido.
- `<figcaption>` explica o titula.
- Ideal para diagramas, gráficos, ilustraciones.

---

## Imagen como enlace

```html
<a href="https://example.com">
  <img src="banner.png" alt="Ir al sitio oficial de Example" />
</a>
```

- El `alt` debe describir la **acción del enlace**, no la imagen.

---

## Imágenes responsive (`srcset` + `sizes`)

Permiten servir **la imagen adecuada según el tamaño real en pantalla**.

```html
<img
  src="imagen-800.jpg"
  srcset="imagen-400.jpg 400w, imagen-800.jpg 800w, imagen-1200.jpg 1200w"
  sizes="(max-width: 600px) 100vw, 800px"
  alt="Paisaje de montaña"
/>
```

### Cómo funciona:

- `srcset`: imágenes disponibles con su ancho real (`w`).
- `sizes`: condiciones de tamaño en CSS.
- El navegador decide **qué archivo descargar**.

---

## Condiciones de tamaño (`sizes`)

```html
sizes=" (max-width: 480px) 100vw, (max-width: 1024px) 50vw, 800px "
```

Interpretación:

- Móviles: ocupa todo el ancho (`100vw`).
- Tablets: mitad del viewport.
- Desktop: máximo 800px.

---

## `<picture>` con condiciones (breakpoints reales)

No solo sirve para formatos alternativos, también para **condiciones de tamaño**.

```html
<picture>
  <source media="(min-width: 1024px)" srcset="hero-desktop.jpg" />
  <source media="(min-width: 600px)" srcset="hero-tablet.jpg" />
  <img src="hero-mobile.jpg" alt="Imagen principal del sitio" />
</picture>
```

- `media`: condiciones tipo CSS.
- Se evalúan de arriba hacia abajo.
- `<img>` es el **fallback obligatorio**.

---

## `<picture>` combinando formatos + condiciones

```html
<picture>
  <source type="image/avif" srcset="imagen.avif" />
  <source type="image/webp" srcset="imagen.webp" />
  <source media="(min-width: 1024px)" srcset="imagen-desktop.jpg" />
  <img src="imagen-mobile.jpg" alt="Imagen adaptable y optimizada" />
</picture>
```

- Primero formato moderno.
- Luego condiciones.
- Último fallback compatible.

---

## Carga diferida (lazy loading)

```html
<img src="foto.jpg" alt="Foto del producto" loading="lazy" />
```

- Carga la imagen **solo cuando entra en viewport**.
- Ideal para galerías y páginas largas.

---

## Decodificación de imágenes (`decoding`)

Controla **cuándo se decodifica** la imagen.

```html
<img src="foto.jpg" alt="Foto" decoding="async" />
```

Valores:

- `auto` (default)
- `async`: no bloquea el render
- `sync`: prioriza render inmediato

> `decoding="async"` es recomendado en la mayoría de casos.

---

## Imágenes decorativas

```html
<img src="decoracion.svg" alt="" />
```

- No aportan información.
- `alt=""` evita ruido en lectores de pantalla.

---

## SVG como imagen

```html
<img src="icono.svg" alt="Icono de usuario" />
```

Ventajas:

- Escalable sin pérdida.
- Ideal para logos e íconos.

> Para animaciones o estilos complejos, usa `<svg>` embebido.

---

## Rutas de imágenes

```html
<img src="/assets/img/logo.png" alt="Logo" />
<img src="./imagenes/foto.jpg" alt="Foto local" />
<img src="https://cdn.example.com/img.png" alt="Imagen remota" />
```

---

## Formatos de imagen recomendados

- **AVIF**: máxima compresión (moderno).
- **WebP**: excelente balance calidad/peso.
- **JPEG**: fotografías.
- **PNG**: transparencia real.
- **SVG**: gráficos vectoriales.

Recomendación general:

- Usa **AVIF o WebP** siempre que puedas.
- Optimiza antes de subir.

Herramienta recomendada:  
👉 https://tinypng.com

---

## Errores comunes

- Omitir `alt`.
- No usar `srcset` en imágenes grandes.
- Usar `<picture>` sin `<img>` fallback.
- Cargar imágenes gigantes para mobile.
- Usar imágenes como texto crítico.

---

## Video (`<video>`)

La etiqueta `<video>` permite incrustar video nativo en el navegador sin plugins.  
Soporta múltiples fuentes para mejorar compatibilidad.

---

## Estructura base

```html
<video src="video.mp4" controls></video>
```

- `controls`: muestra controles del navegador.
- `src`: fuente del video (opcional si usas `<source>`).

---

## Video con tamaño (`width` / `height`)

```html
<video src="intro.mp4" controls width="720" height="405"></video>
```

---

## Video con múltiples fuentes (`<source>`)

Se recomienda usar `<source>` para ofrecer formatos alternativos.

```html
<video controls width="720" height="405">
  <source src="video.webm" type="video/webm" />
  <source src="video.mp4" type="video/mp4" />
  Tu navegador no soporta video HTML5.
</video>
```

- El navegador usa la **primera fuente compatible**.
- El texto final es el **fallback** (se muestra si no soporta `<video>`).

---

## Atributo `type` en `<source>`

```html
<source src="video.mp4" type="video/mp4" />
<source src="video.webm" type="video/webm" />
```

- Ayuda al navegador a decidir sin descargar/analizar el archivo.
- Mejora rendimiento y compatibilidad.

---

## `poster` (imagen previa)

Muestra una imagen antes de reproducir.

```html
<video controls poster="poster.jpg" width="720">
  <source src="video.mp4" type="video/mp4" />
  Tu navegador no soporta video HTML5.
</video>
```

---

## `preload` (carga anticipada)

Controla qué tanto debe cargar el navegador antes de reproducir.

```html
<video controls preload="metadata">
  <source src="video.mp4" type="video/mp4" />
</video>
```

Valores:

- `none`: no precarga (mejor si hay muchos videos).
- `metadata`: carga solo metadatos (duración, dimensiones).
- `auto`: el navegador decide (puede descargar más).

---

## `autoplay`, `muted`, `loop`

```html
<video autoplay muted loop playsinline>
  <source src="hero.mp4" type="video/mp4" />
  Tu navegador no soporta video HTML5.
</video>
```

- `autoplay`: intenta reproducir automáticamente.
- `muted`: necesario en la mayoría de navegadores para permitir autoplay.
- `loop`: repite el video.
- `playsinline`: evita pantalla completa automática en móviles.

---

## `controlslist` (opcional, soporte parcial)

Permite sugerir restricciones a los controles.

```html
<video controls controlslist="nodownload noplaybackrate">
  <source src="video.mp4" type="video/mp4" />
</video>
```

> No es una protección real, solo una sugerencia UI.

---

## `disablepictureinpicture` (opcional)

```html
<video controls disablepictureinpicture>
  <source src="video.mp4" type="video/mp4" />
</video>
```

---

## Texto fallback dentro de `<video>`

```html
<video controls>
  <source src="video.mp4" type="video/mp4" />
  Tu navegador no soporta la etiqueta video. Descarga el archivo
  <a href="video.mp4">aquí</a>.
</video>
```

- Solo se ve si el navegador no soporta `<video>`.

---

## Ejemplo recomendado (completo)

```html
<video controls width="800" height="450" poster="poster.jpg" preload="metadata">
  <source src="video.webm" type="video/webm" />
  <source src="video.mp4" type="video/mp4" />
  Tu navegador no soporta video HTML5. Puedes descargarlo
  <a href="video.mp4">aquí</a>.
</video>
```

---

## Audio (`<audio>`)

La etiqueta `<audio>` permite reproducir sonido nativo en el navegador  
(música, podcasts, efectos de sonido, narraciones, etc.).

Funciona de forma muy similar a `<video>`, pero sin contenido visual.

---

## Estructura base

```html
<audio src="audio.mp3" controls></audio>
```

- `controls`: muestra controles de reproducción.
- `src`: archivo de audio (opcional si se usan `<source>`).

---

## Audio con múltiples fuentes (`<source>`)

Se recomienda usar `<source>` para compatibilidad entre navegadores.

```html
<audio controls>
  <source src="audio.ogg" type="audio/ogg" />
  <source src="audio.mp3" type="audio/mpeg" />
  Tu navegador no soporta audio HTML5.
</audio>
```

- El navegador elige la **primera fuente compatible**.
- El texto final es el **fallback**.

---

## Atributo `type` en `<source>`

```html
<source src="audio.mp3" type="audio/mpeg" />
<source src="audio.ogg" type="audio/ogg" />
```

- Permite detectar compatibilidad sin descargar el archivo.
- Mejora rendimiento.

---

## `preload` (carga anticipada)

Controla qué tanto del audio se carga antes de reproducir.

```html
<audio controls preload="metadata">
  <source src="audio.mp3" type="audio/mpeg" />
</audio>
```

Valores:

- `none`: no precargar nada.
- `metadata`: solo duración y metadatos.
- `auto`: el navegador decide.

> Recomendado: `metadata` para evitar descargas innecesarias.

---

## `autoplay`, `muted`, `loop`

```html
<audio autoplay muted loop>
  <source src="audio.mp3" type="audio/mpeg" />
</audio>
```

- `autoplay`: intenta reproducir automáticamente.
- `muted`: necesario en algunos navegadores.
- `loop`: reproduce en bucle.

> Autoplay suele estar bloqueado sin interacción del usuario.

---

## `controlslist` (soporte parcial)

```html
<audio controls controlslist="nodownload">
  <source src="audio.mp3" type="audio/mpeg" />
</audio>
```

- Sugiere ocultar opciones como descarga.
- No es seguridad real.

---

## Texto fallback dentro de `<audio>`

```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg" />
  Tu navegador no soporta audio HTML5. Puedes descargarlo
  <a href="audio.mp3">aquí</a>.
</audio>
```

- Se muestra solo si `<audio>` no es soportado.

---

## Ejemplo completo recomendado

```html
<audio controls preload="metadata">
  <source src="audio.ogg" type="audio/ogg" />
  <source src="audio.mp3" type="audio/mpeg" />
  Tu navegador no soporta audio HTML5. Descárgalo
  <a href="audio.mp3">aquí</a>.
</audio>
```

---

## Buenas prácticas de audio y video

- Usa siempre `controls`.
- Ofrece múltiples formatos (`mp3`, `ogg`).
- Evita `autoplay` sin interacción.
- Usa `preload="metadata"` por defecto.
- Proporciona texto fallback.

---

## `<iframe>` (documento anidado)

```html
<iframe
  src="https://example.com"
  title="Sitio embebido"
  width="600"
  height="400"
  loading="lazy"
></iframe>
```

- `title`: **obligatorio** para accesibilidad (describe el contenido embebido).
- `loading="lazy"`: difiere la carga hasta que el iframe entra en el viewport.
- `sandbox`: restringe capacidades del contenido embebido (scripts, formularios, popups).

```html
<iframe
  src="widget.html"
  title="Widget externo"
  sandbox="allow-scripts allow-same-origin"
></iframe>
```

---

## `<embed>` y `<object>` (contenido externo/plugins)

```html
<embed src="documento.pdf" type="application/pdf" width="600" height="400" />

<object data="documento.pdf" type="application/pdf" width="600" height="400">
  <p>No se pudo cargar el PDF. <a href="documento.pdf">Descárgalo aquí</a>.</p>
</object>
```

- `<object>` admite contenido de reemplazo (fallback) dentro de la etiqueta; `<embed>` no.
- Uso típico hoy: PDFs embebidos, SVG externo, recursos que no encajan como imagen/video/audio estándar.

---

## Tablas

Las tablas se usan **exclusivamente para datos tabulares**  
(no para layout o maquetación).

Buenas prácticas:

- Usa `<th>` para encabezados.
- Usa `<thead>`, `<tbody>` y `<tfoot>` para estructura.
- Evita tablas para diseño visual (usa CSS Grid/Flexbox).
- Añade títulos y descripciones cuando sea necesario.

---

## Estructura básica de una tabla

```html
<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Edad</th>
      <th>Ciudad</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>Ana</td>
      <td>30</td>
      <td>Bogotá</td>
    </tr>
    <tr>
      <td>Luis</td>
      <td>25</td>
      <td>Medellín</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td colspan="3">Total personas: 2</td>
    </tr>
  </tfoot>
</table>
```

---

## `<table>`

```html
<table>
  ...
</table>
```

- Contenedor principal de la tabla.
- Puede incluir `<caption>` como título descriptivo.

---

## `<caption>` (título de la tabla)

```html
<table>
  <caption>
    Listado de usuarios
  </caption>
</table>
```

- Mejora accesibilidad y comprensión.
- Se coloca **justo después de `<table>`**.

---

## `<thead>`

```html
<thead>
  <tr>
    <th>Producto</th>
    <th>Precio</th>
  </tr>
</thead>
```

- Agrupa encabezados.
- Normalmente contiene `<th>`.

---

## `<tr>` (fila)

```html
<tr>
  <td>Dato 1</td>
  <td>Dato 2</td>
</tr>
```

- Representa una fila.
- Se usa dentro de `thead`, `tbody` o `tfoot`.

---

## `<th>` (celda de encabezado)

```html
<th>Nombre</th>
```

- Define encabezados de columna o fila.
- Por defecto es texto en negrita y centrado.
- Atributo recomendado: `scope`.

### `scope`

```html
<th scope="col">Nombre</th>
<th scope="row">Ana</th>
```

Valores comunes:

- `col`: encabezado de columna.
- `row`: encabezado de fila.

---

## `<tbody>`

```html
<tbody>
  <tr>
    <td>Ana</td>
    <td>30</td>
  </tr>
</tbody>
```

- Contiene los datos principales.
- Permite separar lógica de encabezados y totales.

---

## `<td>` (celda de datos)

```html
<td>Colombia</td>
```

- Celda de datos normal.
- Va dentro de `<tr>`.

---

## `<tfoot>`

```html
<tfoot>
  <tr>
    <td colspan="2">Total</td>
    <td>$500</td>
  </tr>
</tfoot>
```

- Información resumen (totales, promedios).
- Puede colocarse antes o después del `<tbody>` en el HTML
  (el navegador lo renderiza al final).

---

## `colspan` (combinar columnas)

```html
<tr>
  <td colspan="3">Sin resultados</td>
</tr>
```

- Une varias columnas en una sola celda.

---

## `rowspan` (combinar filas)

```html
<tr>
  <td rowspan="2">Grupo A</td>
  <td>Elemento 1</td>
</tr>
<tr>
  <td>Elemento 2</td>
</tr>
```

---

## Tabla con encabezados de fila y columna

```html
<table>
  <thead>
    <tr>
      <th></th>
      <th scope="col">Lunes</th>
      <th scope="col">Martes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Horario</th>
      <td>8:00</td>
      <td>9:00</td>
    </tr>
  </tbody>
</table>
```

---

## Accesibilidad en tablas

- Usa `<caption>` para describir la tabla.
- Usa `<th>` con `scope`.
- No uses tablas para layout.
- Evita celdas vacías si no aportan significado.

---

## Ejemplo completo recomendado

```html
<table>
  <caption>
    Reporte de ventas
  </caption>

  <thead>
    <tr>
      <th scope="col">Producto</th>
      <th scope="col">Cantidad</th>
      <th scope="col">Precio</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>Mouse</td>
      <td>10</td>
      <td>$20</td>
    </tr>
    <tr>
      <td>Teclado</td>
      <td>5</td>
      <td>$50</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td colspan="2">Total</td>
      <td>$450</td>
    </tr>
  </tfoot>
</table>
```

---

## `<details>` y `<summary>` (contenido plegable)

```html
<details>
  <summary>¿Qué incluye el envío?</summary>
  <p>Incluye seguro, seguimiento y entrega en 3 días hábiles.</p>
</details>
```

- Widget nativo de mostrar/ocultar, sin necesidad de JavaScript.
- `<summary>` es la parte siempre visible (encabezado clicable).
- El atributo `open` lo muestra expandido por defecto:

```html
<details open>
  <summary>Detalles técnicos</summary>
  <p>Contenido visible desde el inicio.</p>
</details>
```

---

## `<dialog>` (cuadro de diálogo nativo)

```html
<dialog id="modal">
  <p>¿Confirmas la acción?</p>
  <button value="cancel" formmethod="dialog">Cancelar</button>
  <button value="confirm" formmethod="dialog">Confirmar</button>
</dialog>

<button onclick="modal.showModal()">Abrir diálogo</button>
```

- `showModal()` (JS): abre como modal, bloqueando la interacción con el resto de la página.
- `show()` (JS): abre sin bloquear el resto de la página.
- `close()` (JS): cierra el diálogo; también se cierra con `Esc` en modo modal.
- El atributo `open` refleja si el diálogo está visible.

---

## Accesibilidad (A11y) y ARIA

La accesibilidad busca que **todas las personas**, incluyendo usuarios con discapacidades, puedan usar la web.  
HTML semántico es la **primera y mejor capa** de accesibilidad.  
ARIA se usa **solo cuando HTML no es suficiente**.

---

## ¿Qué es ARIA?

ARIA (**Accessible Rich Internet Applications**) es un conjunto de atributos que:

- Añaden **significado semántico** a elementos no semánticos.
- Ayudan a lectores de pantalla a interpretar la interfaz.

> Regla de oro: **No uses ARIA si HTML ya resuelve el problema.**

---

## Atributos ARIA más usados

### `aria-label`

Proporciona una **etiqueta accesible** cuando no hay texto visible.

```html
<button aria-label="Cerrar modal">✕</button>
```

- Útil para iconos, botones solo visuales.
- No debe duplicar texto visible innecesariamente.

---

### `aria-labelledby`

Asocia un elemento a otro que ya contiene el texto descriptivo.

```html
<h2 id="titulo-form">Registro</h2>

<form aria-labelledby="titulo-form">...</form>
```

- Preferible a `aria-label` cuando ya existe texto visible.

---

### `aria-describedby`

Asocia **texto de ayuda o descripción adicional**.

```html
<label for="password">Contraseña</label>
<input id="password" type="password" aria-describedby="ayuda-pass" />

<p id="ayuda-pass">Debe tener al menos 8 caracteres.</p>
```

- Muy usado en formularios.
- Complementa, no reemplaza, el label.

---

## `role`

Define el **rol semántico** de un elemento cuando no existe etiqueta HTML adecuada.

```html
<div role="alert">Error al guardar los datos</div>
```

Roles comunes:

- `alert`
- `dialog`
- `button`
- `navigation`
- `main`
- `region`
- `tablist`, `tab`, `tabpanel`

> Si usas `<button>`, `<nav>`, `<main>`, **no necesitas `role`**.

---

## Ejemplos comunes de ARIA bien aplicado

### Botón no semántico (caso excepcional)

```html
<div role="button" tabindex="0" aria-label="Guardar cambios">Guardar</div>
```

> Mejor solución: usar `<button>` directamente.

---

### Navegación accesible

```html
<nav aria-label="Navegación principal">
  <a href="/">Inicio</a>
  <a href="/blog">Blog</a>
</nav>
```

---

### Regiones de contenido

```html
<section aria-labelledby="titulo-noticias">
  <h2 id="titulo-noticias">Noticias</h2>
  ...
</section>
```

---

### Mensajes dinámicos

```html
<div role="status" aria-live="polite">Guardando cambios...</div>
```

- `aria-live`: notifica cambios dinámicos.
- Valores comunes:
  - `polite`
  - `assertive`

---

## Buenas prácticas de accesibilidad (general)

- Usa **HTML semántico primero**.
- Siempre usa `<label>` en formularios.
- No abuses de ARIA.
- Usa `aria-describedby` para ayudas y errores.
- Evita `role` innecesarios.
- Asegura navegación con teclado (`Tab`, `Enter`, `Space`).

---

## Errores comunes

- Usar ARIA para "arreglar" mal HTML.
- Duplicar información visible con `aria-label`.
- Usar `div` + `role` en lugar de etiquetas semánticas.
- No asociar labels con inputs.

---

## Resumen rápido

- HTML semántico > ARIA.
- `aria-label`: texto accesible invisible.
- `aria-describedby`: ayuda y contexto adicional.
- `role`: solo cuando no hay alternativa HTML.
- Menos ARIA = mejor accesibilidad.

---

## `<script>` (JavaScript en HTML)

```html
<script src="/app.js" defer></script>
<script type="module" src="/main.js"></script>
<script>
  console.log("Script inline");
</script>
```

- `defer`: descarga en paralelo, ejecuta tras parsear el HTML, respetando el orden.
- `async`: descarga en paralelo, ejecuta apenas está lista (orden no garantizado).
- `type="module"`: habilita `import`/`export` de ES Modules; se difiere automáticamente (similar a `defer`).

---

## `<noscript>` (contenido alternativo sin JavaScript)

```html
<noscript>
  <p>Esta página requiere JavaScript para funcionar correctamente.</p>
</noscript>
```

- Se renderiza solo si el navegador tiene JavaScript deshabilitado o no lo soporta.

---

## `<template>` (marcado reutilizable no renderizado)

```html
<template id="fila-usuario">
  <tr>
    <td class="nombre"></td>
    <td class="correo"></td>
  </tr>
</template>
```

- El contenido no se renderiza ni se ejecuta hasta ser clonado con JavaScript (`content.cloneNode(true)`).
- Útil como plantilla de componentes o filas repetibles.

---

## `<canvas>` (gráficos vía JavaScript)

```html
<canvas id="grafico" width="400" height="200">
  Tu navegador no soporta canvas.
</canvas>
```

- Área en blanco donde se dibuja con la Canvas API o WebGL desde JavaScript.
- El contenido interno del elemento es el fallback si `<canvas>` no es soportado.

---

## SEO y metadatos del documento HTML

Los metadatos permiten a navegadores, buscadores y redes sociales **entender y presentar correctamente** tu página.  
Se definen principalmente dentro de `<head>`.

---

## Idioma del documento (`lang`)

```html
<html lang="es"></html>
```

- Indica el idioma principal del contenido.
- Mejora accesibilidad y SEO.
- Ejemplos: `es`, `en`, `es-CO`.

---

## Codificación de caracteres (`UTF-8`)

```html
<meta charset="UTF-8" />
```

- Permite usar caracteres especiales (ñ, tildes, símbolos).
- Debe ir **al inicio del `<head>`**.

---

## Viewport (responsive)

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

- Controla el renderizado en móviles.
- Obligatorio para diseño responsive.

---

## `<title>` (título del documento)

```html
<title>Curso de HTML | Guía básica</title>
```

- Aparece en la pestaña del navegador.
- Es uno de los factores SEO más importantes.
- Recomendado: 50–60 caracteres.

---

## Meta description

```html
<meta
  name="description"
  content="Guía básica de HTML con buenas prácticas, semántica y accesibilidad."
/>
```

- Resumen de la página para buscadores.
- No afecta ranking directo, pero sí el CTR.
- Recomendado: 150–160 caracteres.

---

## Otras meta etiquetas comunes

### Autor

```html
<meta name="author" content="Tu Nombre" />
```

### Palabras clave (obsoleto para SEO moderno)

```html
<meta name="keywords" content="html, frontend, web" />
```

> Hoy en día Google **no usa** `keywords` para ranking.

---

## Open Graph (redes sociales)

Permite controlar cómo se ve la página al compartirla.

```html
<meta property="og:title" content="Guía de HTML" />
<meta
  property="og:description"
  content="Aprende HTML desde cero con buenas prácticas."
/>
<meta property="og:type" content="website" />
<meta property="og:url" content="https://example.com/html" />
<meta property="og:image" content="https://example.com/preview.jpg" />
```

Campos más usados:

- `og:title`
- `og:description`
- `og:image`
- `og:url`
- `og:type`

---

## Favicon

Icono que aparece en la pestaña del navegador.

```html
<link rel="icon" href="/favicon.ico" />
```

Formatos comunes:

- `.ico`
- `.png`
- `.svg`

Ejemplo moderno:

```html
<link rel="icon" type="image/svg+xml" href="/favicon.svg" />
```

---

## `<base>` (URL base del documento)

```html
<base href="https://example.com/" target="_blank" />
```

- Define la URL base para todas las rutas relativas del documento (`href`, `src`).
- Debe ser **único** y ubicarse entre los primeros elementos del `<head>`.
- El atributo `target` opcional define el destino por defecto de los enlaces del documento.

---

## `<body>` (contenido visible)

```html
<body>
  <h1>Bienvenido</h1>
  <p>Contenido principal del sitio.</p>
</body>
```

- Contiene todo lo visible.
- No debe incluir metadatos SEO (van en `<head>`).

---

## Estructura SEO recomendada (completa)

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <title>Guía de HTML | Frontend</title>
    <meta
      name="description"
      content="Guía completa de HTML con semántica, accesibilidad y buenas prácticas."
    />

    <meta property="og:title" content="Guía de HTML" />
    <meta property="og:description" content="Aprende HTML desde cero." />
    <meta property="og:type" content="website" />
    <meta property="og:image" content="https://example.com/preview.jpg" />
    <meta property="og:url" content="https://example.com/html" />

    <link rel="icon" href="/favicon.ico" />
  </head>

  <body>
    <h1>HTML desde cero</h1>
    <p>Contenido del sitio.</p>
  </body>
</html>
```

---

## Buenas prácticas SEO

- Un solo `<h1>` por página.
- `<title>` único por vista.
- `description` clara y concisa.
- Usa HTML semántico.
- Optimiza imágenes y contenido.
- Usa Open Graph si se comparte en redes.

---
