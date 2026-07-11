## Guía Rápida de JavaScript

Referencia breve de sintaxis y comportamiento propio de JavaScript: variables, tipos, operadores, control de flujo, funciones, objetos, clases, asincronía, módulos y APIs del navegador (DOM, Fetch).

> Versión: ECMAScript 2024+ (ES2015 y posteriores) · Actualizado: 2026-07-10

## Tabla de contenidos

- [Formas de incluir JavaScript](#formas-de-incluir-javascript)
- [Comentarios](#comentarios)
- [Variables (`let`, `const`, `var`)](#variables-let-const-var)
- [Hoisting y Temporal Dead Zone](#hoisting-y-temporal-dead-zone)
- [Tipos de datos](#tipos-de-datos)
- [Conversión de tipos](#conversión-de-tipos)
- [Operadores](#operadores)
- [Optional chaining y nullish coalescing](#optional-chaining-y-nullish-coalescing)
- [Estructuras condicionales](#estructuras-condicionales)
- [Bucles](#bucles)
- [Strings](#strings)
- [Números y `Math`](#números-y-math)
- [Arrays](#arrays)
- [Destructuring](#destructuring)
- [Spread y Rest](#spread-y-rest)
- [Objetos](#objetos)
- [Funciones](#funciones)
- [Scope y Closures](#scope-y-closures)
- [`this`](#this)
- [Clases](#clases)
- [Manejo de errores](#manejo-de-errores)
- [JSON](#json)
- [`Map` y `Set`](#map-y-set)
- [Iteradores y Generadores](#iteradores-y-generadores)
- [Fechas (`Date`)](#fechas-date)
- [Expresiones regulares](#expresiones-regulares)
- [Modelo de ejecución (Call Stack, Event Loop)](#modelo-de-ejecución-call-stack-event-loop)
- [Promesas](#promesas)
- [Async / Await](#async--await)
- [Módulos (`import` / `export`)](#módulos-import--export)
- [DOM: selección y manipulación](#dom-selección-y-manipulación)
- [Eventos del DOM](#eventos-del-dom)
- [Formularios en el DOM](#formularios-en-el-dom)
- [HTTP y Fetch API](#http-y-fetch-api)

---

## Formas de incluir JavaScript

- **Externo** (recomendado): separa responsabilidades y permite cachear el archivo.

```html
<script src="app.js" defer></script>
```

- **Interno**: útil para pruebas rápidas, no escalable.

```html
<script>
  console.log("Hola mundo");
</script>
```

- `defer` descarga el script en paralelo y lo ejecuta cuando el HTML ya fue parseado. `async` lo ejecuta tan pronto termine de descargar, sin garantizar orden.

```js
console.log("Hola mundo"); // consola del navegador: F12 -> pestaña Console
```

---

## Comentarios

```js
// Comentario de una línea

/*
  Comentario
  de varias líneas
*/
```

---

## Variables (`let`, `const`, `var`)

```js
let edad = 20;
edad = 21; // reasignable, scope de bloque

const PI = 3.1416; // no reasignable, scope de bloque, recomendada por defecto

var legado = "evitar"; // scope de función, hoisting completo
```

`const` impide la reasignación, no la mutación interna de objetos/arrays:

```js
const user = { name: "Ana" };
user.name = "Luis"; // válido
user = {}; // TypeError
```

---

## Hoisting y Temporal Dead Zone

`var` y las declaraciones `function` se elevan al inicio de su scope; `let`/`const` también se elevan pero quedan en la **Temporal Dead Zone (TDZ)** hasta su declaración.

```js
console.log(a); // undefined
var a = 10;

console.log(b); // ReferenceError (TDZ)
let b = 5;
```

| Keyword | Scope   | Hoisting | Reasignar | Redeclarar |
| ------- | ------- | -------- | --------- | ---------- |
| `var`   | Función | Sí       | Sí        | Sí         |
| `let`   | Bloque  | TDZ      | Sí        | No         |
| `const` | Bloque  | TDZ      | No        | No         |

---

## Tipos de datos

JavaScript es **dinámicamente tipado**: una variable puede cambiar de tipo en tiempo de ejecución.

**Primitivos** (inmutables, se copian por valor):

```js
let nombre = "Juan"; // string
let edad = 25; // number
let activo = true; // boolean
let vacio = null; // ausencia intencional de valor
let sinDefinir; // undefined
const id = Symbol("id"); // symbol, identificador único
const enorme = 12345678901234567890n; // bigint
```

**Complejos** (se copian por referencia):

```js
const persona = { nombre: "Ana", edad: 30 }; // object
const numeros = [1, 2, 3]; // array (es un object)
function saludar() {} // function (es un object invocable)
```

**Comprobación con `typeof`**

```js
typeof "hola"; // 'string'
typeof 10; // 'number'
typeof true; // 'boolean'
typeof undefined; // 'undefined'
typeof null; // 'object' (error histórico del lenguaje)
typeof {}; // 'object'
typeof []; // 'object'
typeof function () {}; // 'function'
typeof Symbol(); // 'symbol'
typeof 10n; // 'bigint'
```

```js
Array.isArray([1, 2]); // true, distingue array de object
```

---

## Conversión de tipos

### Explícita (recomendada)

```js
String(123); // '123'
String(true); // 'true'

Number("123"); // 123
Number("3.14"); // 3.14
Number(true); // 1
Number("10px"); // NaN

Boolean(1); // true
Boolean(0); // false
Boolean(""); // false
Boolean("hola"); // true

parseInt("10px"); // 10, ignora sufijo no numérico
parseInt("1010", 2); // 10, binario a decimal
parseFloat("10.5px"); // 10.5
```

### Implícita (coerción automática)

```js
"5" + 3; // '53' -> '+' prioriza string si hay uno presente
"5" - 2; // 3    -> operadores aritméticos fuerzan number
2 + true; // 3    -> true -> 1, false -> 0
"5" == 5; // true  -> == compara con coerción
"5" === 5; // false -> === compara valor y tipo (recomendado siempre)
null == undefined; // true
null === undefined; // false
```

---

## Operadores

- **Aritméticos**

```js
2 + 3; // 5
5 - 2; // 3
4 * 3; // 12
10 / 2; // 5
10 % 3; // 1  (módulo/resto)
2 ** 3; // 8  (exponenciación)
```

- **Asignación**

```js
let x = 5;
x += 2; // 7
x -= 1; // 6
x *= 2; // 12
x /= 3; // 4
x **= 2; // 16
```

- **Comparación**

```js
5 > 3; // true
5 >= 5; // true
5 < 3; // false
5 === "5"; // false, compara tipo también
5 !== "5"; // true
```

- **Lógicos**

```js
true && false; // false, AND
true || false; // true,  OR
!true; // false, NOT
```

- **Cortocircuito (short-circuit)**

```js
false && console.log("no se ejecuta");
true || console.log("no se ejecuta");

const nombre = input || "Invitado"; // valor por defecto si input es falsy
```

- **Ternario**

```js
const mensaje = edad >= 18 ? "Mayor" : "Menor";
```

- **Precedencia**: `&&` se evalúa antes que `||`; usa paréntesis para claridad.

```js
true || (false && false); // true
```

---

## Optional chaining y nullish coalescing

```js
const user = { profile: { name: "Ana" } };

user?.profile?.name; // 'Ana'
user?.address?.city; // undefined, sin lanzar error si address no existe
user?.saludar?.(); // llama solo si saludar existe

user.items?.[0]; // acceso opcional a índice de array
```

```js
const valor = 0;
valor || "default"; // 'default' -> || trata 0, '', NaN como falsy
valor ?? "default"; // 0         -> ?? solo cae en default si es null o undefined
```

---

## Estructuras condicionales

```js
if (edad >= 18) {
  console.log("Mayor de edad");
} else if (edad >= 13) {
  console.log("Adolescente");
} else {
  console.log("Menor de edad");
}
```

```js
switch (dia) {
  case 1:
    console.log("Lunes");
    break;
  case 2:
    console.log("Martes");
    break;
  default:
    console.log("Día no válido");
}
```

- `switch` compara con `===` (sin coerción de tipos).
- Sin `break`, la ejecución cae al siguiente `case` ("fallthrough").

---

## Bucles

```js
for (let i = 0; i < 5; i++) {
  console.log(i); // 0 1 2 3 4
}

for (const n of [1, 2, 3]) {
  console.log(n); // valores de un iterable
}

for (const key in { a: 1, b: 2 }) {
  console.log(key); // claves de un objeto -> 'a' 'b'
}

let i = 0;
while (i < 3) {
  console.log(i);
  i++;
}

let j = 0;
do {
  console.log(j); // se ejecuta al menos una vez
  j++;
} while (j < 3);
```

```js
[1, 2, 3].forEach((n, index) => console.log(index, n));
// no admite break/continue, solo para arrays
```

```js
for (let i = 0; i < 5; i++) {
  if (i === 3) break; // detiene el bucle
  if (i === 1) continue; // salta a la siguiente iteración
  console.log(i);
}
```

| Bucle        | Uso principal          |
| ------------ | ----------------------- |
| `for`        | Contador con índice     |
| `for...of`   | Valores de un iterable  |
| `for...in`   | Claves de un objeto     |
| `while`      | Condición dinámica      |
| `do...while` | Al menos una ejecución  |
| `forEach`    | Arrays, estilo funcional|

---

## Strings

```js
const nombre = "Juan";
const saludo = `Hola ${nombre}, tienes ${20 + 1} años`; // template literal
```

```js
const texto = "JavaScript";
texto.length; // 10
texto[0]; // 'J'
texto.charAt(1); // 'a'
texto.slice(0, 4); // 'Java'  (soporta índices negativos)
texto.slice(-6); // 'Script'
texto.toUpperCase(); // 'JAVASCRIPT'
texto.toLowerCase(); // 'javascript'
"  hola  ".trim(); // 'hola'
texto.includes("Script"); // true
texto.indexOf("S"); // 4
texto.startsWith("Java"); // true
texto.endsWith("ipt"); // true
texto.replace("Java", "Type"); // 'TypeScript'
texto.replaceAll("a", "A"); // 'JAvAScript'
texto.repeat(2); // 'JavaScriptJavaScript'
texto.padStart(12, "0"); // '00JavaScript'
texto.padEnd(12, "-"); // 'JavaScript--'
"1,2,3".split(","); // ['1', '2', '3']
["Java", "Script"].join(""); // 'JavaScript'
```

---

## Números y `Math`

```js
const entero = 10;
const decimal = 3.14;
const grande = 1e6; // 1_000_000
const legible = 1_000_000; // separador visual, mismo valor que 1e6

1 / 0; // Infinity
Number("hola"); // NaN
Number.isNaN(NaN); // true, más fiable que el global isNaN()
Number.isInteger(4); // true

(0.1 + 0.2).toFixed(2); // '0.30' -> devuelve string, JS usa punto flotante (IEEE 754)
```

```js
Math.sqrt(9); // 3
Math.abs(-5); // 5
Math.round(3.6); // 4
Math.floor(3.6); // 3
Math.ceil(3.1); // 4
Math.max(1, 5, 3); // 5
Math.min(1, 5, 3); // 1
Math.random(); // número entre 0 (incluido) y 1 (excluido)

Math.floor(Math.random() * (max - min + 1)) + min; // entero aleatorio entre min y max
```

---

## Arrays

```js
const numeros = [1, 2, 3]; // sintaxis literal, recomendada
Array.isArray(numeros); // true
numeros.length; // 3
numeros.at(-1); // 3, acceso desde el final
```

**Mutan el array original**

```js
numeros.push(4); // agrega al final -> [1,2,3,4]
numeros.pop(); // elimina el último
numeros.unshift(0); // agrega al inicio
numeros.shift(); // elimina el primero
numeros.splice(1, 1, "x"); // elimina/inserta en una posición
numeros.sort((a, b) => a - b); // ordena in place, comparador numérico explícito
numeros.reverse();
```

**Retornan un nuevo array (inmutables)**

```js
const dobles = numeros.map((n) => n * 2);
const pares = numeros.filter((n) => n % 2 === 0);
const total = numeros.reduce((acc, n) => acc + n, 0);
const copia = numeros.slice(0, 2);
const combinado = numeros.concat([9, 9]);
const plano = [1, [2, [3, 4]]].flat(2); // [1, 2, 3, 4]
const mapPlano = numeros.flatMap((n) => [n, n * 10]);
```

**Búsqueda y comprobación**

```js
numeros.find((n) => n > 1); // primer valor que cumple
numeros.findIndex((n) => n > 1); // su índice
numeros.includes(3); // true, comprueba presencia
numeros.some((n) => n > 2); // true si al menos uno cumple
numeros.every((n) => n > 0); // true si todos cumplen
```

| Método | Retorna nuevo array | Modifica el original |
| ------ | -------------------- | --------------------- |
| `map` / `filter` / `slice` / `concat` | Sí | No |
| `push` / `pop` / `splice` / `sort` / `reverse` | No | Sí |

---

## Destructuring

```js
const [a, b, ...resto] = [1, 2, 3, 4];
// a = 1, b = 2, resto = [3, 4]

const [, segundo] = ["x", "y"]; // se omite el primero

const { nombre, edad, pais = "N/A" } = { nombre: "Ana", edad: 30 };
// pais toma el valor por defecto al no existir en el objeto

const { nombre: nombreUsuario } = { nombre: "Ana" }; // renombrar al destructurar

function saludar({ nombre, edad }) {
  return `Hola ${nombre}, tienes ${edad}`;
}
```

---

## Spread y Rest

**Spread (`...`)**: expande un iterable u objeto.

```js
const combinado = [...[1, 2], ...[3, 4]]; // [1, 2, 3, 4]
const copiaArr = [...numeros];

const base = { a: 1, b: 2 };
const extendido = { ...base, c: 3 }; // combina/copia propiedades (shallow)
const sobrescrito = { ...base, a: 99 }; // { a: 99, b: 2 }

Math.max(...[1, 5, 3]); // pasa elementos de un array como argumentos
```

**Rest (`...`)**: agrupa el resto de valores.

```js
function sumar(...numeros) {
  return numeros.reduce((acc, n) => acc + n, 0);
}
sumar(1, 2, 3); // 6

const { a, ...otros } = { a: 1, b: 2, c: 3 }; // otros = { b: 2, c: 3 }
```

---

## Objetos

```js
const usuario = {
  nombre: "Ana",
  edad: 30,
  saludar() {
    return `Hola, soy ${this.nombre}`;
  },
};

usuario.pais = "Colombia"; // crear propiedad
delete usuario.pais; // eliminar propiedad
"nombre" in usuario; // true, comprueba existencia de la clave
```

**Métodos estáticos de `Object`**

```js
Object.keys(usuario); // ['nombre', 'edad', 'saludar']
Object.values(usuario); // ['Ana', 30, ƒ]
Object.entries(usuario); // [['nombre','Ana'], ['edad',30], ...]
Object.fromEntries([["a", 1], ["b", 2]]); // { a: 1, b: 2 }
Object.assign({}, usuario, { edad: 31 }); // combina objetos (shallow)
Object.freeze(usuario); // impide agregar/modificar/eliminar propiedades
Object.isFrozen(usuario); // true
```

**Propiedades calculadas y shorthand**

```js
const clave = "rol";
const admin = {
  [clave]: "admin", // nombre de propiedad dinámico
  nombre, // shorthand: equivale a nombre: nombre
};
```

**Getters y setters**

```js
const circulo = {
  radio: 5,
  get area() {
    return Math.PI * this.radio ** 2;
  },
  set area(valor) {
    this.radio = Math.sqrt(valor / Math.PI);
  },
};
circulo.area; // se accede como propiedad, no como método
```

---

## Funciones

```js
function saludar(nombre) {
  return `Hola ${nombre}`;
}

const restar = function (a, b) {
  return a - b;
}; // función anónima asignada a variable

const multiplicar = (a, b) => a * b; // arrow function, return implícito
const cuadrado = (n) => {
  return n * n;
}; // arrow function con bloque, return explícito
```

**Parámetros por defecto y rest**

```js
function crearUsuario(nombre, rol = "invitado") {
  return { nombre, rol };
}

function log(...args) {
  console.log(args); // agrupa argumentos extra en un array
}
```

**Callbacks y funciones de orden superior**

```js
function procesar(valor, callback) {
  return callback(valor);
}
procesar(5, (n) => n * 2); // 10

function crearSaludo(mensaje) {
  return function (nombre) {
    return `${mensaje} ${nombre}`;
  }; // función que retorna otra función
}
const hola = crearSaludo("Hola");
hola("Juan"); // 'Hola Juan'
```

**Funciones puras vs impuras**

```js
function suma(a, b) {
  return a + b; // pura: mismo resultado, sin efectos secundarios
}

let total = 0;
function agregar(x) {
  total += x; // impura: modifica estado externo
}
```

> Las arrow functions no tienen su propio `this`, `arguments` ni pueden usarse con `new`.

---

## Scope y Closures

```js
const global = "visible en todo el archivo";

function ejemplo() {
  var funcion = "scope de función"; // var
  if (true) {
    let bloque = "scope de bloque"; // let/const
  }
}
```

El **scope léxico** se define por dónde se escribe el código, no por dónde se ejecuta:

```js
function exterior() {
  const y = 20;
  function interior() {
    console.log(y); // accede a y por el ámbito léxico
  }
  interior();
}
```

Un **closure** ocurre cuando una función recuerda el scope donde fue creada, incluso fuera de él:

```js
function contador() {
  let count = 0;
  return function () {
    count++;
    return count;
  };
}

const inc = contador();
inc(); // 1
inc(); // 2, count persiste entre llamadas
```

Usos comunes: encapsulación, estado privado, funciones factory.

---

## `this`

`this` depende de **cómo se invoca** la función, no de dónde se define.

```js
const usuario = {
  nombre: "Ana",
  saludar() {
    return this.nombre; // this -> usuario, porque se invoca como usuario.saludar()
  },
};

function Persona(nombre) {
  this.nombre = nombre; // this -> nueva instancia, con 'new'
}

const saludarArrow = () => this; // arrow functions no rebinden this, toman el del contexto léxico
```

```js
const fn = usuario.saludar;
fn(); // this -> undefined (o global en modo no estricto), se pierde el contexto

fn.call(usuario); // fuerza this explícitamente
fn.apply(usuario); // igual que call, pero args como array
const fnLigada = fn.bind(usuario); // retorna una nueva función con this fijo
```

---

## Clases

```js
class Persona {
  #dni; // campo privado, solo accesible dentro de la clase

  static especie = "Homo sapiens"; // propiedad estática, compartida por la clase

  constructor(nombre, edad) {
    this.nombre = nombre;
    this.edad = edad;
    this.#dni = null;
  }

  saludar() {
    return `Hola, soy ${this.nombre}`;
  }

  get esAdulto() {
    return this.edad >= 18;
  } // getter

  set dni(valor) {
    this.#dni = valor;
  } // setter

  static crearAnonimo() {
    return new Persona("Anónimo", 0);
  } // método estático, se llama en la clase, no en instancias
}

class Estudiante extends Persona {
  constructor(nombre, edad, carrera) {
    super(nombre, edad); // llama al constructor padre
    this.carrera = carrera;
  }

  saludar() {
    return `${super.saludar()}, estudio ${this.carrera}`; // sobrescribe y reutiliza el padre
  }
}

const ana = new Estudiante("Ana", 22, "Ingeniería");
ana.saludar(); // 'Hola, soy Ana, estudio Ingeniería'
ana instanceof Persona; // true
```

- Las clases son azúcar sintáctica sobre el sistema de **prototipos**: los métodos viven en `Clase.prototype`, compartidos por todas las instancias.
- Los campos `#privados` solo son accesibles dentro del cuerpo de la clase.

---

## Manejo de errores

```js
try {
  JSON.parse("{ inválido");
} catch (error) {
  console.error(error.message);
} finally {
  console.log("Se ejecuta siempre, haya error o no");
}
```

```js
function dividir(a, b) {
  if (b === 0) throw new Error("No se puede dividir entre cero");
  return a / b;
}
```

**Errores personalizados**

```js
class ValidationError extends Error {
  constructor(mensaje) {
    super(mensaje);
    this.name = "ValidationError";
  }
}

try {
  throw new ValidationError("Campo requerido");
} catch (error) {
  if (error instanceof ValidationError) {
    console.error(error.name, error.message);
  }
}
```

---

## JSON

```js
const obj = { nombre: "Ana", activo: true };

JSON.stringify(obj); // '{"nombre":"Ana","activo":true}'
JSON.stringify(obj, null, 2); // formateado con indentación de 2 espacios

JSON.parse('{"nombre":"Ana"}'); // { nombre: 'Ana' }
```

---

## `Map` y `Set`

`Map`: pares clave–valor, admite **cualquier tipo** de clave (a diferencia de los objetos).

```js
const mapa = new Map();
mapa.set("a", 1);
mapa.set({ id: 1 }, "objeto como clave");

mapa.get("a"); // 1
mapa.has("a"); // true
mapa.delete("a");
mapa.size; // tamaño actual

for (const [clave, valor] of mapa) {
  console.log(clave, valor);
}
```

`Set`: colección de **valores únicos**.

```js
const set = new Set([1, 2, 2, 3]); // {1, 2, 3}, elimina duplicados
set.add(4);
set.has(2); // true
set.delete(1);
[...set]; // convertir a array
```

---

## Iteradores y Generadores

Un objeto es **iterable** si implementa `Symbol.iterator` (arrays, strings, `Map`, `Set` lo son por defecto).

```js
function* contador() {
  yield 1;
  yield 2;
  yield 3;
}

const gen = contador();
gen.next(); // { value: 1, done: false }
gen.next(); // { value: 2, done: false }

for (const n of contador()) {
  console.log(n); // 1 2 3, un generador es iterable
}

[...contador()]; // [1, 2, 3]
```

---

## Fechas (`Date`)

```js
const ahora = new Date();
const fecha = new Date("2025-12-15");
const especifica = new Date(2025, 11, 15); // año, mes (0-indexado), día

fecha.getFullYear(); // 2025
fecha.getMonth(); // 11 (diciembre)
fecha.getDate(); // 15
fecha.getDay(); // día de la semana (0 = domingo)
fecha.toISOString(); // '2025-12-15T00:00:00.000Z'

Date.now(); // timestamp actual en milisegundos
```

---

## Expresiones regulares

```js
const patron = /^[A-Za-z]+$/; // literal
const dinamico = new RegExp("^\\d{3}$"); // desde string

patron.test("Hola"); // true
"Hola Mundo".match(/o/g); // ['o', 'o'], todas las coincidencias
"Hola Mundo".replace(/o/g, "0"); // 'H0la Mund0'

/(\w+)@(\w+)\.com/.exec("ana@mail.com"); // captura de grupos
```

Flags comunes: `g` (global), `i` (case-insensitive), `m` (multilínea).

---

## Modelo de ejecución (Call Stack, Event Loop)

JavaScript es **single-thread**: ejecuta código sincrónico en el **Call Stack** (LIFO) y delega tareas asíncronas (timers, fetch, eventos) a las **Web APIs** del entorno.

```js
console.log("1");
setTimeout(() => console.log("2"), 0); // va a la Task Queue
Promise.resolve().then(() => console.log("3")); // va a la Microtask Queue
console.log("4");
// orden real: 1, 4, 3, 2
```

- El **Event Loop** mueve tareas de las colas al Call Stack solo cuando este está vacío.
- Las **microtareas** (promesas) siempre se procesan antes que las **macrotareas** (`setTimeout`, eventos).

```js
setTimeout(() => console.log("Después"), 1000); // no garantiza el tiempo exacto
```

---

## Promesas

Representan el resultado, eventual, de una operación asíncrona.

```js
const promesa = new Promise((resolve, reject) => {
  const ok = true;
  if (ok) resolve("Éxito");
  else reject(new Error("Falló"));
});

promesa
  .then((res) => console.log(res))
  .catch((err) => console.error(err))
  .finally(() => console.log("Terminó"));
```

Estados: **pending** (inicial) → **fulfilled** (resuelta) o **rejected** (rechazada).

```js
Promise.all([fetch("/a"), fetch("/b")]); // paralelo, falla si una falla
Promise.allSettled([p1, p2]); // espera todas, sin importar si fallan
Promise.race([p1, p2]); // resuelve/rechaza con la primera que termine
```

---

## Async / Await

Sintaxis sobre promesas, más legible que encadenar `.then()`.

```js
async function obtenerDatos() {
  const res = await fetch("/api");
  const data = await res.json();
  return data; // una función async siempre retorna una Promise
}

async function cargar() {
  try {
    const data = await obtenerDatos();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}
```

```js
for await (const valor of iterableAsync) {
  console.log(valor); // itera promesas de forma secuencial
}
```

---

## Módulos (`import` / `export`)

```js
// math.js
export const PI = 3.1416;
export function sumar(a, b) {
  return a + b;
}
export default function multiplicar(a, b) {
  return a * b;
} // un único export default por módulo
```

```js
// app.js
import multiplicar, { PI, sumar } from "./math.js";
import * as math from "./math.js"; // importa todo como namespace
```

```html
<script type="module" src="app.js"></script>
```

- Los módulos tienen su propio scope y se ejecutan en **modo estricto** por defecto.
- Las rutas relativas requieren extensión explícita (`./math.js`) en el navegador.

---

## DOM: selección y manipulación

```js
const titulo = document.querySelector("h1"); // primer elemento que coincide
const items = document.querySelectorAll(".item"); // NodeList de todos los que coinciden

items.forEach((item) => console.log(item.textContent));
```

```js
const p = document.createElement("p");
p.textContent = "Nuevo párrafo";
document.querySelector("#app").appendChild(p);
p.remove();
```

```js
element.textContent = "Texto plano";
element.innerHTML = "<strong>Texto</strong>"; // cuidado con XSS

img.setAttribute("src", "foto.jpg");
img.getAttribute("alt");
img.removeAttribute("title");

element.classList.add("activo");
element.classList.remove("oculto");
element.classList.toggle("open");
element.classList.contains("open");

element.style.color = "red"; // preferir clases CSS a estilos en línea
```

---

## Eventos del DOM

```js
const btn = document.querySelector("button");

btn.addEventListener("click", (event) => {
  event.preventDefault();
  console.log("Click");
});

function handler() {
  console.log("click");
}
btn.addEventListener("click", handler);
btn.removeEventListener("click", handler);
```

Eventos comunes: `click`, `submit`, `input`, `change`, `keydown`, `keyup`, `mouseover`, `load`.

---

## Formularios en el DOM

```js
const form = document.querySelector("form");

form.addEventListener("submit", (e) => {
  e.preventDefault();
  const data = new FormData(form);
  data.get("email"); // valor de un campo por su name
});
```

---

## HTTP y Fetch API

```js
fetch("/api/users"); // GET por defecto
fetch("/api/users", { method: "POST" }); // POST: crear
fetch("/api/users/1", { method: "PUT" }); // PUT: reemplaza el recurso completo
fetch("/api/users/1", { method: "PATCH" }); // PATCH: actualización parcial
fetch("/api/users/1", { method: "DELETE" });
```

```js
fetch("/api/users", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ name: "Ana", age: 25 }),
})
  .then((res) => {
    if (!res.ok) throw new Error(`Error HTTP ${res.status}`);
    return res.json();
  })
  .then((data) => console.log(data))
  .catch((err) => console.error(err));
```

```js
async function cargarUsuarios() {
  try {
    const res = await fetch("/api/users");
    if (!res.ok) throw new Error(`Error HTTP ${res.status}`);
    return await res.json();
  } catch (error) {
    console.error(error);
  }
}
```

Tipos de contenido comunes: `application/json`, `application/x-www-form-urlencoded`, `multipart/form-data`, `text/plain`.
