# Guía Rápida de CSS

CSS (**Cascading Style Sheets**) es el lenguaje encargado de definir la **apariencia visual** de un documento HTML.  
Controla colores, tamaños, tipografías, espacios, layout y comportamiento responsive.

HTML define la **estructura**.  
CSS define **cómo se ve**.

---

## Tabla de contenidos

- [¿Qué significa "Cascading"?](#qué-significa-cascading)
- [Formas de aplicar CSS](#formas-de-aplicar-css)
- [Selectores en CSS](#selectores-en-css)
- [Especificidad](#especificidad-orden-de-importancia)
- [Box Model](#box-model-modelo-de-caja)
- [Position](#position-posicionamiento-en-css)
- [BEM](#organización-css-con-bem)
- [Unidades](#unidades-de-medida-en-css)
- [Tipografía](#tipografía-en-css-fuentes)
- [Texto](#control-del-texto-en-css)
- [Colores](#sistema-de-colores-en-css)
- [Variables CSS](#variables-css-custom-properties)
- [Degradados](#degradados-en-css)
- [Sombras y bordes](#sombras-y-bordes-en-css)
- [Flexbox](#flexbox-flexible-box-layout)
- [CSS Grid](#css-grid-grid-layout)
- [Responsive](#media-queries-y-diseño-responsive)
- [Transformaciones y animaciones](#transformaciones-transiciones-y-animaciones-en-css)

---

## ¿Qué significa "Cascading"?

"Cascading" (en cascada) significa que los estilos:

- Se aplican siguiendo **prioridades**.
- Pueden **sobrescribirse** entre sí.
- Se resuelven según reglas de **origen, especificidad y orden**.

Regla práctica para entender quién gana (cuando hay conflicto):

1. Gana el estilo con `!important` (último recurso).
2. Si no hay `!important`, gana el selector con mayor **especificidad**.
3. Si hay empate, gana la regla que aparece **más abajo** (orden en el CSS).

> El CSS en línea (`style="..."`) suele tener alta prioridad, pero se recomienda evitarlo por mantenibilidad.

---

## Formas de aplicar CSS

### 1. CSS en línea (inline)

Se escribe directamente dentro de la etiqueta HTML.

```html
<p style="color: red;">Texto rojo</p>
```

- ❌ No recomendado.
- Difícil de mantener.
- Rompe la separación entre estructura y estilos.
- Alta prioridad (sobrescribe otros estilos).

---

### 2. CSS interno (en el `<head>`)

Se define dentro de la etiqueta `<style>`.

```html
<head>
  <style>
    p {
      color: red;
    }
  </style>
</head>
```

- Útil para pruebas rápidas.
- Aplica solo a ese documento.
- ❌ No escalable para proyectos grandes.

---

### 3. CSS externo (recomendado)

Se escribe en un archivo separado `.css`.

#### HTML

```html
<link rel="stylesheet" href="styles.css" />
```

#### CSS (`styles.css`)

```css
p {
  color: red;
}
```

- ✔️ Mejor práctica.
- Reutilizable.
- Mantenible.
- Permite hojas de estilo grandes y organizadas.

---

## Hoja de estilos (stylesheet)

Una **hoja de estilos** es un archivo CSS que contiene todas las reglas visuales del sitio.

Ejemplo de estructura básica:

```css
/* styles.css */

/* Estilos base */
body {
  font-family: Arial, sans-serif;
  color: #333;
}

/* Componentes */
.button {
  background-color: blue;
  color: white;
}
```

---

## Recomendación general

- Usa **CSS externo** siempre que sea posible.
- Evita CSS en línea.
- Mantén CSS separado del HTML.
- Piensa en CSS como una capa independiente de presentación.

---

## Selectores en CSS

Los selectores indican **a qué elementos HTML se les aplican los estilos**.  
Elegir bien el selector es clave para un CSS limpio, mantenible y predecible.

---

## Selector de tipo (etiqueta)

```css
p {
  color: black;
}
```

- Aplica a **todas** las etiquetas del mismo tipo.
- Útil para estilos globales.
- ❌ No recomendado para estilos específicos.

**Cuándo usarlo**

- Reset
- Tipografía base
- Estilos generales

---

## Selector de clase (`.`)

```css
.card {
  border: 1px solid #ccc;
}
```

```html
<div class="card"></div>
```

- Reutilizable.
- Flexible.
- ✔️ **Selector recomendado por defecto**.

### Cuándo usar clases

- Componentes reutilizables.
- Estados visuales.
- Layout y diseño.
- Cuando un estilo se repite.

---

## Selector de ID (`#`)

```css
#header {
  background-color: #222;
}
```

```html
<header id="header"></header>
```

- Identificador único.
- Alta especificidad.
- ❌ Evitar para estilos.

### Cuándo usar IDs

✔️ JavaScript  
✔️ Anclas (`#seccion`)  
❌ CSS (en la mayoría de casos)

---

## Selectores dependientes (padre → hijo)

### Descendiente

```css
article p {
  color: gray;
}
```

- Aplica a `<p>` dentro de `<article>` (no importa el nivel).

---

### Hijo directo (`>`)

```css
ul > li {
  list-style: none;
}
```

- Solo hijos directos.

---

### Hermanos adyacentes (`+`)

```css
h2 + p {
  margin-top: 0;
}
```

- Primer hermano inmediato.

---

### Hermanos generales (`~`)

```css
h2 ~ p {
  color: gray;
}
```

---

## Especificidad (orden de importancia)

La especificidad define **qué regla gana** cuando hay conflicto.

### Cómo se calcula (de menor a mayor)

Se suele expresar como **(IDs, clases, tipos)**:

- `*` no aporta especificidad.
- Selector de tipo (`p`) y pseudoelemento (`::before`) suman en **tipos**.
- Clase (`.card`), atributo (`[type="text"]`) y pseudoclase (`:hover`) suman en **clases**.
- ID (`#header`) suma en **IDs**.

> Si la especificidad empata, gana la regla declarada más abajo (orden del CSS).  
> `!important` no es especificidad: cambia la prioridad en la cascada.

---

### Ejemplo

```css
p {
  color: blue;
}

.texto {
  color: red;
}

#principal {
  color: green;
}
```

```html
<p id="principal" class="texto">Texto</p>
```

✔️ Resultado: **verde**

---

## `!important`

```css
p {
  color: red !important;
}
```

- Sobrescribe todo.
- ❌ Mala práctica en la mayoría de casos.

**Úsalo solo cuando:**

- Corriges librerías externas.
- No puedes modificar el CSS original.

---

## Herencia de estilos

Algunas propiedades se heredan automáticamente del padre al hijo.

### Propiedades que heredan

- `color`
- `font-family`
- `font-size`
- `line-height`

```css
body {
  color: #333;
}
```

```html
<p>Este texto hereda el color</p>
```

---

### Forzar herencia

```css
button {
  color: inherit;
}
```

---

## Pseudoclases

Representan **estados** de un elemento.

```css
a:hover {
  color: red;
}
```

Pseudoclases comunes:

- `:hover`
- `:active`
- `:focus`
- `:visited`
- `:checked`
- `:disabled`
- `:first-child`
- `:last-child`
- `:nth-child(n)`

---

### Ejemplo

```css
input:focus {
  outline: 2px solid blue;
}
```

---

## Pseudoelementos

Representan **partes internas** de un elemento.

```css
p::first-letter {
  font-size: 2rem;
}
```

Pseudoelementos comunes:

- `::before`
- `::after`
- `::first-letter`
- `::first-line`
- `::selection`

---

### Ejemplo con `::before`

```css
.button::before {
  content: "👉 ";
}
```

---

## Reglas prácticas recomendadas

- Usa **clases** como selector principal.
- Evita IDs para estilos.
- Evita `!important`.
- Mantén selectores poco profundos.
- Aprovecha herencia.
- Usa pseudoclases para estados.
- Usa pseudoelementos para decoración.

---

## Box Model (Modelo de caja)

El **Box Model** define cómo el navegador calcula el **tamaño y espacio** que ocupa cada elemento HTML en la página.

Todo elemento en CSS es una **caja rectangular** compuesta por varias capas.

---

## Estructura del Box Model

```text
+---------------------------+
|        margin             |
|  +---------------------+  |
|  |      border         |  |
|  |  +---------------+  |  |
|  |  |   padding     |  |  |
|  |  | +-----------+ |  |  |
|  |  | |  content  | |  |  |
|  |  | +-----------+ |  |  |
|  |  +---------------+  |  |
|  +---------------------+  |
+---------------------------+
```

Orden (de adentro hacia afuera):

1. **Content**
2. **Padding**
3. **Border**
4. **Margin**

---

## `content`

Es el **contenido real** del elemento.

```css
.box {
  width: 200px;
  height: 100px;
}
```

- Contiene texto, imágenes u otros elementos.
- `width` y `height` aplican **solo al content** (por defecto).

---

## `padding`

Espacio interno entre el contenido y el borde.

```css
.box {
  padding: 16px;
}
```

- Aumenta el tamaño visual del elemento.
- El fondo (`background`) **sí cubre el padding**.

```css
padding: 10px; /* todos los lados */
padding: 10px 20px; /* vertical | horizontal */
padding: 5px 10px 15px; /* top | horizontal | bottom */
padding: 5px 10px 15px 20px; /* top | right | bottom | left */
```

---

## `border`

Borde que rodea el padding y el contenido.

```css
.box {
  border: 2px solid black;
}
```

- Suma al tamaño total del elemento.
- Forma parte del cálculo del layout.

---

## `margin`

Espacio **externo** entre un elemento y los demás.

```css
.box {
  margin: 20px;
}
```

- No tiene fondo.
- Se usa para separar elementos.
- Los márgenes verticales pueden **colapsar**.

---

## Tamaño total del elemento (por defecto)

```css
.box {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
}
```

Tamaño real:

- Ancho total = 200 + 20×2 + 5×2 = **250px**

Esto suele ser **confuso y poco intuitivo**.

---

## `box-sizing`

Controla cómo se calcula el tamaño del elemento.

---

### `content-box` (por defecto)

```css
.box {
  box-sizing: content-box;
}
```

- `width` y `height` solo afectan al contenido.
- Padding y border **se suman**.
- ❌ Difícil de mantener layouts.

---

### `border-box` (recomendado)

```css
.box {
  box-sizing: border-box;
}
```

- `width` y `height` incluyen:
  - content
  - padding
  - border
- ✔️ Tamaños predecibles.
- ✔️ Layouts más simples.

---

## Ejemplo comparativo

```css
.box {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  box-sizing: border-box;
}
```

✔️ Tamaño final: **200px exactos**

---

## Resetear estilos por defecto del navegador

Los navegadores aplican estilos propios (márgenes, tamaños, fuentes).

### Reset básico recomendado

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

- Elimina márgenes y paddings por defecto.
- Establece `border-box` globalmente.

---

## Reset moderno recomendado (base)

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

- Incluye pseudoelementos.
- Más seguro y estándar.

---

## Ejemplo completo con Box Model

```css
.card {
  width: 300px;
  padding: 16px;
  border: 1px solid #ccc;
  margin: 20px;
  box-sizing: border-box;
}
```

```html
<div class="card">Contenido de la tarjeta</div>
```

---

## Buenas prácticas (Box Model)

- Usa `box-sizing: border-box` globalmente.
- Controla espacios con `margin` y `padding`.
- Evita calcular tamaños "a mano".
- Piensa en el box model antes de diseñar layouts.

---

## Position (posicionamiento en CSS)

La propiedad `position` controla **cómo se ubica un elemento en la página** y cómo se relaciona con los demás elementos y el viewport.

Valores principales:

- `static`
- `relative`
- `absolute`
- `fixed`
- `sticky`

---

## `position: static` (por defecto)

```css
.element {
  position: static;
}
```

- Valor por defecto de todos los elementos.
- Sigue el flujo normal del documento.
- **No responde** a `top`, `right`, `bottom`, `left`.

---

## `position: relative`

```css
.box {
  position: relative;
  top: 10px;
  left: 20px;
}
```

- Se mueve **respecto a su posición original**.
- **Sigue ocupando su espacio** en el layout.
- Muy usado como **referencia** para hijos `absolute`.

### Uso típico

```css
.container {
  position: relative;
}
```

✔️ No rompe el flujo  
✔️ Crea contexto para `absolute`

---

## `position: absolute`

```css
.badge {
  position: absolute;
  top: 0;
  right: 0;
}
```

- Sale del flujo normal.
- Se posiciona respecto al **ancestro posicionado más cercano**
  (`relative`, `absolute`, `fixed`, `sticky`).
- Si no hay ancestro → usa el viewport.

### Ejemplo correcto (padre + hijo)

```css
.card {
  position: relative;
}

.card .badge {
  position: absolute;
  top: 8px;
  right: 8px;
}
```

```html
<div class="card">
  <span class="badge">Nuevo</span>
</div>
```

---

## `position: fixed`

```css
.header {
  position: fixed;
  top: 0;
  width: 100%;
}
```

- Se posiciona respecto al **viewport**.
- No se mueve al hacer scroll.
- Sale del flujo normal.

### Usos comunes

- Navbar fija
- Botones flotantes
- WhatsApp / acciones rápidas

---

## `position: sticky`

```css
.section-title {
  position: sticky;
  top: 0;
}
```

- Mezcla de `relative` + `fixed`.
- Se comporta como `relative` hasta llegar a un límite.
- Luego se "pega" como `fixed`.

### Requisitos importantes

- Debe tener un valor `top`, `left`, etc.
- Funciona **dentro de su contenedor**.
- El contenedor no debe tener `overflow: hidden`.

---

## Propiedades de desplazamiento

Funcionan con `relative`, `absolute`, `fixed`, `sticky`.

```css
.element {
  top: 10px;
  right: 20px;
  bottom: auto;
  left: auto;
}
```

---

## `z-index` (orden de apilamiento)

Controla **qué elemento se muestra encima de otro**.

```css
.modal {
  position: fixed;
  z-index: 1000;
}
```

Reglas clave:

- Solo funciona en elementos **posicionados**.
- Valores más altos se superponen.
- No es global: depende del **contexto de apilamiento**.

---

### Contexto de apilamiento

Se crea cuando un elemento tiene:

- `position` + `z-index`
- `opacity < 1`
- `transform`
- `filter`
- `will-change`

Ejemplo problemático:

```css
.parent {
  position: relative;
  z-index: 1;
}

.child {
  position: absolute;
  z-index: 9999;
}
```

👉 El hijo **no puede salir** del contexto del padre.

---

## Comparación rápida

| Position | Sale del flujo | Referencia            |
| -------- | -------------- | --------------------- |
| static   | ❌             | flujo normal          |
| relative | ❌             | posición original     |
| absolute | ✔️             | ancestro posicionado  |
| fixed    | ✔️             | viewport              |
| sticky   | ❌ / ✔️        | contenedor + viewport |

---

## Buenas prácticas (Position y z-index)

- Usa `relative` para crear contexto.
- Usa `absolute` para overlays internos.
- Usa `fixed` con moderación.
- Prefiere `sticky` para headers de sección.
- Evita valores gigantes de `z-index` sin criterio.
- Documenta rangos de `z-index` en proyectos grandes.

---

## Ejemplo completo recomendado

```css
.header {
  position: sticky;
  top: 0;
  z-index: 100;
}

.card {
  position: relative;
}

.card .icon {
  position: absolute;
  top: 8px;
  right: 8px;
}
```

---

## Organización CSS con BEM

BEM (**Block · Element · Modifier**) es una metodología para **nombrar clases CSS** de forma clara, escalable y mantenible.

Su objetivo es:

- Evitar colisiones de estilos.
- Reducir dependencia de selectores anidados.
- Hacer el CSS predecible y fácil de leer.

---

## Conceptos básicos de BEM

### Block (Bloque)

Es una **entidad independiente** que tiene sentido por sí sola.

```css
.card {
}
.button {
}
.nav {
}
```

```html
<div class="card"></div>
```

- No depende del contexto.
- Representa un componente completo.

---

### Element (Elemento)

Es una **parte interna del bloque**.
Depende completamente del bloque.

Sintaxis: `bloque__elemento`

```css
.card__title {
}
.card__content {
}
.card__footer {
}
```

```html
<div class="card">
  <h3 class="card__title">Título</h3>
  <p class="card__content">Contenido</p>
</div>
```

---

### Modifier (Modificador)

Define una **variación de estado o apariencia**.

Sintaxis:

- `bloque--modificador`
- `bloque__elemento--modificador`

```css
.button--primary {
}
.button--secondary {
}
.card--highlighted {
}
```

```html
<button class="button button--primary">Guardar</button>
```

---

## Ejemplo completo BEM

### HTML

```html
<article class="card card--featured">
  <h3 class="card__title">Artículo destacado</h3>
  <p class="card__text">Contenido del artículo</p>
  <button class="card__button card__button--primary">Leer más</button>
</article>
```

---

### CSS

```css
.card {
  padding: 1rem;
  border: 1px solid #ccc;
}

.card--featured {
  border-color: gold;
}

.card__title {
  font-size: 1.2rem;
}

.card__text {
  color: #555;
}

.card__button {
  padding: 0.5rem 1rem;
}

.card__button--primary {
  background-color: blue;
  color: white;
}
```

---

## Reglas clave de BEM

- ❌ No anidar selectores:

```css
.card .title {
}
```

- ✅ Usar clases explícitas:

```css
.card__title {
}
```

---

## Cuándo usar modificadores

Usa modificadores para:

- Estados visuales
- Variantes
- Tamaños
- Temas

```css
.button--disabled {
}
.button--large {
}
.alert--error {
}
.alert--success {
}
```

---

## BEM y estados dinámicos

Estados temporales (JS) suelen manejarse con clases:

```html
<div class="modal modal--open"></div>
```

```css
.modal--open {
  display: block;
}
```

---

## BEM + pseudoclases

```css
.button:hover {
}
.button--primary:hover {
}
```

---

## Ventajas de BEM

- CSS predecible.
- Evita colisiones.
- Facilita trabajo en equipo.
- Escala bien en proyectos grandes.
- Reduce dependencia del HTML.

---

## Errores comunes

- Usar IDs con BEM ❌
- Anidar selectores ❌
- Crear bloques demasiado grandes ❌
- Usar modificadores sin bloque base ❌

---

## Comparación rápida

❌ Sin BEM:

```css
.card .title {
  color: red;
}
```

✅ Con BEM:

```css
.card__title {
  color: red;
}
```

---

## Buenas prácticas finales

- Usa **clases siempre**.
- Un bloque = un componente.
- Elementos no viven fuera del bloque.
- Modificadores no reemplazan al bloque base.
- Mantén nombres claros y consistentes.

---

## Unidades de medida en CSS

Las unidades de medida definen **tamaños, espacios y proporciones** en la interfaz.  
Elegir la unidad correcta es clave para **responsive design**, accesibilidad y escalabilidad.

---

## `px` (píxeles)

Unidad **absoluta**.

```css
.box {
  width: 200px;
  padding: 16px;
}
```

- Tamaño fijo.
- No escala con preferencias del usuario.
- ❌ Poco flexible para responsive.

**Cuándo usarlo**

- Bordes (`border-width`)
- Sombras
- Detalles precisos

---

## `%` (porcentaje)

Unidad **relativa al elemento padre**.

```css
.container {
  width: 80%;
}
```

- Muy útil para layouts fluidos.
- Depende del tamaño del contenedor.

**Casos comunes**

- Anchos de columnas
- Imágenes responsive
- Layouts flexibles

---

## `em`

Unidad **relativa al tamaño de fuente del elemento padre**.

```css
.card {
  font-size: 16px;
}

.card__title {
  font-size: 1.5em; /* 24px */
}
```

- Se acumula (puede crecer sin control).
- Potente pero peligrosa si no se domina.

**Cuándo usarlo**

- Componentes que deben escalar con su contexto
- Padding/margins ligados al texto

---

## `rem` (recomendada)

Unidad **relativa al tamaño de fuente raíz (`html`)**.

```css
html {
  font-size: 16px;
}

p {
  font-size: 1rem; /* 16px */
}
```

- No se acumula.
- Predecible.
- ✔️ **Unidad recomendada para tipografía y spacing**.

**Ventaja clave**

- Escala automáticamente si el usuario cambia el tamaño base.

---

## `vw` (viewport width)

Porcentaje del **ancho del viewport**.

```css
.hero {
  width: 100vw;
}
```

- `1vw` = 1% del ancho de la pantalla.
- Ideal para layouts full width.

---

## `vh` (viewport height)

Porcentaje del **alto del viewport**.

```css
.section {
  min-height: 100vh;
}
```

- `1vh` = 1% del alto de la pantalla.
- Muy usado para secciones a pantalla completa.

---

## Unidades modernas recomendadas

| Unidad | Relativa a      | Uso recomendado        |
| ------ | --------------- | ---------------------- |
| `px`   | Píxel           | Detalles finos         |
| `%`    | Padre           | Layout fluido          |
| `em`   | Padre           | Componentes escalables |
| `rem`  | Root            | Tipografía, spacing    |
| `vw`   | Viewport width  | Layout horizontal      |
| `vh`   | Viewport height | Secciones full screen  |

---

## Recomendación práctica

```css
html {
  font-size: 16px;
}

body {
  font-size: 1rem;
}

.container {
  max-width: 80%;
  padding: 2rem;
}

.hero {
  min-height: 100vh;
}
```

---

## Buenas prácticas (Unidades)

- Usa **`rem` como unidad principal**.
- Usa `%`, `vw`, `vh` para layout responsive.
- Evita depender solo de `px`.
- Usa `em` con cuidado (efecto acumulativo).
- Combina unidades según el contexto.

---

## Tipografía en CSS (Fuentes)

La tipografía define **cómo se lee y percibe** el contenido.  
Una buena elección de fuentes mejora legibilidad, accesibilidad y estética.

---

## Fuentes web

Las **fuentes web** permiten usar tipografías que no están instaladas en el sistema del usuario.

---

## Familias genéricas

Son categorías base que garantizan un fallback correcto.

```css
font-family: serif;
font-family: sans-serif;
font-family: monospace;
```

### Tipos principales

- **serif**  
  Con remates. Más tradicional.  
  Ej: Times New Roman, Georgia

- **sans-serif**  
  Sin remates. Más moderna y legible en pantalla.  
  Ej: Arial, Helvetica

- **monospace**  
  Todos los caracteres ocupan el mismo ancho.  
  Ej: Courier, Consolas

---

## Google Fonts

Servicio popular para fuentes web.

### Uso recomendado

```html
<link
  href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap"
  rel="stylesheet"
/>
```

```css
body {
  font-family: "Inter", sans-serif;
}
```

- `display=swap` mejora rendimiento.
- Permite múltiples pesos (`wght`).

---

## Font stack del sistema (recomendado)

Usa fuentes nativas del sistema para mayor rendimiento.

```css
body {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Arial, sans-serif;
}
```

- Carga instantánea.
- Apariencia nativa en cada SO.
- Ideal para apps web modernas.

---

## Font stack (fallback)

```css
body {
  font-family: "Inter", Arial, sans-serif;
}
```

- Si la primera no carga, usa la siguiente.

---

## Propiedades tipográficas principales

### `font-size`

Define el tamaño del texto.

```css
p {
  font-size: 1rem;
}
```

- Recomendado: `rem`.

---

### `font-weight`

Define el grosor del texto.

```css
h1 {
  font-weight: 700;
}
```

Valores comunes:

- `400` (normal)
- `600` (semi-bold)
- `700` (bold)

---

### `line-height`

Controla el espacio entre líneas.

```css
p {
  line-height: 1.6;
}
```

- Mejor usar valor **unitless**.
- Mejora legibilidad.

---

### `font-style`

Estilo del texto.

```css
em {
  font-style: italic;
}
```

Valores:

- `normal`
- `italic`
- `oblique`

---

### `font-variant`

```css
small {
  font-variant: small-caps;
}
```

---

### `letter-spacing`

Espacio entre letras.

```css
h1 {
  letter-spacing: 0.05em;
}
```

---

### `word-spacing`

```css
p {
  word-spacing: 0.1em;
}
```

---

### `text-transform`

```css
h2 {
  text-transform: uppercase;
}
```

Valores:

- `uppercase`
- `lowercase`
- `capitalize`

---

### `text-align`

```css
p {
  text-align: center;
}
```

---

## Atajo `font`

```css
h1 {
  font: italic 700 2rem/1.2 "Inter", sans-serif;
}
```

Orden:

1. `font-style`
2. `font-weight`
3. `font-size` / `line-height`
4. `font-family`

---

## Ejemplo recomendado (base tipográfica)

```css
html {
  font-size: 16px;
}

body {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Arial, sans-serif;
  font-size: 1rem;
  line-height: 1.6;
  color: #333;
}
```

---

## Buenas prácticas (Tipografía)

- Usa `rem` para tamaños.
- Usa `line-height` sin unidad.
- Limita a 2–3 pesos por fuente.
- Prefiere font stack del sistema.
- Usa Google Fonts con moderación.

---

## Control del texto en CSS

Las propiedades de texto permiten controlar **alineación, transformación y decoración** del contenido textual.  
Afectan la legibilidad y la jerarquía visual.

---

## `text-align`

Define la **alineación horizontal** del texto dentro de su contenedor.

```css
p {
  text-align: left;
}
```

Valores comunes:

- `left` (por defecto)
- `right`
- `center`
- `justify`

### Ejemplos

```css
h1 {
  text-align: center;
}

p {
  text-align: justify;
}
```

> `text-align` **no centra elementos**, solo texto.

---

## `text-transform`

Controla la **capitalización** del texto.

```css
p {
  text-transform: uppercase;
}
```

Valores:

- `uppercase` → todo en mayúsculas
- `lowercase` → todo en minúsculas
- `capitalize` → primera letra de cada palabra en mayúscula
- `none` → sin transformación

### Ejemplo

```css
h2 {
  text-transform: capitalize;
}
```

> No modifica el contenido real, solo la visualización.

---

## `text-decoration`

Aplica decoraciones al texto.

```css
a {
  text-decoration: underline;
}
```

Valores comunes:

- `underline`
- `overline`
- `line-through`
- `none`

---

### Combinación moderna de `text-decoration`

```css
a {
  text-decoration-line: underline;
  text-decoration-style: solid;
  text-decoration-color: red;
}
```

O en una sola línea:

```css
a {
  text-decoration: underline solid red;
}
```

---

## Quitar subrayado en enlaces

```css
a {
  text-decoration: none;
}
```

> Recomendado agregar otro indicador visual (color, hover).

---

## Propiedades relacionadas útiles

### `text-indent`

```css
p {
  text-indent: 2rem;
}
```

---

### `white-space`

Controla cómo se manejan espacios y saltos de línea.

```css
pre {
  white-space: pre;
}
```

Valores comunes:

- `normal`
- `nowrap`
- `pre`
- `pre-wrap`

---

### `text-overflow`

```css
.title {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```

---

## Ejemplo práctico

```css
.article-title {
  text-align: center;
  text-transform: uppercase;
  text-decoration: underline;
  letter-spacing: 0.05em;
}
```

---

## Buenas prácticas (Texto)

- Evita textos largos en `uppercase`.
- Usa `justify` con cuidado (puede crear ríos).
- No dependas solo del subrayado para enlaces.
- Mantén coherencia tipográfica.

---

## Sistema de colores en CSS

CSS ofrece varios sistemas para definir colores.  
Elegir el adecuado mejora **consistencia visual**, **mantenibilidad** y **accesibilidad**.

---

## Colores por nombre

```css
p {
  color: green;
}
```

- CSS soporta nombres predefinidos (`red`, `blue`, `green`, etc.).
- ❌ Poco precisos.
- ❌ No recomendados para sistemas de diseño.

---

## HEX

Representación hexadecimal.

```css
.box {
  background-color: #ff0000;
}
```

Variantes:

- `#ff0000` → rojo
- `#fff` → blanco (forma corta)
- `#000` → negro

✔️ Muy común  
✔️ Fácil de copiar  
❌ Difícil de ajustar visualmente

---

## RGB

Define color por canales rojo, verde y azul.

```css
.text {
  color: rgb(255, 0, 0);
}
```

- Cada valor va de `0` a `255`.
- Más intuitivo que HEX para ajustes.

---

## RGBA (transparencia alpha)

```css
.overlay {
  background-color: rgba(0, 0, 0, 0.5);
}
```

- `alpha`: valor de `0` (transparente) a `1` (opaco).
- Muy usado para overlays y sombras.

---

## HSL (recomendado)

Define color por:

- **Hue** (tono)
- **Saturation** (saturación)
- **Lightness** (luminosidad)

```css
.button {
  background-color: hsl(220, 80%, 50%);
}
```

✔️ Más fácil de ajustar visualmente  
✔️ Ideal para sistemas de diseño

---

## HSLA

```css
.alert {
  background-color: hsla(220, 80%, 50%, 0.7);
}
```

---

## `currentColor`

Usa el color actual del texto.

```css
.icon {
  color: blue;
}

.icon svg {
  fill: currentColor;
}
```

- Hereda el valor de `color`.
- Muy útil para íconos y SVG.
- Mejora consistencia.

---

## Ejemplo comparativo

```css
.hex {
  color: #ff0000;
}

.rgb {
  color: rgb(255, 0, 0);
}

.hsl {
  color: hsl(0, 100%, 50%);
}
```

---

## Recomendación práctica

```css
:root {
  --primary: hsl(220, 80%, 50%);
  --primary-light: hsl(220, 80%, 70%);
  --overlay: hsla(0, 0%, 0%, 0.5);
}

.button {
  background-color: var(--primary);
  color: white;
}
```

---

## Buenas prácticas (Colores)

- Usa **HSL** para sistemas de color.
- Usa `rgba` / `hsla` para transparencias.
- Evita nombres de color en producción.
- Usa `currentColor` para íconos.
- Define colores con variables CSS.

---

## Variables CSS (Custom Properties)

Las **variables CSS** permiten definir valores reutilizables que pueden cambiar dinámicamente según el contexto.  
Son clave para **sistemas de diseño**, temas y mantenimiento del código.

---

## Declaración de variables

Las variables se declaran con `--` y se acceden con `var()`.

```css
--color-primary: blue;
```

---

## `:root`

` :root` representa el **elemento raíz del documento (`html`)**.  
Las variables definidas aquí son **globales**.

```css
:root {
  --color-primary: hsl(220, 80%, 50%);
  --color-secondary: hsl(160, 60%, 40%);
  --spacing: 1rem;
}
```

---

## Uso de variables con `var()`

```css
.button {
  background-color: var(--color-primary);
  padding: var(--spacing);
}
```

---

## Valor por defecto (fallback)

```css
.card {
  color: var(--text-color, #333);
}
```

- Si la variable no existe, se usa el valor de respaldo.

---

## Sobrescribir variables por contexto

Las variables siguen **el alcance del DOM**.

### Ejemplo: sobrescribir en una clase

```css
:root {
  --color-primary: blue;
}

.dark-theme {
  --color-primary: orange;
}

.button {
  background-color: var(--color-primary);
}
```

```html
<button class="button">Claro</button>

<div class="dark-theme">
  <button class="button">Oscuro</button>
</div>
```

✔️ El segundo botón usa el valor sobrescrito.

---

## Sobrescribir variables por componente

```css
.card {
  --card-bg: white;
  background-color: var(--card-bg);
}

.card--highlighted {
  --card-bg: gold;
}
```

---

## Variables y estados

```css
.button {
  --btn-color: hsl(220, 80%, 50%);
  background-color: var(--btn-color);
}

.button:hover {
  --btn-color: hsl(220, 80%, 40%);
}
```

---

## Variables y media queries

```css
:root {
  --font-size: 1rem;
}

@media (max-width: 768px) {
  :root {
    --font-size: 0.9rem;
  }
}
```

---

## Ventajas de las variables CSS

- Reutilización.
- Temas (dark/light).
- Menos duplicación.
- Cambio dinámico sin JS.
- Funcionan con herencia.

---

## Ejemplo completo (sistema de diseño simple)

```css
:root {
  --color-primary: hsl(220, 80%, 50%);
  --color-bg: #fff;
  --color-text: #333;
}

body {
  background-color: var(--color-bg);
  color: var(--color-text);
}

.dark {
  --color-bg: #111;
  --color-text: #eee;
}
```

---

## Buenas prácticas (Variables CSS)

- Define variables globales en `:root`.
- Usa nombres semánticos (`--color-primary`).
- No abuses de valores mágicos.
- Usa variables para colores, spacing y tipografía.
- Sobrescribe por contexto, no por duplicación.

---

## Degradados en CSS

Los **degradados (gradients)** permiten crear transiciones suaves entre colores **sin usar imágenes**.  
Se consideran **imágenes CSS** y se usan comúnmente en `background` o `background-image`.

---

## `linear-gradient()`

Crea un degradado en línea recta.

### Lineal simple

```css
.box {
  background: linear-gradient(red, blue);
}
```

- Por defecto: de arriba hacia abajo.
- Dos colores mínimos.

---

### Lineal con dirección

```css
.box {
  background: linear-gradient(to right, red, blue);
}
```

Direcciones comunes:

- `to top`
- `to bottom`
- `to left`
- `to right`

---

### Lineal con ángulo

```css
.box {
  background: linear-gradient(45deg, red, blue);
}
```

- `0deg` → de abajo hacia arriba
- `90deg` → izquierda a derecha
- `180deg` → arriba a abajo

---

### Lineal diagonal

```css
.box {
  background: linear-gradient(to bottom right, red, blue);
}
```

---

## Múltiples colores en degradado lineal

```css
.box {
  background: linear-gradient(to right, red, yellow, green, blue);
}
```

---

### Control de posiciones

```css
.box {
  background: linear-gradient(
    to right,
    red 0%,
    yellow 40%,
    green 70%,
    blue 100%
  );
}
```

---

## `radial-gradient()`

Crea un degradado desde un punto central hacia afuera.

---

### Radial simple

```css
.box {
  background: radial-gradient(circle, red, blue);
}
```

- Por defecto: círculo centrado.

---

### Radial con posición

```css
.box {
  background: radial-gradient(circle at top left, red, blue);
}
```

Posiciones comunes:

- `center`
- `top`
- `bottom`
- `left`
- `right`
- `top left`, etc.

---

### Radial con tamaño

```css
.box {
  background: radial-gradient(circle closest-side, red, blue);
}
```

Valores:

- `closest-side`
- `farthest-side`
- `closest-corner`
- `farthest-corner`

---

## Degradados con transparencia

```css
.overlay {
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0));
}
```

---

## Ejemplo combinado (realista)

```css
.hero {
  background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
    url("banner.jpg");
  background-size: cover;
}
```

---

## Buenas prácticas (Degradados)

- Usa degradados para overlays.
- Evita degradados muy saturados.
- Prefiere HSL para ajustar colores.
- Combina con variables CSS.

---

## Ejemplo con variables CSS

```css
:root {
  --primary: hsl(220, 80%, 50%);
  --secondary: hsl(160, 60%, 40%);
}

.button {
  background: linear-gradient(to right, var(--primary), var(--secondary));
}
```

---

## Sombras y bordes en CSS

Las **sombras y bordes** aportan profundidad, jerarquía visual y separación entre elementos.  
Bien usados, mejoran la experiencia; mal usados, saturan la interfaz.

---

## `box-shadow`

Aplica sombra a la **caja completa** del elemento.

### Sintaxis

```css
box-shadow: offset-x offset-y blur spread color;
```

---

## Sombra simple

```css
.card {
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
}
```

Valores:

- `offset-x` → desplazamiento horizontal
- `offset-y` → desplazamiento vertical
- `blur` → difuminado
- `spread` → expansión (opcional)
- `color`

---

## Sombra interna (`inset`)

```css
.input {
  box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.2);
}
```

- La sombra se dibuja **hacia dentro**.
- Útil para inputs y efectos de profundidad interna.

---

## Múltiples sombras

```css
.card {
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1), 0 8px 16px rgba(0, 0, 0, 0.08);
}
```

- Se apilan de arriba hacia abajo.
- Permite sombras más realistas.

---

## `text-shadow`

Aplica sombra al **texto**.

```css
h1 {
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4);
}
```

Sintaxis:

```css
text-shadow: offset-x offset-y blur color;
```

---

## `border`

Define el borde del elemento.

```css
.box {
  border: 1px solid #ccc;
}
```

Componentes:

- `border-width`
- `border-style`
- `border-color`

---

### Bordes individuales

```css
.box {
  border-top: 2px solid red;
  border-bottom: 1px dashed gray;
}
```

---

## `border-radius`

Redondea las esquinas del elemento.

```css
.card {
  border-radius: 8px;
}
```

---

### Bordes circulares

```css
.avatar {
  width: 80px;
  height: 80px;
  border-radius: 50%;
}
```

---

### Bordes asimétricos

```css
.box {
  border-radius: 8px 16px 4px 16px;
}
```

Orden:

- top-left
- top-right
- bottom-right
- bottom-left

---

## Combinación borde + sombra

```css
.card {
  border: 1px solid #e5e5e5;
  border-radius: 12px;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.08);
}
```

---

## Buenas prácticas (Sombras y bordes)

- Usa sombras sutiles.
- Evita sombras muy oscuras o duras.
- Usa `rgba` o `hsla` para suavidad.
- Usa `border-radius` de forma consistente.
- No mezcles demasiados estilos de sombra.

---

## Ejemplo recomendado (card moderna)

```css
.card {
  background: white;
  border-radius: 12px;
  border: 1px solid #eee;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1), 0 4px 12px rgba(0, 0, 0, 0.08);
}
```

---

## Flexbox (Flexible Box Layout)

Flexbox es un sistema de layout diseñado para **alinear y distribuir elementos** en una dimensión (fila o columna).  
Es ideal para componentes, alineación y layouts simples.

---

## Activar Flexbox

```css
.container {
  display: flex;
}
```

- Convierte al elemento en **contenedor flex**.
- Sus hijos se convierten en **flex items**.

---

## `flex-direction`

Define la **dirección principal** del eje.

```css
.container {
  flex-direction: row;
}
```

Valores:

- `row` → horizontal (por defecto)
- `row-reverse`
- `column`
- `column-reverse`

### Columna

```css
.container {
  display: flex;
  flex-direction: column;
}
```

---

## Ejes en Flexbox

- **Eje principal** → definido por `flex-direction`
- **Eje secundario (cross axis)** → perpendicular al principal

Ejemplo:

- `row` → principal horizontal / secundario vertical
- `column` → principal vertical / secundario horizontal

---

## `justify-content`

Alinea los elementos en el **eje principal**.

```css
.container {
  justify-content: center;
}
```

Valores comunes:

- `flex-start`
- `center`
- `flex-end`
- `space-between`
- `space-around`
- `space-evenly`

---

## `align-items`

Alinea los elementos en el **eje secundario**.

```css
.container {
  align-items: center;
}
```

Valores:

- `stretch` (por defecto)
- `flex-start`
- `center`
- `flex-end`
- `baseline`

---

## `flex-grow`

Controla **cuánto puede crecer** un elemento respecto a los demás.

```css
.item {
  flex-grow: 1;
}
```

Ejemplo:

```css
.item-1 {
  flex-grow: 1;
}

.item-2 {
  flex-grow: 2;
}
```

👉 El segundo crece el doble.

---

## Propiedad abreviada `flex`

```css
.item {
  flex: 1;
}
```

Equivale a:

```css
flex-grow: 1;
flex-shrink: 1;
flex-basis: 0;
```

Ejemplo típico:

```css
.column {
  flex: 1;
}
```

---

## `align-self`

Permite que **un solo elemento** sobrescriba `align-items`.

```css
.item-special {
  align-self: flex-end;
}
```

Valores:

- `auto`
- `flex-start`
- `center`
- `flex-end`
- `stretch`

---

## Ejemplo completo

```css
.container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.item {
  flex: 1;
}

.item-right {
  align-self: flex-end;
}
```

```html
<div class="container">
  <div class="item">A</div>
  <div class="item">B</div>
  <div class="item item-right">C</div>
</div>
```

---

## Buenas prácticas (Flexbox)

- Usa Flexbox para **componentes**, no para grids complejos.
- Piensa siempre en los ejes.
- Usa `gap` para espacios (mejor que margins).
- Prefiere `flex` en lugar de `flex-grow` aislado.

---

## Resumen rápido

- `display: flex` → activa flexbox
- `flex-direction` → dirección
- `justify-content` → eje principal
- `align-items` → eje secundario
- `flex` → crecimiento del item
- `align-self` → alineación individual

---

## CSS Grid (Grid Layout)

CSS Grid es un sistema de layout **bidimensional** (filas y columnas).  
Es ideal para **estructuras de página** y layouts complejos.

---

## Activar Grid

```css
.container {
  display: grid;
}
```

- El contenedor se convierte en **grid container**.
- Sus hijos son **grid items**.

---

## `grid-template-columns`

Define las columnas del grid.

```css
.container {
  grid-template-columns: 200px 1fr 2fr;
}
```

- Acepta valores fijos y flexibles.

---

## `fr` (fraction)

Unidad flexible que reparte el espacio disponible.

```css
.container {
  grid-template-columns: 1fr 1fr 1fr;
}
```

- Cada columna ocupa una fracción igual.

---

## `repeat()`

Simplifica definiciones repetidas.

```css
.container {
  grid-template-columns: repeat(3, 1fr);
}
```

Equivale a:

```css
grid-template-columns: 1fr 1fr 1fr;
```

---

## Filas (`grid-template-rows`)

```css
.container {
  grid-template-rows: auto 1fr auto;
}
```

---

## `gap`

Espacio entre filas y columnas.

```css
.container {
  gap: 16px;
}
```

También:

```css
gap: 10px 20px; /* filas | columnas */
```

✔️ Recomendado en lugar de margins.

---

## Grid Lines (líneas del grid)

Las líneas se numeran desde 1.

```css
.item {
  grid-column: 1 / 3;
  grid-row: 1 / 2;
}
```

- `1 / 3` → desde la línea 1 hasta la 3.

---

## `grid-span`

Extiende un elemento varias columnas o filas.

```css
.item {
  grid-column: span 2;
}
```

```css
.item {
  grid-row: span 3;
}
```

---

## `grid-template-areas`

Define el layout de forma **visual y semántica**.

```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
  gap: 16px;
}
```

```css
.header {
  grid-area: header;
}
.sidebar {
  grid-area: sidebar;
}
.main {
  grid-area: main;
}
.footer {
  grid-area: footer;
}
```

```html
<div class="container">
  <header class="header">Header</header>
  <aside class="sidebar">Sidebar</aside>
  <main class="main">Main</main>
  <footer class="footer">Footer</footer>
</div>
```

---

## Grid automático

```css
.container {
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
}
```

- Layout responsive sin media queries.
- Muy usado en galerías y cards.

---

## Ejemplo completo

```css
.layout {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: auto 1fr;
  gap: 24px;
}

.header {
  grid-column: span 3;
}
```

---

## Grid vs Flexbox

| Grid                  | Flexbox            |
| --------------------- | ------------------ |
| 2D (filas y columnas) | 1D (una dimensión) |
| Layout de página      | Componentes        |
| Estructura global     | Alineación         |

---

## Buenas prácticas (CSS Grid)

- Usa Grid para layouts grandes.
- Usa `fr` y `repeat()` para flexibilidad.
- Usa `gap`, no margins.
- Prefiere `grid-template-areas` para layouts claros.
- Combina Grid + Flexbox cuando sea necesario.

---

## Media Queries y Diseño Responsive

Las **media queries** permiten adaptar el diseño según el tamaño, resolución y capacidades del dispositivo.  
Son la base del **responsive design moderno**.

---

## Media Queries

```css
@media (max-width: 768px) {
  body {
    font-size: 14px;
  }
}
```

- Evalúan condiciones del dispositivo.
- Se usan para cambiar layout, tipografía y visibilidad.

---

## Enfoque Mobile First (recomendado)

Mobile First significa:

- Escribir primero los estilos para **pantallas pequeñas**.
- Escalar progresivamente a pantallas más grandes.

```css
/* Base: mobile */
.container {
  padding: 1rem;
}

/* Tablet */
@media (min-width: 768px) {
  .container {
    padding: 2rem;
  }
}
```

✔️ Mejor rendimiento  
✔️ Mejor experiencia real de usuario  
✔️ Código más limpio

---

## Columnas responsive

### Mobile First con Grid

```css
.grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 16px;
}

@media (min-width: 768px) {
  .grid {
    grid-template-columns: repeat(3, 1fr);
  }
}
```

---

## Menú responsive

```css
.nav {
  display: none;
}

@media (min-width: 768px) {
  .nav {
    display: flex;
  }
}
```

- En mobile: menú oculto / hamburguesa.
- En desktop: menú visible.

---

## Visibilidad responsive

```css
.hide-mobile {
  display: none;
}

@media (min-width: 768px) {
  .hide-mobile {
    display: block;
  }
}
```

---

## Diseño fluido

Un diseño fluido se adapta **continuamente** al tamaño de pantalla  
hasta que alcanza un breakpoint.

---

## Contenedor fluido

```css
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 1rem;
}
```

Propiedades clave:

- `width`
- `max-width`
- `min-width`

---

## Grid fluido automático

```css
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 16px;
}
```

✔️ No requiere media queries  
✔️ Ideal para cards y galerías

---

## Imágenes fluidas

```css
img {
  max-width: 100%;
  height: auto;
}
```

- Se adaptan al contenedor.
- Evita desbordes.

---

## Texto fluido con `clamp()`

```css
h1 {
  font-size: clamp(1.5rem, 5vw, 3rem);
}
```

Estructura:

```text
clamp(mínimo, preferido, máximo)
```

✔️ Escala suave  
✔️ Sin media queries

---

## Mobile First: principios clave

### Cargar lo esencial primero

- Menos CSS
- Menos JS
- Contenido prioritario

---

### Contenido prioritario

- Información clave visible sin scroll excesivo.
- CTA claros.
- Evitar elementos secundarios en mobile.

---

### Mejora progresiva

```text
Mobile → Tablet → Desktop
```

- No ocultes funcionalidades críticas.
- Agrega mejoras visuales progresivas.

---

### Touch friendly

```css
button {
  min-width: 44px;
  min-height: 44px;
}
```

- Recomendación WCAG.
- Mejora usabilidad táctil.

---

### Navegación progresiva

- Mobile: menú simple
- Desktop: menú completo
- Mega-menús solo si aportan valor

---

### Cards progresivas

```css
.card {
  padding: 1rem;
}

@media (min-width: 1024px) {
  .card {
    padding: 2rem;
  }
}
```

---

## Buenas prácticas finales

- Usa **Mobile First siempre**.
- Prefiere diseños fluidos.
- Usa `clamp()` para tipografía.
- Usa Grid automático (`auto-fit`).
- No diseñes solo para desktop.
- Prueba en dispositivos reales.

---

## Transformaciones, Transiciones y Animaciones en CSS

CSS permite **mover, rotar, escalar y animar** elementos sin JavaScript.  
Se usan para mejorar la interacción y el feedback visual.

---

## `transform`

Modifica visualmente un elemento **sin afectar el flujo del layout**.

### `translate`

Mueve el elemento en los ejes X y Y.

```css
.box {
  transform: translate(20px, 10px);
}
```

Variantes:

```css
transform: translateX(20px);
transform: translateY(10px);
```

---

### `rotate`

Rota el elemento.

```css
.box {
  transform: rotate(45deg);
}
```

- Valores en `deg`, `turn`, `rad`.

---

### `scale`

Escala el tamaño del elemento.

```css
.box {
  transform: scale(1.2);
}
```

Variantes:

```css
transform: scaleX(1.2);
transform: scaleY(0.8);
```

---

### Transformaciones combinadas

```css
.box {
  transform: translateY(10px) rotate(5deg) scale(1.05);
}
```

> El orden **sí importa**.

---

## `transition`

Define **cómo** cambian las propiedades en el tiempo.

### Sintaxis básica

```css
transition: property duration timing-function delay;
```

---

### Ejemplo simple

```css
.button {
  background-color: blue;
  transition: background-color 0.3s ease;
}

.button:hover {
  background-color: darkblue;
}
```

---

## `transition-timing-function`

Controla la aceleración.

Valores comunes:

- `linear`
- `ease` (por defecto)
- `ease-in`
- `ease-out`
- `ease-in-out`

```css
.box {
  transition: transform 0.4s ease-in-out;
}
```

---

### Múltiples transiciones

```css
.card {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
```

---

## Buenas prácticas con transiciones

- Transiciona solo propiedades necesarias.
- Prefiere `transform` y `opacity` (mejor rendimiento).
- Evita transiciones largas.

---

## Animaciones (`@keyframes`)

Permiten animaciones **automáticas y repetitivas**.

---

## `@keyframes`

Define los estados de la animación.

```css
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
```

---

## `animation`

Aplica la animación.

```css
.box {
  animation: fadeIn 1s ease forwards;
}
```

Sintaxis:

```css
animation: name duration timing-function delay iteration-count direction
  fill-mode;
```

---

## Animaciones comunes

### Pulse

```css
@keyframes pulse {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
  100% {
    transform: scale(1);
  }
}

.pulse {
  animation: pulse 1.5s ease-in-out infinite;
}
```

---

### Rotate / Spin

```css
@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

.spinner {
  animation: spin 1s linear infinite;
}
```

---

### Bounce

```css
@keyframes bounce {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
}

.bounce {
  animation: bounce 0.8s ease-in-out infinite;
}
```

---

## Control de animaciones

```css
.box {
  animation-play-state: paused;
}
```

```css
.box:hover {
  animation-play-state: running;
}
```

---

## Transición vs Animación

| Transición          | Animación         |
| ------------------- | ----------------- |
| Reacciona a eventos | Automática        |
| Simple              | Compleja          |
| Hover / focus       | Loops, secuencias |
| Menor control       | Mayor control     |

---

## Accesibilidad (reduce motion)

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}
```

---

## Buenas prácticas finales

- Usa `transform` + `opacity`.
- Evita animaciones excesivas.
- Usa `ease-in-out` para UI.
- Respeta `prefers-reduced-motion`.
- Prioriza claridad sobre espectáculo.

---
