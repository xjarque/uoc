
# INTELIGENCIA ARTIFICIAL
~~Lorem~~ `OK`

## INDICE

1. Introducción a la resolución de problemas y búsqueda
   
1.1 Espacio de estados y representación de un problema

[MODELIZACIÓN]

```js

Ejemplos de modelizaciones

a) Rompecabezas lineal

  Dada una permutación cualquiera de la secuencia [1, 2, 3, 4], determinar cómo construi-
  ríamos otra que satisfaga una determinada propiedad (por ejemplo, que esté ordenada
  de mayor a menor, que represente un número múltiplo de 2, etc.). Consideraremos que,
  dada una permutación, para construir una nueva podemos intercambiar solo dos núme-
  ros que estén en posiciones consecutivas de la secuencia. Por ejemplo, ¿cómo se ordena
  la secuencia [3, 4, 1, 2] 

Estados posibles en el rompecabezas lineal

  En el ejemplo del rompecabezas lineal las secuencias [1, 2, 3, 4], [2, 3, 4, 1], [3, 1, 2, 4] son
  estados posibles. De hecho, el conjunto de estados posibles es el conjunto de todas las
  secuencias posibles construibles con las permutaciones de las cuatro cifras. Dado que el
  número de secuencias posibles formadas con los cuatro dígitos {1,2,3,4} es 4!, tendremos
  que los posibles estados son 24 y son, evidentemente, los siguientes: {[1, 2, 3, 4], [1, 2, 4,
  3], [1, 3, 2, 4], [1, 3, 4, 2], [1, 4, 2, 3], [1, 4, 3, 2], [2, 1, 3, 4], [2, 1, 4, 3], [2, 3, 1, 4], [2, 3,
  4, 1], [2, 4, 1, 3], [2, 4, 3, 1], [3, 2, 1, 4], [3, 2, 4, 1], [3, 1, 2, 4], [3, 1, 4, 2], [3, 4, 2, 1], [3,
  4, 1, 2], [4, 2, 3, 1], [4, 2, 1, 3], [4, 3, 2, 1], [4, 3, 1, 2], [4, 1, 2, 3], [4, 1, 3, 2]}.

Posibles acciones del sistema en el rompecabezas lineal
  
  En el sistema del rompecabezas lineal hay tres acciones posibles correspondientes a los
  tres intercambios que podemos hacer. Denominaremos las acciones ID, IC e IE, que co-
  rresponderán, respectivamente, a los intercambios derecho, central e izquierdo. Dado el
  estado [A, B, C, D], la acción IE nos conducirá al estado [B, A, C, D], la acción IC nos
  conducirá al estado [A, C, B, D] y la acción ID al estado [A, B, D, C]. En el esquema de
  la figura 1 se hace una representación gráfica de estas acciones. La representación gráfica
  de la aplicación de la acción IC al estado [1, 2, 3, 4] es al esquema b. El espacio de estados
  correspondiente a este problema aparece en c.

La definición del problema necesita una descripción del [estado inicial]
y una función objetivo. Las [funciones objetivo] comprueban la satis-
facción de los requerimientos exigidos a un estado solución.

Definición del problema del rompecabezas lineal

  En el caso del rompecabezas lineal, un ejemplo de problema es el siguiente: dada la se-
  cuencia [2, 4, 1, 3], determinar los movimientos para conseguir una secuencia que sea
  múltiplo de dos. En este caso, el estado inicial es [2, 4, 1, 3] y la función objetivo aplica-
  da a un estado corresponde a probar si la secuencia acaba en 2 o en 4. Otro problema
  es, dada la secuencia anterior, determinar los movimientos para conseguir la secuencia
  ordenada [1, 2, 3, 4]. En este caso, tenemos, como antes, que el estado inicial es [2, 4, 1,
  3] y la función objetivo será comprobar que el estado es [1, 2, 3, 4]


```

1.1.1.Algunas clases generales de problemas: satisfacción de restricciones y planificación

[PLANIFICACIÓN]

La manera más sencilla de tratar la planificación es considerando que cada posible situación de los objetos es un estado.

```js
Ejemplo de planificación

Consideramos la ubicación de tres objetos A, B y C y queremos determinar los movi-
  mientos necesarios para poner cada objeto en la posición requerida. En la figura 3 se
  muestra dónde están los objetos y cómo se quieren dejar. Para conseguir este resultado,
  el sistema puede coger un objeto apilado y dejarlo sobre la superficie o coger un objeto
  y ponerlo sobre otro.
```


[RESTRICCIONES]

Problemas de satisfacción de restricciones

Un problema de satisfacción de restricciones se define mediante un conjunto
de variables, un dominio para cada variable y un conjunto de restricciones que
las variables han de satisfacer. El problema estará resuelto cuando todas las va-
riables tienen un valor asignado y, además, se satisfacen todas las restricciones.

```js
Ejemplos de modelización de problemas de satisfacción de restricciones
1) Problema de las ocho reinas
Una manera de modelizar este problema siguiendo lo que se ha explicado hasta ahora
es considerar ocho variables de forma que cada una de ellas corresponda a la columna
en que está la reina de la i-ésima fila.
```


1.1.2. Algunas consideraciones adicionales: la importancia de una representación adecuada y la cuestión del coste

Dado que los algoritmos de búsqueda se basan en el espacio de estados que
se define, interesa que el espacio sea lo más reducido posible para que la bús-
queda sea menos costosa. A veces, un cambio de representación puede reducir
enormemente una búsqueda.


