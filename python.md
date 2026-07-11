## Guía Rápida de Python

Colección de recordatorios y fragmentos de código orientados a quienes ya
exploraron los conceptos básicos y quieren revisar la sintaxis con ejemplos
breves. Todas las secciones siguen un estilo de "receta": título corto, contexto
concreto y snippet listo para copiar.

> Versión: Python 3.12+ · Actualizado: 2026-07-10

## Tabla de contenidos

- [Comentarios](#comentarios)
- [Tipos y conversión](#tipos-y-conversión)
- [Operadores numéricos](#operadores-numéricos)
- [Operadores de asignación](#operadores-de-asignación)
- [Operadores de comparación](#operadores-de-comparación)
- [Operadores lógicos](#operadores-lógicos)
- [Operadores de identidad](#operadores-de-identidad)
- [Operadores de pertenencia](#operadores-de-pertenencia)
- [Operador condicional (ternario)](#operador-condicional-ternario)
- [Estructuras condicionales](#estructuras-condicionales)
- [Estructuras iterativas](#estructuras-iterativas)
- [Range](#range)
- [Cláusulas en Loops](#cláusulas-en-loops)
- [pass](#pass)
- [match](#match)
- [Texto](#texto)
- [Listas](#listas)
- [Tuplas](#tuplas)
- [Conjuntos](#conjuntos)
- [Diccionarios](#diccionarios)
- [Funciones](#funciones)
- [Decoradores](#decoradores)
- [Generadores](#generadores)
- [Iteradores](#iteradores)
- [Módulos](#módulos)
- [Módulos Estándar de Python](#módulos-estándar-de-python)
- [La función dir()](#la-función-dir)
- [Paquetes](#paquetes)
- [Clases](#clases)
- [Herencia Múltiple](#herencia-múltiple)
- [Clases abstractas](#clases-abstractas)
- [Enum](#enum)
- [Type hints](#type-hints)
- [Formatos de salida](#formatos-de-salida)
- [Métodos de Objetos de Archivo](#métodos-de-objetos-de-archivo)
- [Administradores de contexto personalizados](#administradores-de-contexto-personalizados)
- [Excepciones](#excepciones)
- [Docstrings](#docstrings)
- [Estilo de codificación](#estilo-de-codificación)
- [Uso de la librería estándar](#uso-de-la-librería-estándar)
- [Entornos virtuales](#entornos-virtuales)

---

## Comentarios

```python
# Soy un comentario
```

---

## Tipos y conversión

- **Tipos básicos**

```python
type(1)      # <class 'int'>
type(1.5)    # <class 'float'>
type('a')    # <class 'str'>
type(True)   # <class 'bool'>
type(None)   # <class 'NoneType'>
type([1])    # <class 'list'>
```

- **Conversión explícita**

```python
int('42')      # 42
int(3.9)       # 3 (trunca)
float('3.14')  # 3.14
str(42)        # '42'
bool(0)        # False
bool('')       # False
bool('texto')  # True
list('abc')    # ['a', 'b', 'c']
```

- **Comprobar el tipo**

```python
isinstance(1, int)        # True
isinstance(1, (int, float))  # True
```

---

## Operadores numéricos

- **Suma**

```python
1 + 2 # 3
```

- **Resta**

```python
1 - 2 # -1
```

- **Multiplicación**

```python
2 * 3 # 6
```

- **División**

```python
2 / 3 # 0.6666666666666666
```

- **División entera**

```python
3 // 2 # 1
```

- **Módulo o resto**

```python
9 % 3 # 0
```

- **Potencia**

```python
2 ** 3 # 8
```

- **Módulo y cociente en un único paso**

```python
divmod(9, 4)  # (2, 1)
```

- **Valor absoluto y redondeos**

```python
abs(-3.5)      # 3.5
round(3.1415)  # 3
round(3.1415, 2)  # 3.14
```

---

## Operadores de asignación

- **Asignación**

```python
x = 5  # x ahora es 5
```

- **Suma en asignación**

```python
x = 5
x += 3  # x ahora es 8 (5 + 3)
```

- **Resta en asignación**

```python
x = 5
x -= 2  # x ahora es 3 (5 - 2)
```

- **Multiplicación en asignación**

```python
x = 5
x *= 3  # x ahora es 15 (5 * 3)
```

- **División en asignación**

```python
x = 10
x /= 2  # x ahora es 5 (10 / 2)
```

- **División entera en asignación**

```python
x = 10
x //= 3  # x ahora es 3 (10 // 3)
```

- **Módulo en asignación**

```python
x = 10
x %= 3  # x ahora es 1 (10 % 3)
```

- **Potencia en asignación**

```python
x = 5
x **= 3  # x ahora es 125 (5 ** 3)
```

- **Asignación múltiple y desempaquetado**

```python
a, b, c = 1, 2, 3
a, b = b, a  # intercambio: a = 2, b = 1
primero, *resto = [1, 2, 3, 4]  # primero = 1, resto = [2, 3, 4]
```

- **Operador "walrus" (asignación en expresiones)**

```python
if (n := len([1, 2, 3])) > 2: # asigna y evalúa a la vez
  print(f'La lista tiene {n} elementos') # La lista tiene 3 elementos
```

---

## Operadores de comparación

- **Igual**

```python
1 == 1 # True
```

- **Distinto**

```python
1 != 1 # False
```

- **Menor que**

```python
1 < 2 # True
```

- **Menor o igual que**

```python
1 <= 2 # True
```

- **Mayor que**

```python
1 > 2 # False
```

- **Mayor o igual que**

```python
1 >= 2 # False
```

- **Comparaciones encadenadas**

```python
1 < 2 < 3  # True, equivale a (1 < 2) and (2 < 3)
```

---

## Operadores lógicos

- **And**

```python
True and True # True
```

- **Or**

```python
True or False # True
```

- **Not**

```python
not False # True
```

> Cualquier objeto puede evaluarse como verdadero/falso. Por ejemplo, listas
> vacías, `0` y `None` se consideran false; el resto es truthy.

---

## Operadores de identidad

- **is**

```python
1 is 1 # True
```

- **is not**

```python
1 is not 1 # False
```

> Usa `is`/`is not` para comparar identidades de objetos (misma posición en
> memoria). Para comparar valores escalares como números o cadenas, prefiere
> `==`/`!=`, ya que la interning de objetos pequeños puede hacer que `is`
> devuelva resultados engañosos.

---

## Operadores de pertenencia

- **in**

```python
1 in [1, 2, 3] # True
```

- **not in**

```python
1 not in [1, 2, 3] # False
```

---

## Operador condicional (ternario)

```python
edad = 20
estado = 'mayor' if edad >= 18 else 'menor'  # 'mayor'
```

---

## Estructuras condicionales

- **if**

```python
if 1 == 1:
  print('1 es igual a 1')
# 1 es igual a 1
```

- **if-else**

```python
if 1 != 1:
  print('1 es distinto de 1')
else:
  print('1 es igual a 1')
# 1 es igual a 1
```

- **if-elif-else**

```python
if 1 > 1:
  print('1 es mayor que 1')
elif 1 < 1:
  print('1 es menor que 1')
else:
  print('1 es igual a 1')
# 1 es igual a 1
```

---

## Estructuras iterativas

- **while**

```python
x = 1
while x < 5:
  print(x)
  x += 1
# 1 2 3 4
```

- **for**

```python
for x in [1, 2, 3]:
  print(x)
# 1 2 3
```

---

## Range

```python
for i in range(5):
  print(i)
# 0 1 2 3 4
```

Rangos también aceptan inicio y paso personalizados:

```python
for i in range(2, 10, 2):
  print(i)
# 2 4 6 8
```

---

## Cláusulas en Loops

- **break**

```python
for i in range(5):
  if i == 3:
    break
  print(i)
# 0 1 2
```

- **continue**

```python
for i in range(5):
  if i == 3:
    continue
  print(i)
# 0 1 2 4
```

- **else en loops**

Se ejecuta cuando el bucle termina sin `break`.

```python
for i in range(5):
  if i == 10:
    break
else:
  print('El bucle terminó sin interrupciones')
# El bucle terminó sin interrupciones
```

---

## pass

Marcador de posición para código que aún no has escrito.
Permite a los desarrolladores crear esqueletos de código que pueden ser completados más tarde, manteniendo la estructura del programa clara y sin errores de sintaxis.

- **Estructuras condicionales**

```python
if condicion:
    pass  # Implementar más tarde
else:
    ejecutar_algo()
```

- **En Funciones o Clases Vacías**

```python
def mi_funcion():
    pass

class MiClase:
    pass
```

- **En Bucles**

```python
for elemento in mi_lista:
    pass  # Implementación futura
```

---

## match

> Disponible desde Python 3.10. Facilita el "pattern matching" estructural.

- **Estructura**

```python
def describir_tipo(objeto):
    match objeto:
        case int():
            return "Es un entero"
        case str():
            return "Es una cadena de texto"
        case list():
            return "Es una lista"
        case _:
            return "Tipo no identificado"
```

- **Desempaquetado de Secuencias**

```python
punto = (1, 2)
match punto:
    case (0, 0):
        print("Origen")
    case (x, 0):
        print(f"Sobre el eje X en {x}")
    case (0, y):
        print(f"Sobre el eje Y en {y}")
    case (x, y):
        print(f"En la posición ({x}, {y})")
    case _:
        raise ValueError("No es un punto válido")
```

- **Comprobación de Tipos y Guardas**

```python
match objeto:
    case str() if objeto.isnumeric():
        print("Es una cadena numérica")
    case str():
        print("Es una cadena de texto")
    case int() | float():
        print("Es un número")
    case _:
        print("Tipo no identificado")
```

- **Coincidencia con diccionarios**

```python
comando = {"tipo": "mover", "x": 10, "y": 5}

match comando:
    case {"tipo": "mover", "x": x, "y": y}:
        print(f"Moviendo a ({x}, {y})")
    case {"tipo": "esperar", "segundos": s} if s > 0:
        print(f"Esperando {s} segundos")
    case _:
        raise ValueError("Comando no soportado")
```

---

## Texto

- **Creación de una cadena de caracteres**

```python
s1 = 'Hola, mundo!'
s2 = "Python es genial"
```

- **Concatenación**

```python
saludo = 'Hola' + ' ' + 'Mundo' # Hola mundo
```

- **Interpolación**

```python
nombre = 'Juan'
saludo = f'Hola {nombre}' # Hola Juan
```

- **Repetición**

```python
repeticion = 'Hola' * 3 + 'Mundo' # HolaHolaHola Mundo
```

- **Acceso a un caracter o subcadena**

```python
cadena = "Python"
caracter = cadena[0] # 'P'
subcadena = cadena[1:4] # 'yth'
```

- **Slicing con paso**

```python
cadena = "Python"
cadena[::2]   # 'Pto'
cadena[::-1]  # 'nohtyP' (invertir)
```

- **Cadena multilinea**

```python
multilinea = """Línea 1
Línea 2
Línea 3"""
# Línea 1
# Línea 2
# Línea 3
```

- **Caracteres especiales**

```python
cadena_con_salto_de_linea = "Línea 1\nLínea 2"
# Línea 1
# Línea 2
cadena_con_tabulacion = "Columna 1\tColumna 2" # Columna 1  Columna 2
```

- **Raw string**

```python
cadena = r'C:\Users\Juan\Documents'
```

### Operaciones básicas de cadenas

```python
cadena = "Python"
```

- **Longitud**

```python
len(cadena) # 6
```

- **Capitalizar**

```python
cadena.upper() # 'PYTHON'
```

- **Minuscular**

```python
cadena.lower() # 'python'
```

- **Empieza por**

```python
cadena.startswith('P') # True
```

- **Termina por**

```python
cadena.endswith('n') # True
```

- **Reemplazar**

```python
cadena.replace('P', 'J') # 'Jython'
```

- **Partir**

```python
cadena.split('t') # ['Py', 'hon']
```

- **Buscar**

```python
cadena.find('t') # 2
cadena.find('w') # -1
```

- **Contar**

```python
cadena.count('t') # 1
```

- **Comprobar si es alfanumérica**

```python
cadena.isalnum() # False
```

- **Comprobar si es alfabética**

```python
cadena.isalpha() # True
```

- **Buscar el índice de un caracter**

```python
cadena.index('P') # 0
cadena.index('w') # ValueError
```

- **Eliminar espacios en blanco al inicio y final**

```python
"  hola  ".strip()   # 'hola'
"__hola__".strip('_')  # 'hola'
```

- **Unir elementos iterables**

```python
"-".join(["2024", "05", "01"])  # '2024-05-01'
```

- **Separar en tuplas usando el primer separador**

```python
"usuario:123".partition(":")  # ('usuario', ':', '123')
```

---

## Listas

### Creación de listas

- **Con corchetes**

```python
lista1 = []
lista2 = [1, 2, 3]
```

- **Con el constructor**

```python
lista3 = list()
```

### Acceso a Elementos

- **Acceder a un elemento**

```python
lista = [1, 2, 3]
lista[0] # 1
```

- **Acceder al último elemento (indice negativo)**

```python
lista = [1, 2, 3]
lista[-1] # 3
```

- **Acceder a varios elementos**

```python
lista = [1, 2, 3, 4, 5]
lista[1:3] # [2, 3]
```

### Modificación de Listas

- **Modificar un elemento**

```python
lista = [1, 2, 3]
lista[0] = 4 # [4, 2, 3]
```

- **Agregar un elemento al final**

```python
lista = [1, 2, 3]
lista.append(4) # [1, 2, 3, 4]
```

- **Agregar varios elementos al final**

```python
lista = [1, 2, 3]
lista.extend([4, 5]) # [1, 2, 3, 4, 5]
```

- **Agregar un elemento en una posición específica**

```python
lista = [1, 2, 3]
lista.insert(1, 4) # [1, 4, 2, 3]
```

- **Unir 2 listas**

```python
lista = [1, 2, 3]
lista2 = [4, 5, 6]
lista3 = lista + lista2 # [1, 2, 3, 4, 5, 6]
```

### Eliminación de Elementos

- **Eliminar un Elemento por su Índice**

```python
lista = [1, 2, 3]
del lista[0] # [2, 3]
```

- **Eliminar un Elemento por su Valor**

```python
lista = [1, 2, 3]
lista.remove(1) # [2, 3]
```

- **Eliminar y Devolver su valor (por su índice)**

```python
lista = [1, 2, 3]
lista.pop(1) # 2
# lista = [1, 3]
```

- **Vaciar Toda la Lista**

```python
lista = [1, 2, 3]
lista.clear() # []
```

### Operaciones básicas

- **Longitud de la Lista**

```python
lista = [1, 2, 3]
len(lista) # 3
```

- **Máximo**

```python
max([1, 2, 3]) # 3
```

- **Mínimo**

```python
min([1, 2, 3]) # 1
```

- **Suma**

```python
sum([1, 2, 3]) # 6
```

- **Ordenar la Lista**

```python
lista = [3, 2, 1]
lista.sort() # [1, 2, 3]
lista.sort(reverse=True) # [3, 2, 1]
```

- **sorted() con clave personalizada**

```python
personas = [('Ana', 30), ('Luis', 25)]
sorted(personas, key=lambda p: p[1])  # [('Luis', 25), ('Ana', 30)]
```

- **Invertir la lista**

```python
lista = [1, 2, 3]
lista.reverse() # [3, 2, 1]
list(reversed(lista))  # nuevo iterable invertido, no muta la lista
```

- **Contar la Ocurrencia de un Elemento**

```python
lista = [1, 2, 3, 1, 1]
lista.count(1) # 3
```

- **Obtener el Índice de un Elemento**

```python
lista = [1, 2, 3]
lista.index(2) # 1
```

- **Copiar una Lista**

```python
lista = [1, 2, 3]
lista2 = lista.copy() # [1, 2, 3]
```

### Comprensiones y utilidades

- **Comprensión básica**

```python
[n * 2 for n in range(5)]  # [0, 2, 4, 6, 8]
```

- **Comprensión con condición**

```python
[n for n in range(10) if n % 2 == 0]  # [0, 2, 4, 6, 8]
```

- **Comprensión anidada**

```python
[[f'{i}{j}' for j in range(2)] for i in range(2)]
# [['00', '01'], ['10', '11']]
```

- **Enumerar elementos**

```python
for indice, valor in enumerate(['a', 'b']):
  print(indice, valor)
# 0 a
# 1 b
```

- **Combinar listas con zip**

```python
for nombre, edad in zip(['Ana', 'Luis'], [30, 25]):
  print(f'{nombre} tiene {edad} años')
```

- **map, filter y reduce**

```python
list(map(str.upper, ['a', 'b']))      # ['A', 'B']
list(filter(lambda n: n > 1, [1, 2, 3]))  # [2, 3]

from functools import reduce
reduce(lambda acc, n: acc + n, [1, 2, 3], 0)  # 6
```

- **any() y all()**

```python
any([False, True, False])  # True
all([True, True, False])   # False
```

---

## Tuplas

Colecciones inmutables y ordenadas; ideales para representar registros fijos.

### Creación de tuplas

- **Con paréntesis**

```python
tupla1 = ()
tupla2 = (1, 2, 3)
```

- **Con el constructor**

```python
tupla3 = tuple()
```

### Acceso a elementos

- **Acceder a un elemento**

```python
tupla = (1, 2, 3)
tupla[0] # 1
```

- **Acceder al último elemento (índice negativo)**

```python
tupla = (1, 2, 3)
tupla[-1] # 3
```

- **Acceder a varios elementos**

```python
tupla = (1, 2, 3, 4, 5)
tupla[1:3] # (2, 3)
```

### Operaciones básicas

- **Longitud de la tupla**

```python
tupla = (1, 2, 3)
len(tupla) # 3
```

- **Máximo**

```python
max((1, 2, 3)) # 3
```

- **Mínimo**

```python
min((1, 2, 3)) # 1
```

- **Suma**

```python
sum((1, 2, 3)) # 6
```

- **Contar la ocurrencia de un elemento**

```python
tupla = (1, 2, 3, 1, 1)
tupla.count(1) # 3
```

- **Obtener el índice de un elemento**

```python
tupla = (1, 2, 3)
tupla.index(2) # 1
```

### Conversión de tuplas

- **A lista**

```python
tupla = (1, 2, 3)
lista = list(tupla) # [1, 2, 3]
```

- **A tupla**

```python
lista = [1, 2, 3]
tupla = tuple(lista) # (1, 2, 3)
```

- **Desempaquetado**

```python
punto = (10, 20)
x, y = punto  # x = 10, y = 20

def extremos():
    return 1, 99  # retorna una tupla
```

- **namedtuple**

```python
from collections import namedtuple

Punto = namedtuple('Punto', ['x', 'y'])
p = Punto(1, 2)
p.x, p.y  # (1, 2)
```

---

## Conjuntos

### Creación de conjuntos

- **Con llaves**

```python
conjunto1 = {1, 2, 3}
```

- **Con el constructor**

```python
conjunto2 = set()
```

- **Comprensión de conjuntos**

```python
{n % 3 for n in range(6)}  # {0, 1, 2}
```

### Añadir Elementos

- **Añadir un elemento**

```python
conjunto = {1, 2, 3}
conjunto.add(4) # {1, 2, 3, 4}
```

- **Añadir varios elementos**

```python
conjunto = {1, 2, 3}
conjunto.update([4, 5, 6]) # {1, 2, 3, 4, 5, 6}
```

### Eliminación de Elementos

- **Eliminar un elemento**

```python
conjunto = {1, 2, 3}
conjunto.remove(1) # {2, 3}
```

- **Eliminar y devolver su valor**

```python
conjunto = {1, 2, 3}
conjunto.pop() # 1
# conjunto = {2, 3}
```

- **Eliminar un elemento sin error**

```python
conjunto = {1, 2, 3}
conjunto.discard(1) # {2, 3}
```

- **Vaciar todo el conjunto**

```python
conjunto = {1, 2, 3}
conjunto.clear() # set()
```

### Operaciones básicas

- **Longitud del conjunto**

```python
conjunto = {1, 2, 3}
len(conjunto) # 3
```

- **Comprobar si un elemento está en el conjunto**

```python
conjunto = {1, 2, 3}
1 in conjunto # True
```

- **Comprobar si un elemento no está en el conjunto**

```python
conjunto = {1, 2, 3}
1 not in conjunto # False
```

- **Unión de conjuntos**

```python
conjunto1 = {1, 2, 3}
conjunto2 = {3, 4, 5}
conjunto1 | conjunto2 # {1, 2, 3, 4, 5}
```

- **Intersección de conjuntos**

```python
conjunto1 = {1, 2, 3}
conjunto2 = {3, 4, 5}
conjunto1 & conjunto2 # {3}
```

- **Diferencia de conjuntos**

```python
conjunto1 = {1, 2, 3}
conjunto2 = {3, 4, 5}
conjunto1 - conjunto2 # {1, 2}
```

- **Diferencia simétrica de conjuntos**

```python
conjunto1 = {1, 2, 3}
conjunto2 = {3, 4, 5}
conjunto1 ^ conjunto2 # {1, 2, 4, 5}
```

### Comprobaciones con Conjuntos

- **Comprobar si un conjunto es subconjunto de otro**

```python
conjunto1 = {1, 2}
conjunto2 = {1, 2, 3}
conjunto1.issubset(conjunto2) # True
```

- **Comprobar si un conjunto es superconjunto de otro**

```python
conjunto1 = {1, 2, 3}
conjunto2 = {1, 2}
conjunto1.issuperset(conjunto2) # True
```

- **Comprobar si dos conjuntos son disjuntos**

```python
conjunto1 = {1, 2}
conjunto2 = {3, 4}
conjunto1.isdisjoint(conjunto2) # True
```

- **Actualizar en sitio sin crear nuevos conjuntos**

```python
conjunto = {1, 2, 3}
conjunto.difference_update({2, 3})  # conjunto = {1}
```

- **Conjuntos inmutables**

```python
permisos = frozenset({'lectura', 'escritura'})
# Ideal para usar como clave en diccionarios
```

---

## Diccionarios

- **Con llaves**

```python
diccionario1 = {}
diccionario2 = {'nombre': 'Juan', 'edad': 25}
```

- **Con el constructor**

```python
diccionario3 = dict()
```

### Acceso a elementos

- **Acceder a un elemento**

```python
diccionario = {'nombre': 'Juan', 'edad': 25}
diccionario['nombre'] # 'Juan'
```

- **Acceder a un elemento (get)**

```python
diccionario = {'nombre': 'Juan', 'edad': 25}
diccionario.get('nombre') # 'Juan'
```

- **Acceder a las claves**

```python
diccionario = {'nombre': 'Juan', 'edad': 25}
diccionario.keys() # dict_keys(['nombre', 'edad'])
```

- **Acceder a los valores**

```python
diccionario = {'nombre': 'Juan', 'edad': 25}
diccionario.values() # dict_values(['Juan', 25])
```

- **Acceder clave-valor**

```python
diccionario = {'nombre': 'Juan', 'edad': 25}
diccionario.items() # dict_items([('nombre', 'Juan'), ('edad', 25)])
```

- **Iterar sobre claves y valores**

```python
for clave, valor in diccionario.items():
  print(clave, valor)
```

- **Obtener con valor por defecto**

```python
diccionario.get('altura', 0)  # 0
```

- **Actualizar múltiples claves**

```python
diccionario.update({'nombre': 'Ana', 'pais': 'Perú'})
```

- **Establecer si no existe**

```python
diccionario.setdefault('rol', 'viewer')  # agrega 'rol' si falta
```

- **Eliminar una clave**

```python
diccionario = {'a': 1, 'b': 2}
diccionario.pop('a')  # 1, diccionario = {'b': 2}
del diccionario['b']  # diccionario = {}
```

- **Fusionar diccionarios**

```python
base = {'a': 1}
extra = {'b': 2}
base | extra  # {'a': 1, 'b': 2} (Python 3.9+)
```

- **Comprensión de diccionarios**

```python
cuadrados = {n: n**2 for n in range(3)}  # {0: 0, 1: 1, 2: 4}
```

- **Diccionario con valores por defecto**

```python
from collections import defaultdict

contador = defaultdict(int)
contador['a'] += 1  # 1, sin KeyError aunque 'a' no existiera
```

---

## Funciones

```python
def saludar(nombre):
  print(f'Hola {nombre}')
saludar('Juan') # Hola Juan
```

- **Argumentos**

```python
def saludar(nombre, saludo='Hola'):
  print(f'{saludo} {nombre}')
saludar('Juan') # Hola Juan
saludar('Juan', 'Buenas tardes') # Buenas tardes Juan
```

- **Argumentos indeterminados**

```python
def saludar(*nombres):
  for nombre in nombres:
    print(f'Hola {nombre}')
saludar('Juan', 'Carlos', 'Ricardo')
# Hola Juan
# Hola Carlos
# Hola Ricardo
```

- **Argumentos con nombre**

```python
def saludar(**kwargs):
  print(f'Hola {kwargs["nombre"]}')
saludar(nombre='Juan') # Hola Juan
```

- **Desempaquetar argumentos al llamar**

```python
def sumar(a, b, c):
  return a + b + c

valores = [1, 2, 3]
sumar(*valores)  # 6

datos = {'a': 1, 'b': 2, 'c': 3}
sumar(**datos)  # 6
```

- **Parámetros solo-posicionales y solo-nombrados**

```python
def funcion(pos_solo, /, normal, *, kw_solo):
  return (pos_solo, normal, kw_solo)

funcion(1, 2, kw_solo=3)      # (1, 2, 3)
funcion(1, normal=2, kw_solo=3)  # (1, 2, 3)
```

- **Retorno de valores**

```python
def sumar(a, b):
  return a + b
resultado = sumar(2, 3) # 5
```

- **Funciones anónimas**

```python
sumar = lambda a, b: a + b
resultado = sumar(2, 3) # 5
```

- **Función Anotada**

```python
def suma(a: int, b: int) -> int:
    """Suma dos números enteros."""
    return a + b
```

- **Funciones de orden superior**

```python
from typing import Callable

def operar(a: int, b: int, funcion: Callable[[int, int], int]) -> int:
    return funcion(a, b)

operar(2, 3, lambda x, y: x * y)  # 6
```

- **Closures y `nonlocal`**

```python
def contador():
  n = 0
  def incrementar():
    nonlocal n
    n += 1
    return n
  return incrementar

siguiente = contador()
siguiente()  # 1
siguiente()  # 2
```

- **`global` dentro de una función**

```python
total = 0

def acumular(valor):
  global total
  total += valor

acumular(5)  # total ahora es 5
```

---

## Decoradores

Envuelven una función para extender su comportamiento sin modificar su código.

- **Decorador básico**

```python
def con_log(func):
    def envoltorio(*args, **kwargs):
        print(f'Llamando a {func.__name__}')
        return func(*args, **kwargs)
    return envoltorio

@con_log
def saludar(nombre):
    print(f'Hola {nombre}')

saludar('Juan')
# Llamando a saludar
# Hola Juan
```

- **Preservar metadatos con `functools.wraps`**

```python
from functools import wraps

def con_log(func):
    @wraps(func)
    def envoltorio(*args, **kwargs):
        return func(*args, **kwargs)
    return envoltorio
```

- **Decorador con argumentos propios**

```python
def repetir(veces):
    def decorador(func):
        def envoltorio(*args, **kwargs):
            for _ in range(veces):
                func(*args, **kwargs)
        return envoltorio
    return decorador

@repetir(2)
def saludar():
    print('Hola')
# Hola
# Hola
```

- **`functools.lru_cache` para memoización**

```python
from functools import lru_cache

@lru_cache(maxsize=None)
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)
```

---

## Generadores

Funciones que producen valores de forma perezosa usando `yield`, sin construir
toda la secuencia en memoria.

- **Función generadora**

```python
def contar_hasta(n):
    i = 1
    while i <= n:
        yield i
        i += 1

for numero in contar_hasta(3):
    print(numero)
# 1 2 3
```

- **`yield from` para delegar en otro iterable**

```python
def combinar(a, b):
    yield from a
    yield from b

list(combinar([1, 2], [3, 4]))  # [1, 2, 3, 4]
```

- **Expresión generadora**

```python
cuadrados = (n ** 2 for n in range(5))
next(cuadrados)  # 0
list(cuadrados)  # [1, 4, 9, 16] (0 ya se consumió)
```

- **Enviar valores a un generador**

```python
def eco():
    while True:
        recibido = yield
        print(f'Recibido: {recibido}')

gen = eco()
next(gen)        # avanza hasta el primer yield
gen.send('hola') # Recibido: hola
```

---

## Iteradores

Todo objeto iterable implementa `__iter__`; un iterador implementa además
`__next__`.

```python
class Contador:
    def __init__(self, limite):
        self.limite = limite
        self.actual = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.actual >= self.limite:
            raise StopIteration
        self.actual += 1
        return self.actual

for numero in Contador(3):
    print(numero)
# 1 2 3
```

- **Uso manual con `iter()` y `next()`**

```python
it = iter([1, 2, 3])
next(it)  # 1
next(it)  # 2
next(it)  # 3
next(it)  # StopIteration
```

---

## Módulos

- **Creación de un módulo**

```python
# modulo.py
def saludar():
  print('Hola, soy un módulo')

if __name__ == '__main__':
  saludar()
```

- **Importación de un módulo**

```python
import modulo
modulo.saludar() # Hola, soy un módulo
```

- **Importación de un módulo con un alias**

```python
import modulo as md
md.saludar() # Hola, soy un módulo
```

- **Importación selectiva con `from`**

```python
from modulo import saludar
saludar() # Hola, soy un módulo
```

- **Importación de objetos múltiples**

```python
from modulo import saludar, despedir
```

- **Evitar imports globales de comodín**

```python
from modulo import *  # solo para sesiones interactivas o ejemplos rápidos
```

- **Alias para elementos importados**

```python
from modulo import funcion_costosa as fc
```

- **Controlar qué se exporta con `__all__`**

```python
# modulo.py
__all__ = ['saludar']
```

---

## Módulos Estándar de Python

Python viene con una biblioteca estándar que ofrece muchos módulos útiles. Algunos de los módulos estándar más utilizados incluyen:

- math: Funciones matemáticas.
- os: Interacción con el sistema operativo.
- sys: Acceso a variables y funciones relacionadas con Python.
- datetime: Manipulación de fechas y horas.
- json: Manipulación de datos JSON.
- random: Generación de números aleatorios.
- pathlib: Manipulación de rutas de archivo orientada a objetos.
- collections: Estructuras adicionales (deque, Counter, defaultdict, etc.).
- itertools: Herramientas para trabajar con iteradores infinitos o combinatorios.
- functools: Herramientas para programación funcional (reduce, lru_cache, wraps).
- re: Expresiones regulares.
- logging: Registro de eventos y mensajes de diagnóstico.

- **json: serializar y deserializar**

```python
import json

datos = {'nombre': 'Ana', 'edad': 30}
texto = json.dumps(datos)  # '{"nombre": "Ana", "edad": 30}'
json.loads(texto)  # {'nombre': 'Ana', 'edad': 30}
```

- **re: expresiones regulares**

```python
import re

re.match(r'\d+', '123abc')          # coincide '123'
re.findall(r'\d+', 'a1 b22 c333')   # ['1', '22', '333']
re.sub(r'\s+', ' ', 'a   b   c')    # 'a b c'
```

- **datetime: fechas y horas**

```python
from datetime import datetime, timedelta

ahora = datetime.now()
manana = ahora + timedelta(days=1)
ahora.strftime('%Y-%m-%d')  # '2026-07-10'
```

> Consejo: agrupa importaciones estándar al inicio del archivo y revisa la
> documentación oficial para descubrir utilidades menos conocidas como `statistics`
> o `itertools`.

---

## La función dir()

- La función dir() en Python es una herramienta poderosa que proporciona una lista de los nombres definidos en un espacio de nombres. Cuando se usa sin argumentos, dir() devuelve una lista de nombres en el alcance local actual. Si se le pasa un objeto como argumento, devuelve una lista de los nombres válidos para ese objeto.

### Uso Básico de dir()

- **Sin Argumentos**
  Al usar dir() sin argumentos, obtienes una lista de nombres definidos en el espacio de nombres local actual.

```python
a = 5
b = "Hola Mundo"
print(dir())
# Esto mostrará todos los nombres definidos en tu espacio de nombres actual, incluyendo variables, funciones y módulos importados.
```

- **Con un objeto**
  Al pasarle un objeto, dir() devuelve los atributos del objeto, lo cual incluye métodos y propiedades.

```python
print(dir("Hola Mundo"))
# Aquí se enumeran todos los métodos y propiedades asociados con un objeto de cadena (str).
```

- **Combinado con `vars()`**

```python
class Persona:
    def __init__(self, nombre):
        self.nombre = nombre

p = Persona("Lucía")
print(vars(p))  # {'nombre': 'Lucía'}
```

---

## Paquetes

- **Creación de un paquete**

```python
# paquete/__init__.py
```

- **Importación de un paquete**

```python
import paquete
```

- **Importación de un módulo de un paquete**

```python
from paquete import modulo
```

- **Importación de un módulo de un paquete con un alias**

```python
from paquete import modulo as md
```

- **Importación de todas las funciones de un módulo de un paquete**

```python
from paquete.modulo import *
```

- **Importación selectiva**

```python
from paquete.modulo import saludar, despedir
```

- **Importaciones relativas**

```python
# paquete/subpaquete/operaciones.py
from ..utilidades import limpiar_nombre
```

- **Controlar exportaciones**

```python
# paquete/__init__.py
__all__ = ['modulo']
```

---

## Clases

- **Creación de una clase**

```python
class Persona:
  pass
```

- **Constructor**

```python
class Persona:
  def __init__(self):
    pass
```

- **Atributos**

```python
class Persona:
  def __init__(self, nombre, edad):
    self.nombre = nombre
    self.edad = edad
```

- **Métodos**

```python
class Persona:
  def __init__(self, nombre, edad):
    self.nombre = nombre
    self.edad = edad

  def saludar(self):
    print(f'Hola, me llamo {self.nombre} y tengo {self.edad} años')
```

- **Herencia**

```python
class Persona:
  def __init__(self, nombre, edad):
    self.nombre = nombre
    self.edad = edad

  def saludar(self):
    print(f'Hola, me llamo {self.nombre} y tengo {self.edad} años')

class Estudiante(Persona):
  def __init__(self, nombre, edad, carrera):
    super().__init__(nombre, edad)
    self.carrera = carrera

  def estudiar(self):
    print(f'Estoy estudiando la carrera de {self.carrera}')
```

- **Propiedades y `dataclass`**

```python
from dataclasses import dataclass

@dataclass
class Punto:
  x: int
  y: int = 0

class Cuenta:
  def __init__(self, saldo):
    self._saldo = saldo

  @property
  def saldo(self):
    return self._saldo

  @saldo.setter
  def saldo(self, nuevo):
    if nuevo < 0:
      raise ValueError('Saldo negativo')
    self._saldo = nuevo
```

- **Métodos estáticos y de clase**

```python
class Circulo:
  def __init__(self, radio):
    self.radio = radio

  @staticmethod
  def es_radio_valido(radio):
    return radio > 0

  @classmethod
  def unidad(cls):
    return cls(radio=1)

Circulo.es_radio_valido(5)  # True
Circulo.unidad().radio      # 1
```

- **Atributos y métodos "privados" (convención)**

```python
class Cuenta:
  def __init__(self, saldo):
    self._saldo = saldo      # protegido por convención
    self.__pin = '1234'      # name mangling: _Cuenta__pin
```

- **Método super()**

```python
super().__init__(nombre, edad)
```

- **Método isinstance()**

```python
juan = Persona('Juan', 25)
isinstance(juan, Persona) # True
isinstance(juan, Estudiante) # False
```

- **Método issubclass()**

```python
issubclass(Estudiante, Persona) # True
issubclass(Persona, Estudiante) # False
```

- **Método getattr()**

```python
juan = Persona('Juan', 25)
getattr(juan, 'nombre') # 'Juan'
```

- **Método setattr()**

```python
juan = Persona('Juan', 25)
setattr(juan, 'nombre', 'Carlos')
juan.nombre # 'Carlos'
```

- **Método delattr()**

```python
juan = Persona('Juan', 25)
delattr(juan, 'edad')
juan.edad # AttributeError: 'Persona' object has no attribute 'edad'
```

- **Métodos mágicos comunes**

```python
class Vector:
  def __init__(self, x, y):
    self.x, self.y = x, y

  def __repr__(self):
    return f'Vector({self.x}, {self.y})'

  def __eq__(self, otro):
    return (self.x, self.y) == (otro.x, otro.y)

  def __add__(self, otro):
    return Vector(self.x + otro.x, self.y + otro.y)

Vector(1, 2) + Vector(3, 4)  # Vector(4, 6)
```

---

## Herencia Múltiple

```python
class A:
  def __init__(self):
    print('Soy de clase A')

class B:
  def __init__(self):
    print('Soy de clase B')

class C(A, B):
  def __init__(self):
    super().__init__()
    print('Soy de clase C')

c = C()
# Soy de clase A
# Soy de clase C

print(C.mro())
# [<class '__main__.C'>, <class '__main__.A'>, <class '__main__.B'>, <class 'object'>]
```

> `super()` sigue el Method Resolution Order (MRO). Si necesitas llamar a un
> padre específico, llama a su método directamente, pero mantén el orden del MRO
> para evitar ejecuciones duplicadas.

---

## Clases abstractas

Usa `abc` para definir interfaces que obligan a implementar ciertos métodos.

```python
from abc import ABC, abstractmethod

class Figura(ABC):
  @abstractmethod
  def area(self):
    ...

class Cuadrado(Figura):
  def __init__(self, lado):
    self.lado = lado

  def area(self):
    return self.lado ** 2

Cuadrado(4).area()  # 16
Figura()  # TypeError: no se puede instanciar una clase abstracta
```

---

## Enum

```python
from enum import Enum, auto

class Color(Enum):
  ROJO = auto()
  VERDE = auto()
  AZUL = auto()

Color.ROJO          # <Color.ROJO: 1>
Color.ROJO.name      # 'ROJO'
Color.ROJO.value     # 1
Color.ROJO == Color.VERDE  # False

for color in Color:
  print(color)
```

---

## Type hints

Las anotaciones documentan tipos esperados; no se aplican en tiempo de
ejecución sin herramientas externas como `mypy`.

- **Tipos básicos y colecciones (Python 3.9+)**

```python
def saludar(nombre: str) -> str:
  return f'Hola {nombre}'

edades: dict[str, int] = {'Ana': 30}
numeros: list[int] = [1, 2, 3]
```

- **Uniones y opcionales (Python 3.10+)**

```python
def buscar(id: int) -> str | None:
  return None

def procesar(valor: int | str) -> None:
  ...
```

- **Alias de tipos (Python 3.12+)**

```python
type Vector = list[float]

def escalar(factor: float, v: Vector) -> Vector:
  return [factor * n for n in v]
```

- **Callable**

```python
from collections.abc import Callable

def aplicar(funcion: Callable[[int, int], int], a: int, b: int) -> int:
  return funcion(a, b)
```

- **Genéricos en clases (Python 3.12+)**

```python
class Caja[T]:
  def __init__(self, contenido: T) -> None:
    self.contenido = contenido

  def obtener(self) -> T:
    return self.contenido
```

---

## Formatos de salida

- **Comodines**

```python
nombre = 'Juan'
edad = 25
print('Hola, me llamo %s y tengo %d años' % (nombre, edad))
# Hola, me llamo Juan y tengo 25 años
```

- **Formato**

```python
nombre = 'Juan'
edad = 25
print('Hola, me llamo {} y tengo {} años'.format(nombre, edad))
# Hola, me llamo Juan y tengo 25 años
```

- **F-strings**

```python
nombre = 'Juan'
edad = 25
print(f'Hola, me llamo {nombre} y tengo {edad} años')
# Hola, me llamo Juan y tengo 25 años
```

- **F-strings con expresiones y debug (`=`)**

```python
x = 10
print(f'{x=}')        # x=10
print(f'{x * 2}')     # 20
```

- **Alineación y Relleno**

```python
for i in range(1, 4):
    print(f"{i:2} {i*i:3} {i*i*i:4}")
# 1   1    1
# 2   4    8
# 3   9   27
```

- **Números**

```python
numero = 3.1415926
print('{:f}'.format(numero)) # '3.141593'
print('{:.2f}'.format(numero)) # '3.14'
print('{:10.2f}'.format(numero)) # '      3.14'
print('{:010.2f}'.format(numero)) # '0000003.14'
print(f'{1234567:,}')   # '1,234,567'
print(f'{0.256:.1%}')   # '25.6%'
```

- **Fecha y Hora**

```python
import datetime
fecha = datetime.datetime.now()
print('{:%Y-%m-%d %H:%M}'.format(fecha)) # '2021-06-14 23:09'
```

---

## Métodos de Objetos de Archivo

- **Crear un archivo**

```python
archivo = open('archivo.txt', 'w')
```

- **Escribir en un archivo**

```python
archivo = open('archivo.txt', 'w')
archivo.write('Hola Mundo')
archivo.close()
```

- **Leer un archivo**

```python
archivo = open('archivo.txt', 'r')
contenido = archivo.read()
archivo.close()
print(contenido) # 'Hola Mundo'
```

- **Leer un archivo línea por línea**

```python
archivo = open('archivo.txt', 'r')
linea1 = archivo.readline()
linea2 = archivo.readline()
archivo.close()
print(linea1) # 'Hola Mundo'
print(linea2) # ''
```

- **Leer todas las líneas de un archivo**

```python
archivo = open('archivo.txt', 'r')
lineas = archivo.readlines()
archivo.close()
print(lineas) # ['Hola Mundo']
```

- **Iterar sobre un archivo sin cargarlo completo**

```python
with open('archivo.txt', 'r') as archivo:
  for linea in archivo:
    print(linea.strip())
```

- **Cerrar un archivo**

```python
archivo = open('archivo.txt', 'r')
archivo.close()
```

- **Usar un archivo como un administrador de contexto**

```python
with open('archivo.txt', 'r') as archivo:
  contenido = archivo.read()
print(contenido) # 'Hola Mundo'
```

- **Modos de apertura comunes**

```python
open('a.txt', 'r')   # lectura (por defecto)
open('a.txt', 'w')   # escritura, trunca el archivo
open('a.txt', 'a')   # añade al final
open('a.txt', 'x')   # crea, falla si ya existe
open('a.bin', 'rb')  # lectura binaria
```

- **Uso de `pathlib.Path`**

```python
from pathlib import Path
ruta = Path('archivo.txt')
ruta.write_text('Hola con Path\n', encoding='utf-8')
print(ruta.read_text())
ruta.exists()  # True
ruta.suffix    # '.txt'
```

---

## Administradores de contexto personalizados

El protocolo `with` requiere `__enter__` y `__exit__`.

- **Con una clase**

```python
class Temporizador:
  def __enter__(self):
    print('Iniciando')
    return self

  def __exit__(self, exc_type, exc_value, traceback):
    print('Finalizando')
    return False  # no suprime excepciones

with Temporizador():
  print('Trabajando')
# Iniciando
# Trabajando
# Finalizando
```

- **Con `contextlib.contextmanager`**

```python
from contextlib import contextmanager

@contextmanager
def recurso():
  print('Abriendo')
  yield 'valor'
  print('Cerrando')

with recurso() as v:
  print(v)
# Abriendo
# valor
# Cerrando
```

---

## Excepciones

### Tipos Comunes de Excepciones

- SyntaxError: Error de sintaxis en el código.
- NameError: Se intenta acceder a una variable o función no definida.
- TypeError: Operación aplicada a un objeto de tipo inapropiado.
- IndexError: Acceso a un índice fuera del rango de una secuencia.
- KeyError: Acceso a una clave que no existe en un diccionario.
- ValueError: Argumento de función de tipo correcto pero valor inapropiado.
- FileNotFoundError: Intento de abrir un archivo que no existe.
- ZeroDivisionError: División por cero.

### Estructura Básica para el Manejo de Excepciones

```python
try:
    # Código que puede generar una excepción
except ExcepcionTipo1:
    # Código que se ejecuta si se produce ExcepcionTipo1
except (ExcepcionTipo2, ExcepcionTipo3) as e:
    # Código para manejar múltiples excepciones
    # 'e' es la excepción capturada
except Exception as e:
    # Código que se ejecuta para cualquier excepción no capturada por los anteriores
    # No es recomendable capturar todas las excepciones sin distinción
else:
    # Código que se ejecuta si no hay excepciones
finally:
    # Código que se ejecuta siempre, con o sin excepción
```

- **Ejemplo**

```python
try:
    with open("datos.txt", "r") as archivo:
        contenido = archivo.read()
        numero = int(contenido.strip())
        resultado = 10 / numero
except FileNotFoundError:
    print("El archivo no se encontró.")
except ValueError:
    print("El archivo no contiene un número válido.")
except ZeroDivisionError:
    print("El archivo contiene un cero, lo que causa una división por cero.")
except Exception as e:
    print(f"Error inesperado: {e}")
else:
    print(f"Resultado procesado con éxito: {resultado}")
finally:
    print("Finalización del manejo de archivos.")
```

### Levantando Excepciones

```python
x = -1
if x < 0:
    raise ValueError("x no puede ser negativo")
```

- **Encadenar excepciones**

```python
try:
    cargar_config()
except FileNotFoundError as error:
    raise RuntimeError("No se pudo iniciar la aplicación") from error
```

- **Agrupar varias excepciones (Python 3.11+)**

```python
try:
    raise ExceptionGroup('varios errores', [ValueError('a'), TypeError('b')])
except* ValueError as eg:
    print('Se capturaron ValueError:', eg.exceptions)
except* TypeError as eg:
    print('Se capturaron TypeError:', eg.exceptions)
```

### Excepciones Personalizadas

```python
class MiExcepcion(Exception):
    pass

raise MiExcepcion("Un mensaje de error")
```

- **Ignorar temporalmente excepciones conocidas**

```python
from contextlib import suppress
from pathlib import Path

with suppress(FileNotFoundError):
    Path('cache.tmp').unlink()
```

---

## Docstrings

- **Estilo de Google**

```python
def funcion(arg1, arg2):
    """Descripción de lo que hace la función.

    Args:
        arg1: Descripción del arg1.
        arg2: Descripción del arg2.

    Returns:
        Lo que devuelve la función.
    """
```

- **Estilo de reStructuredText (reST) utilizado por Sphinx**

```python
def funcion(arg1, arg2):
    """
    Descripción de lo que hace la función.

    :param arg1: Descripción del arg1.
    :param arg2: Descripción del arg2.
    :returns: Lo que devuelve la función.
    """
```

- **Estilo NumPy/SciPy**

```python
def funcion(arg1, arg2):
    """Descripción de lo que hace la función.

    Parameters
    ----------
    arg1 : tipo
        Descripción del arg1.
    arg2 : tipo
        Descripción del arg2.

    Returns
    -------
        tipo
        Lo que devuelve la función.
    """
```

Consulta los docstrings con `help(funcion)` o `print(funcion.__doc__)` para
aprovechar la documentación desde el intérprete.

---

## Estilo de codificación

### Indentación

- Usa 4 espacios por nivel de indentación.
- Evita el uso de tabs, o configura tu editor para que convierta tabs a espacios.

### Longitud de Líneas

- Limita todas las líneas a un máximo de 79 caracteres para código y 72 para comentarios y docstrings.

### Espacios en Blanco

- Usa espacios en blanco de manera adecuada para mejorar la legibilidad.
- No uses espacios en blanco alrededor de paréntesis, llaves o corchetes.

### Importaciones

- Las importaciones deben estar en líneas separadas.
- Agrupa las importaciones: primero las bibliotecas estándar, luego las bibliotecas de terceros, y finalmente las importaciones locales.

### Comentarios

- Los comentarios deben ser claros y concisos.
- Asegúrate de que los comentarios estén actualizados con el código.

### Docstrings

- Usa docstrings para documentar módulos, funciones, clases y métodos
- El estilo de docstring recomendado es reStructuredText (reST).

### Nombres de Variables y Funciones

- Usa nombres descriptivos y evita abreviaturas.
- Para nombres de variables y funciones, usa snake_case (palabras en minúsculas separadas por guiones bajos).
- Para nombres de clases, usa CamelCase (estilo camel case).

### Espacios en Blanco en Expresiones y Declaraciones

- No coloques espacios adicionales alrededor de una asignación o una comparación.

### Buenas Prácticas de Programación

- Escribe código pensando en su legibilidad.
- Sigue los principios DRY (Don't Repeat Yourself) y KISS (Keep It Simple, Stupid).
- Prueba tu código rigurosamente.

### Herramientas Útiles

- Utiliza linters y formateadores de código como ruff (incluye reglas de flake8) y black para asegurarte de que tu código cumple con PEP 8.
- Usa mypy para la verificación de tipos si estás utilizando anotaciones de tipo.

---

## Uso de la librería estándar

Explora la documentación oficial para descubrir módulos poco conocidos:

- https://docs.python.org/3/tutorial/stdlib.html
- https://docs.python.org/3/tutorial/stdlib2.html
- `pydoc <módulo>` desde la terminal para abrir la ayuda integrada.

---

## Entornos virtuales

Un entorno virtual es una instancia independiente de Python que mantiene sus propios archivos, directorios y paths. Al trabajar dentro de un entorno virtual, puedes instalar y gestionar paquetes sin afectar a otros proyectos o al sistema global de Python. Esto es especialmente útil cuando trabajas en múltiples proyectos con distintas dependencias.

- **Creación:**

```bash
python3 -m venv mi_entorno
```

Esto crea un nuevo entorno virtual en el directorio mi_entorno.

### Creación y Activación de un Entorno Virtual

- **Activación**
  - En Windows:
  ```bash
  mi_entorno\Scripts\activate.bat
  ```
  - En Unix o MacOS:
  ```bash
  source mi_entorno/bin/activate
  ```
  Al activar el entorno, verás el nombre del entorno en tu terminal, lo que indica que todas las operaciones de Python se realizan ahora en ese entorno aislado.

### Desactivación del Entorno Virtual

Para dejar de usar un entorno virtual y volver al entorno global de Python, simplemente ejecuta:

```bash
deactivate
```

### Gestión de Paquetes con pip

pip es el gestor de paquetes de Python que te permite instalar, actualizar y eliminar paquetes. Dentro de un entorno virtual, pip gestiona los paquetes para ese entorno específico.

- **Instalación de Paquetes**

```bash
pip install nombre_paquete
```

- **Listado de Paquetes Instalados**

```bash
pip list
```

- **Actualización de Paquetes**

```bash
pip install --upgrade nombre_paquete
```

- **Eliminación de Paquetes**

```bash
pip uninstall nombre_paquete
```

### Uso de requirements.txt

Un archivo requirements.txt es una forma estándar de listar las dependencias de un proyecto, permitiendo instalar todos los paquetes necesarios con un solo comando. Suele contener una lista de paquetes y versiones.

- Para generar un requirements.txt con todos los paquetes instalados:

```bash
pip freeze > requirements.txt
```

- Para instalar paquetes desde un requirements.txt:

```bash
pip install -r requirements.txt
```
