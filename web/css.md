## Guía Rápida de CSS

Referencia breve de sintaxis y comportamiento propio de CSS: cascada, selectores, layout, tipografía, colores y características modernas del lenguaje.

> Versión: CSS actual (Snapshot) · Actualizado: 2026-07-10

## Tabla de contenidos

- [Formas de aplicar CSS](#formas-de-aplicar-css)
- [Selectores](#selectores)
- [Selectores lógicos modernos](#selectores-lógicos-modernos)
- [Cascada, especificidad y herencia](#cascada-especificidad-y-herencia)
- [Box Model](#box-model)
- [`box-sizing` y reset](#box-sizing-y-reset)
- [Position](#position)
- [Apilamiento (`z-index`)](#apilamiento-z-index)
- [Propiedades lógicas](#propiedades-lógicas)
- [Unidades de medida](#unidades-de-medida)
- [Funciones de tamaño (`clamp`, `min`, `max`)](#funciones-de-tamaño-clamp-min-max)
- [Colores](#colores)
- [Variables CSS (Custom Properties)](#variables-css-custom-properties)
- [Tipografía](#tipografía)
- [Control del texto](#control-del-texto)
- [Degradados](#degradados)
- [Sombras y bordes](#sombras-y-bordes)
- [Filtros y efectos visuales](#filtros-y-efectos-visuales)
- [Flexbox](#flexbox)
- [CSS Grid](#css-grid)
- [Subgrid](#subgrid)
- [`aspect-ratio` y `object-fit`](#aspect-ratio-y-object-fit)
- [Media queries y diseño responsive](#media-queries-y-diseño-responsive)
- [Container queries](#container-queries)
- [Cascade layers (`@layer`)](#cascade-layers-layer)
- [`@supports`](#supports)
- [CSS Nesting](#css-nesting)
- [Transformaciones, transiciones y animaciones](#transformaciones-transiciones-y-animaciones)
- [Preferencias del usuario](#preferencias-del-usuario)
- [BEM (metodología de nombrado)](#bem-metodología-de-nombrado)

---

## Formas de aplicar CSS

- **En línea** (mayor prioridad, evitar)

```html
<p style="color: red;">Texto rojo</p>
```

- **Interno**, dentro de `<head>`

```html
<style>
  p { color: red; }
</style>
```

- **Externo** (recomendado, cacheable y reutilizable)

```html
<link rel="stylesheet" href="styles.css" />
```

---

## Selectores

- **Tipo**

```css
p { color: black; } /* todas las <p> */
```

- **Clase**

```css
.card { border: 1px solid #ccc; }
```

- **ID**

```css
#header { background-color: #222; } /* único por documento, alta especificidad */
```

- **Universal**

```css
* { box-sizing: border-box; }
```

- **Atributo**

```css
input[type="email"] { border-color: blue; }
a[href^="https"] { color: green; } /* empieza con */
a[href$=".pdf"] { color: red; }    /* termina con */
```

- **Descendiente / hijo directo / hermanos**

```css
article p { color: gray; }   /* cualquier nivel dentro de article */
ul > li { list-style: none; } /* solo hijos directos */
h2 + p { margin-top: 0; }     /* hermano inmediato siguiente */
h2 ~ p { color: gray; }       /* todos los hermanos siguientes */
```

- **Pseudoclases** (estados)

```css
a:hover { color: red; }
input:focus { outline: 2px solid blue; }
li:first-child { font-weight: bold; }
li:nth-child(2n) { background: #f5f5f5; } /* pares */
```

- **Pseudoelementos** (partes internas)

```css
p::first-letter { font-size: 2rem; }
.tooltip::before { content: "→ "; }
::selection { background: yellow; }
```

---

## Selectores lógicos modernos

- **`:is()`** — agrupa selectores, toma la especificidad del más alto

```css
:is(header, main, footer) p { line-height: 1.6; }
```

- **`:where()`** — igual que `:is()` pero con especificidad `0`

```css
:where(header, main, footer) p { line-height: 1.6; }
```

- **`:has()`** — selector padre condicionado a su contenido

```css
card:has(img) { padding-top: 0; }         /* .card que contiene una imagen */
form:has(:invalid) { border-color: red; } /* formulario con campo inválido */
```

- **`:not()`**

```css
li:not(:last-child) { border-bottom: 1px solid #eee; }
```

---

## Cascada, especificidad y herencia

El orden en que se resuelve un conflicto entre reglas: origen y `!important` → especificidad → orden de aparición.

```css
p          { color: blue; }  /* especificidad (0,0,1) */
.texto     { color: red; }   /* especificidad (0,1,0) */
#principal { color: green; } /* especificidad (1,0,0) */
```

```html
<p id="principal" class="texto">Texto</p>
<!-- resultado: verde, gana el ID -->
```

- **`!important`** sobrescribe la especificidad normal (usar solo como último recurso)

```css
p { color: red !important; }
```

- **Herencia**: `color`, `font-family`, `font-size` y `line-height` pasan del padre al hijo automáticamente

```css
body { color: #333; }
button { color: inherit; } /* fuerza herencia en elementos que no heredan por defecto */
```

---

## Box Model

Todo elemento es una caja compuesta, de adentro hacia afuera, por `content`, `padding`, `border` y `margin`.

```css
.box {
  width: 200px;
  height: 100px;
  padding: 16px;             /* espacio interno, el fondo sí lo cubre */
  border: 2px solid black;   /* suma al tamaño total */
  margin: 20px;               /* espacio externo, sin fondo, puede colapsar */
}
```

- **Notación abreviada** (top, right, bottom, left en sentido horario)

```css
padding: 10px;                 /* todos los lados */
padding: 10px 20px;            /* vertical | horizontal */
padding: 5px 10px 15px 20px;   /* top | right | bottom | left */
```

---

## `box-sizing` y reset

```css
.box { box-sizing: content-box; } /* width/height solo miden el content (por defecto) */
.box { box-sizing: border-box; }  /* width/height incluyen padding + border */
```

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}

body {
  margin: 0;
}
```

---

## Position

```css
.a { position: static; }   /* por defecto, ignora top/right/bottom/left */

.b {
  position: relative;      /* se mueve desde su posición original, mantiene su espacio */
  top: 10px;
  left: 20px;
}

.c {
  position: absolute;      /* fuera del flujo, respecto al ancestro posicionado más cercano */
  top: 0;
  right: 0;
}

.d {
  position: fixed;         /* respecto al viewport, ignora el scroll */
  top: 0;
  width: 100%;
}

.e {
  position: sticky;        /* relative hasta cruzar el umbral, luego fixed */
  top: 0;
}
```

> `absolute` se posiciona respecto al ancestro más cercano con `position` distinto de `static`. Un padre con `position: relative` sin desplazamiento crea ese contexto sin salir del flujo.

---

## Apilamiento (`z-index`)

Solo funciona en elementos posicionados (`position` distinto de `static`).

```css
.modal {
  position: fixed;
  z-index: 1000;
}
```

- **Contexto de apilamiento**: se crea con `position` + `z-index`, `opacity < 1`, `transform`, `filter` o `will-change`. Un `z-index` alto en un hijo no puede escapar del contexto de su padre.

---

## Propiedades lógicas

Se adaptan a la dirección de escritura del documento (`ltr`/`rtl`) en vez de asumir izquierda/derecha fijas.

```css
.box {
  margin-inline: 1rem;   /* margin-left + margin-right en ltr */
  margin-block: 2rem;    /* margin-top + margin-bottom */
  padding-inline-start: 1rem;
  border-block-end: 1px solid #ccc;
  inline-size: 300px;    /* equivalente lógico de width */
  block-size: 100px;     /* equivalente lógico de height */
}
```

---

## Unidades de medida

- **Absolutas**

```css
.box { border-width: 1px; } /* px: fija, no escala con preferencias del usuario */
```

- **Relativas al contenedor**

```css
.container { width: 80%; } /* % del padre */
```

- **Relativas a tipografía**

```css
html { font-size: 16px; }
.card { font-size: 16px; }
.card__title { font-size: 1.5em; }  /* relativo al padre: 24px, se acumula */
p { font-size: 1rem; }              /* relativo al root (html): 16px, no se acumula */
```

- **Relativas al viewport**

```css
.hero { width: 100vw; min-height: 100vh; }  /* 1vw = 1% ancho, 1vh = 1% alto */
.title { font-size: 4svh; }                  /* svh/lvh/dvh: variantes estables en móvil */
```

- **Relativa al carácter**

```css
.column { max-width: 60ch; } /* ancho basado en el carácter "0" de la fuente */
```

---

## Funciones de tamaño (`clamp`, `min`, `max`)

```css
h1 {
  font-size: clamp(1.5rem, 5vw, 3rem); /* mínimo, preferido, máximo: sin media queries */
}

.container {
  width: min(90%, 1200px); /* el menor de los dos */
  padding: max(1rem, 3vw); /* el mayor de los dos */
}
```

---

## Colores

```css
p { color: green; }                    /* nombre predefinido */
.box { background-color: #ff0000; }    /* hex, #fff forma corta */
.text { color: rgb(255 0 0); }         /* canales 0-255 */
.overlay { background-color: rgb(0 0 0 / 50%); } /* con alpha */
.button { background-color: hsl(220 80% 50%); }  /* tono, saturación, luminosidad */
.modern { color: oklch(65% 0.2 250); }           /* perceptualmente uniforme */
```

- **`currentColor`**

```css
.icon { color: blue; }
.icon svg { fill: currentColor; } /* hereda el valor de color */
```

- **`color-mix()`**

```css
.hover { background: color-mix(in srgb, blue 70%, white); }
```

---

## Variables CSS (Custom Properties)

Se declaran con `--` y se leen con `var()`. Siguen el alcance del DOM: se pueden sobrescribir por contexto.

```css
:root {
  --color-primary: hsl(220 80% 50%);
  --spacing: 1rem;
}

.button {
  background-color: var(--color-primary);
  padding: var(--spacing);
}

.card {
  color: var(--text-color, #333); /* valor de respaldo si la variable no existe */
}

.dark-theme {
  --color-primary: orange; /* sobrescribe solo dentro de este contenedor */
}
```

---

## Tipografía

```css
body {
  font-family: system-ui, -apple-system, "Segoe UI", Roboto, Arial, sans-serif;
  font-size: 1rem;
  font-weight: 600;   /* 400 normal, 700 bold */
  line-height: 1.6;   /* sin unidad: mejor legibilidad, no se acumula */
  font-style: italic;
  letter-spacing: 0.05em;
}
```

- **Atajo `font`**

```css
h1 { font: italic 700 2rem/1.2 "Inter", sans-serif; } /* style weight size/line-height family */
```

- **`@font-face`**: carga tipografías propias

```css
@font-face {
  font-family: "Inter";
  src: url("/fonts/inter.woff2") format("woff2");
  font-weight: 400 700;
  font-display: swap; /* muestra fallback mientras carga */
}
```

---

## Control del texto

```css
p { text-align: justify; }          /* left, right, center, justify */
h2 { text-transform: capitalize; }  /* uppercase, lowercase, capitalize */
a  { text-decoration: underline solid red; }
p  { text-indent: 2rem; }
pre { white-space: pre-wrap; }      /* normal, nowrap, pre, pre-wrap */

.title {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis; /* corta con "…" */
}
```

---

## Degradados

```css
.a { background: linear-gradient(red, blue); }                 /* arriba hacia abajo */
.b { background: linear-gradient(to right, red, blue); }
.c { background: linear-gradient(45deg, red, yellow, blue); }  /* con ángulo y varios colores */
.d { background: radial-gradient(circle at top left, red, blue); }
.e { background: conic-gradient(red, yellow, green, blue, red); } /* alrededor de un punto */
```

---

## Sombras y bordes

```css
.card {
  box-shadow: 0 4px 10px rgb(0 0 0 / 15%);              /* offset-x offset-y blur color */
  box-shadow: inset 0 2px 4px rgb(0 0 0 / 20%);         /* hacia dentro */
  box-shadow: 0 2px 4px rgb(0 0 0 / 10%), 0 8px 16px rgb(0 0 0 / 8%); /* apiladas */
}

h1 { text-shadow: 2px 2px 4px rgb(0 0 0 / 40%); }

.avatar { border-radius: 50%; }                 /* círculo si width = height */
.box { border-radius: 8px 16px 4px 16px; }      /* top-left top-right bottom-right bottom-left */
```

---

## Filtros y efectos visuales

```css
.img { filter: blur(4px) brightness(0.9) grayscale(50%); }
.modal-bg { backdrop-filter: blur(8px); } /* difumina lo que hay detrás */
.shape { clip-path: circle(50% at center); } /* recorta la caja a una forma */
```

---

## Flexbox

Layout de una dimensión, ideal para componentes y alineación.

```css
.container {
  display: flex;
  flex-direction: row;          /* row, row-reverse, column, column-reverse */
  justify-content: space-between; /* eje principal */
  align-items: center;            /* eje secundario */
  flex-wrap: wrap;
  gap: 16px;                      /* espacio entre items */
}

.item {
  flex: 1;          /* flex-grow: 1; flex-shrink: 1; flex-basis: 0 */
}

.item-special {
  align-self: flex-end; /* sobrescribe align-items solo para este item */
}
```

---

## CSS Grid

Layout bidimensional, ideal para estructuras de página completas.

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* tres columnas iguales */
  grid-template-rows: auto 1fr auto;
  gap: 24px;
}

.item {
  grid-column: 1 / 3; /* desde línea 1 hasta línea 3 */
  grid-row: span 2;   /* ocupa 2 filas */
}

.layout {
  grid-template-columns: 200px 1fr;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
}
.header  { grid-area: header; }
.sidebar { grid-area: sidebar; }
```

- **Grid automático responsive** (sin media queries)

```css
.cards {
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
}
```

---

## Subgrid

Un grid hijo hereda las pistas de su ancestro en vez de definir las suyas propias.

```css
.parent { display: grid; grid-template-columns: repeat(4, 1fr); }
.child {
  display: grid;
  grid-column: span 4;
  grid-template-columns: subgrid; /* alinea sus columnas con las del padre */
}
```

---

## `aspect-ratio` y `object-fit`

```css
.video { aspect-ratio: 16 / 9; } /* mantiene proporción sin calcular height */

img {
  width: 100%;
  height: 200px;
  object-fit: cover; /* cover, contain, fill: cómo se ajusta dentro de la caja */
}
```

---

## Media queries y diseño responsive

Enfoque mobile-first: estilos base para pantallas pequeñas, se amplían con `min-width`.

```css
.container { padding: 1rem; }

@media (min-width: 768px) {
  .container { padding: 2rem; }
}

@media (prefers-color-scheme: dark) {
  body { background: #111; color: #eee; }
}
```

```css
img { max-width: 100%; height: auto; } /* imágenes fluidas */
```

---

## Container queries

Los estilos responden al tamaño del **contenedor**, no del viewport.

```css
.card-container {
  container-type: inline-size;
  container-name: card;
}

@container card (min-width: 400px) {
  .card { flex-direction: row; }
}
```

---

## Cascade layers (`@layer`)

Agrupan reglas en capas con prioridad explícita, independiente del orden de especificidad dentro de cada capa.

```css
@layer reset, base, components, utilities;

@layer reset {
  * { margin: 0; padding: 0; }
}

@layer components {
  .button { padding: 0.5rem 1rem; }
}
/* utilities siempre gana sobre components, sin importar especificidad */
```

---

## `@supports`

Aplica estilos solo si el navegador soporta una característica.

```css
@supports (display: grid) {
  .container { display: grid; }
}

@supports not (aspect-ratio: 1) {
  .square { padding-bottom: 100%; } /* fallback */
}
```

---

## CSS Nesting

Anidamiento nativo de selectores, sin preprocesador.

```css
.card {
  padding: 1rem;

  & .card__title {
    font-size: 1.2rem;
  }

  &:hover {
    box-shadow: 0 4px 10px rgb(0 0 0 / 15%);
  }

  @media (min-width: 768px) {
    padding: 2rem;
  }
}
```

---

## Transformaciones, transiciones y animaciones

```css
.box { transform: translate(20px, 10px) rotate(45deg) scale(1.2); } /* el orden importa */

.button {
  background-color: blue;
  transition: background-color 0.3s ease; /* property duration timing-function delay */
}
.button:hover { background-color: darkblue; }

@keyframes fadeIn {
  from { opacity: 0; }
  to   { opacity: 1; }
}

.box {
  animation: fadeIn 1s ease forwards; /* name duration timing-function ... */
}

.box:hover { animation-play-state: paused; }
```

---

## Preferencias del usuario

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}
```

---

## BEM (metodología de nombrado)

Convención de nombres de clases: **Block__Element--Modifier**, evita anidar selectores y colisiones de estilos.

```css
.card { }                    /* block: componente independiente */
.card__title { }              /* element: parte interna, depende del block */
.card--featured { }           /* modifier: variación del block */
.card__button--primary { }    /* modifier de un element */
```

```html
<article class="card card--featured">
  <h3 class="card__title">Título</h3>
  <button class="card__button card__button--primary">Leer más</button>
</article>
```
