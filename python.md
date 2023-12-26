## Comentarios

```python
# Soy un comentario
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

---

## pass

Marcador de posición para código que aún no has escrito.
Permite a los desarrolladores crear esqueletos de código que pueden ser completados más tarde, manteniendo la estructura del programa clara y sin errores de sintaxis

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

## match

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
cadena.isnumeric() # False
```

- **Comprobar si es alfabética**

```python
cadena.isalpha() # True
```

- **Buscar el índice de un caracter**

```python
cadena.index('P') # 0S
cadena.index('w') # ValueError
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

---

## Tuplas

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

---

## Modulos

- **Creación de un módulo**

```python
# modulo.py
def saludar():
  print('Hola, soy un módulo')
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

- **Importación de un módulo con la función from**

```python
from modulo import saludar
saludar() # Hola, soy un módulo
```

- **Importación de todas las funciones de un módulo**

```python
from modulo import *
```

- **Importación de todas las funciones de un módulo con un alias**

```python
from modulo import * as md
```

- **Importación de todas las funciones de un módulo excepto una**

```python
from modulo import * except saludar
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

- **Con un Objetos**
  Al pasarle un objeto, dir() devuelve los atributos del objeto, lo cual incluye métodos y propiedades.

```python
print(dir("Hola Mundo"))
# Aquí se enumeran todos los métodos y propiedades asociados con un objeto de cadena (str).

```

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

- **Importación de todas las funciones de un módulo de un paquete con un alias**

```python
from paquete.modulo import * as md
```

- **Importación de todas las funciones de un módulo de un paquete excepto una**

```python
from paquete.modulo import * except saludar
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

- **Leer todas las líneas de un archivo como una lista**

```python
archivo = open('archivo.txt', 'r')
lineas = archivo.readlines()
archivo.close()
print(lineas) # ['Hola Mundo']
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

- **Leer todas las líneas de un archivo como una lista**

```python
archivo = open('archivo.txt', 'r')
lineas = archivo.readlines()
archivo.close()
print(lineas) # ['Hola Mundo']
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

### Excepciones Personalizadas

```python
class MiExcepcion(Exception):
    pass

raise MiExcepcion("Un mensaje de error")
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

- Utiliza linters y formateadores de código, como flake8 y black, para asegurarte de que tu código cumple con PEP 8.
- Usa mypy para la verificación de tipos si estás utilizando anotaciones de tipo.

---

## Uso de llibreria

- https://docs.python.org/3/tutorial/stdlib.html
- https://docs.python.org/3/tutorial/stdlib2.html

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