1.1.3. Análisis práctico del problema de las ocho reinas

Basándonos en la modelización que acabamos de dar del problema de las ocho
reinas, nos podemos hacer algunas preguntas que serán determinantes para
poder implementar un procedimiento de búsqueda de soluciones:

¿Cuántos estados posibles tiene nuestro problema 


1.1.4. Representación de un problema: implementación con
Python del rompecabezas lineal

A continuación, haremos la representación del problema del rompecabezas lineal con Python.

1) Modelización del entorno

Con Python, representaremos el estado
mediante la secuencia [A, B, C, D].

2) Modelización de las acciones del sistema

```python

# Primer elemento car (estado)
# Segundo elemento cadr(estado)
# Tercer elemento caddr(estado)
# Cuarto elemento cadddr(estado)

def mov_ie (estado, info):
  return [cadr(estado), car(estado), caddr(estado), cadddr(estado)]

def mov_ic (estado, info):
  return [car(estado), caddr(estado), cadr(estado), cadddr(estado)]

def mov_id (estado, info):
  return [car(estado), cadr(estado), cadddr(estado), caddr(estado)]

# Los operadores del rompecabezas lineal los almacenamos en una lista
def rl_operadores():
  return [['ie', mov_ie], ['ic', mov_ic], ['id', mov_id]]

```

3) Definición del problema

Necesitamos saber cómo representamos el estado inicial y disponer de una
función objetivo.
Así, el estado inicial es la secuencia
[2, 4, 1, 3].

```python
# la secuencia acaba en 2 o 4
def rl_funcion_objetivo_par(estado):
  return cadddr(estado) == 2 or cadddr(estado) == 4
```

```python
# Si consideramos que solo hay un estado solución y este es el de la secuencia [1, 2, 3, 4]
def rl_funcion_objetivo(estado):
  return estado == [1,2,3,4]
```

En la definición del problema consideramos los cuatro elementos siguientes:
los operadores del problema (en este caso rl-operadores()), el estado ini-
cial (la lista [4,3,2,1]), la función objetivo lambda estado: estado ==
[1,2,3,4] y una función, que más adelante nos será de utilidad, que asocia
a cada estado información adicional (de momento, como que no la usamos,
la definimos de forma que retorne [] para cualquier estado). El problema se
representa mediante una lista con estos cuatro elementos en el orden estable-
cido.

```python
# Ahora, con todos estos elementos podemos montar el problema.
def problema():
  return [
    rl_operadores(),
    (lambda info_nodo_padre, estado, nombre_operador: []),
    [4,3,2,1],
    (lambda estado: estado == [1,2,3,4]),
    (lambda estado: [])]
```


2.1. La implementación                         28
2.1.1. Implementación con Python              . 32
2.1.2. El árbol de búsqueda: representación y funciones   .. 34
2.1.3. Los nodos: representación y funciones         . 36
2.1.4. El problema: representación y funciones        . 39
Algunas consideraciones adicionales                39
Estrategias de búsqueda no informada              42
3.1. Búsqueda en anchura                        42
3.1.1. Implementación                     . 44
Búsqueda en profundidad                    .. 44
3.2.1. Búsqueda en profundidad limitada           . 46
Ejemplo práctico de búsqueda de solución           .. 52
Coste y función heurística                    .. 55
4.1. Búsqueda de coste uniforme                   . 56
4.2. Búsqueda con función heurística: búsqueda ávida o voraz   .. 59
4.3. Búsqueda con función heurística: algoritmo A*         . 62
4.3.1. Algunas cuestiones de la función heurística      .. 65
4.3.2. Consistencia del heurístico               . 66
4.3.3. Implementación                     . 69
Otros métodos de búsqueda heurística               72
Búsqueda con adversario: los juegos              .. 74
5.1. 74
3.3.
4.4.
5.
1.1.3. 21
3.2.
4.
19
con Python del rompecabezas lineal          ..
2.2.
3.
coste                           .
Decisiones perfectas                       ..Resolución de problemas y búsqueda
© FUOC   PID_00267997
5.1.1.
La poda  -                        .. 86
5.2. Decisiones imperfectas                      . 92
5.3. Juegos con elementos de azar                  .. 94

### Problema del laberinto

https://www.linkedin.com/pulse/explorando-la-inteligencia-artificial-en-resoluci%C3%B3n-de-limon-peralta-xffie/

Ejercicios de autoevaluación

1. Considerad el problema siguiente:
   
Dado un laberinto, encontrad la secuencia de movimientos que permite ir de la entrada a la
salida. Responded las cuestiones siguientes:

a) Formulad el problema de forma que pueda ser resuelto mediante los **métodos de búsqueda**.



b) De acuerdo con la formulación, describid el espacio de estados del problema.
c) Mostrad cómo se aplica esta formulación al laberinto de la figura.
d) ¿Qué métodos de búsqueda podemos utilizar para resolver el problema 
e) Si queremos que el número de posiciones del laberinto atravesadas sea mínimo, ¿podemos
aplicar el algoritmo A*  Indicad una función heurística admisible para este problema.

[METODOS_BUSQUEDA]


## Bibliografía

Bibliografía
Russell, S. J., & Norvig, P. (2020). Artificial Intelligence: A Modern Approach (4th Edition). Pearson.
Thrun, S., Burgard, W., & Fox, D. (2005). Probabilistic Robotics. MIT Press.
Cormen, T. H., Leiserson, C. E., Rivest, R. L., & Stein, C. (2009). Introduction to Algorithms (3rd Edition). MIT Press.
