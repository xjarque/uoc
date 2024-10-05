
# INTELIGENCIA ARTIFICIAL
~~Lorem~~ `OK`

## INDICE

1. Introducci�n a la resoluci�n de problemas y b�squeda
   
1.1 Espacio de estados y representaci�n de un problema

[MODELIZACI�N]

```js

Ejemplos de modelizaciones

a) Rompecabezas lineal

  Dada una permutaci�n cualquiera de la secuencia [1, 2, 3, 4], determinar c�mo construi-
  r�amos otra que satisfaga una determinada propiedad (por ejemplo, que est� ordenada
  de mayor a menor, que represente un n�mero m�ltiplo de 2, etc.). Consideraremos que,
  dada una permutaci�n, para construir una nueva podemos intercambiar solo dos n�me-
  ros que est�n en posiciones consecutivas de la secuencia. Por ejemplo, �c�mo se ordena
  la secuencia [3, 4, 1, 2] 

Estados posibles en el rompecabezas lineal

  En el ejemplo del rompecabezas lineal las secuencias [1, 2, 3, 4], [2, 3, 4, 1], [3, 1, 2, 4] son
  estados posibles. De hecho, el conjunto de estados posibles es el conjunto de todas las
  secuencias posibles construibles con las permutaciones de las cuatro cifras. Dado que el
  n�mero de secuencias posibles formadas con los cuatro d�gitos {1,2,3,4} es 4!, tendremos
  que los posibles estados son 24 y son, evidentemente, los siguientes: {[1, 2, 3, 4], [1, 2, 4,
  3], [1, 3, 2, 4], [1, 3, 4, 2], [1, 4, 2, 3], [1, 4, 3, 2], [2, 1, 3, 4], [2, 1, 4, 3], [2, 3, 1, 4], [2, 3,
  4, 1], [2, 4, 1, 3], [2, 4, 3, 1], [3, 2, 1, 4], [3, 2, 4, 1], [3, 1, 2, 4], [3, 1, 4, 2], [3, 4, 2, 1], [3,
  4, 1, 2], [4, 2, 3, 1], [4, 2, 1, 3], [4, 3, 2, 1], [4, 3, 1, 2], [4, 1, 2, 3], [4, 1, 3, 2]}.

Posibles acciones del sistema en el rompecabezas lineal
  
  En el sistema del rompecabezas lineal hay tres acciones posibles correspondientes a los
  tres intercambios que podemos hacer. Denominaremos las acciones ID, IC e IE, que co-
  rresponder�n, respectivamente, a los intercambios derecho, central e izquierdo. Dado el
  estado [A, B, C, D], la acci�n IE nos conducir� al estado [B, A, C, D], la acci�n IC nos
  conducir� al estado [A, C, B, D] y la acci�n ID al estado [A, B, D, C]. En el esquema de
  la figura 1 se hace una representaci�n gr�fica de estas acciones. La representaci�n gr�fica
  de la aplicaci�n de la acci�n IC al estado [1, 2, 3, 4] es al esquema b. El espacio de estados
  correspondiente a este problema aparece en c.

La definici�n del problema necesita una descripci�n del [estado inicial]
y una funci�n objetivo. Las [funciones objetivo] comprueban la satis-
facci�n de los requerimientos exigidos a un estado soluci�n.

Definici�n del problema del rompecabezas lineal

  En el caso del rompecabezas lineal, un ejemplo de problema es el siguiente: dada la se-
  cuencia [2, 4, 1, 3], determinar los movimientos para conseguir una secuencia que sea
  m�ltiplo de dos. En este caso, el estado inicial es [2, 4, 1, 3] y la funci�n objetivo aplica-
  da a un estado corresponde a probar si la secuencia acaba en 2 o en 4. Otro problema
  es, dada la secuencia anterior, determinar los movimientos para conseguir la secuencia
  ordenada [1, 2, 3, 4]. En este caso, tenemos, como antes, que el estado inicial es [2, 4, 1,
  3] y la funci�n objetivo ser� comprobar que el estado es [1, 2, 3, 4]


```

1.1.1.Algunas clases generales de problemas: satisfacci�n de restricciones y planificaci�n

[PLANIFICACI�N]

La manera m�s sencilla de tratar la planificaci�n es considerando que cada posible situaci�n de los objetos es un estado.

```js
Ejemplo de planificaci�n

Consideramos la ubicaci�n de tres objetos A, B y C y queremos determinar los movi-
  mientos necesarios para poner cada objeto en la posici�n requerida. En la figura 3 se
  muestra d�nde est�n los objetos y c�mo se quieren dejar. Para conseguir este resultado,
  el sistema puede coger un objeto apilado y dejarlo sobre la superficie o coger un objeto
  y ponerlo sobre otro.
```


[RESTRICCIONES]

Problemas de satisfacci�n de restricciones

Un problema de satisfacci�n de restricciones se define mediante un conjunto
de variables, un dominio para cada variable y un conjunto de restricciones que
las variables han de satisfacer. El problema estar� resuelto cuando todas las va-
riables tienen un valor asignado y, adem�s, se satisfacen todas las restricciones.

```js
Ejemplos de modelizaci�n de problemas de satisfacci�n de restricciones
1) Problema de las ocho reinas
Una manera de modelizar este problema siguiendo lo que se ha explicado hasta ahora
es considerar ocho variables de forma que cada una de ellas corresponda a la columna
en que est� la reina de la i-�sima fila.
```


1.1.2. Algunas consideraciones adicionales: la importancia de una representaci�n adecuada y la cuesti�n del coste

Dado que los algoritmos de b�squeda se basan en el espacio de estados que
se define, interesa que el espacio sea lo m�s reducido posible para que la b�s-
queda sea menos costosa. A veces, un cambio de representaci�n puede reducir
enormemente una b�squeda.


1.1.3. An�lisis pr�ctico del problema de las ocho reinas

Bas�ndonos en la modelizaci�n que acabamos de dar del problema de las ocho
reinas, nos podemos hacer algunas preguntas que ser�n determinantes para
poder implementar un procedimiento de b�squeda de soluciones:

�Cu�ntos estados posibles tiene nuestro problema 


1.1.4. Representaci�n de un problema: implementaci�n con
Python del rompecabezas lineal

A continuaci�n, haremos la representaci�n del problema del rompecabezas lineal con Python.

1) Modelizaci�n del entorno

Con Python, representaremos el estado
mediante la secuencia [A, B, C, D].

2) Modelizaci�n de las acciones del sistema

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

3) Definici�n del problema

Necesitamos saber c�mo representamos el estado inicial y disponer de una
funci�n objetivo.
As�, el estado inicial es la secuencia
[2, 4, 1, 3].

```python
# la secuencia acaba en 2 o 4
def rl_funcion_objetivo_par(estado):
  return cadddr(estado) == 2 or cadddr(estado) == 4
```

```python
# Si consideramos que solo hay un estado soluci�n y este es el de la secuencia [1, 2, 3, 4]
def rl_funcion_objetivo(estado):
  return estado == [1,2,3,4]
```

En la definici�n del problema consideramos los cuatro elementos siguientes:
los operadores del problema (en este caso rl-operadores()), el estado ini-
cial (la lista [4,3,2,1]), la funci�n objetivo lambda estado: estado ==
[1,2,3,4] y una funci�n, que m�s adelante nos ser� de utilidad, que asocia
a cada estado informaci�n adicional (de momento, como que no la usamos,
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


2.1. La implementaci�n                         28
2.1.1. Implementaci�n con Python              . 32
2.1.2. El �rbol de b�squeda: representaci�n y funciones   .. 34
2.1.3. Los nodos: representaci�n y funciones         . 36
2.1.4. El problema: representaci�n y funciones        . 39
Algunas consideraciones adicionales                39
Estrategias de b�squeda no informada              42
3.1. B�squeda en anchura                        42
3.1.1. Implementaci�n                     . 44
B�squeda en profundidad                    .. 44
3.2.1. B�squeda en profundidad limitada           . 46
Ejemplo pr�ctico de b�squeda de soluci�n           .. 52
Coste y funci�n heur�stica                    .. 55
4.1. B�squeda de coste uniforme                   . 56
4.2. B�squeda con funci�n heur�stica: b�squeda �vida o voraz   .. 59
4.3. B�squeda con funci�n heur�stica: algoritmo A*         . 62
4.3.1. Algunas cuestiones de la funci�n heur�stica      .. 65
4.3.2. Consistencia del heur�stico               . 66
4.3.3. Implementaci�n                     . 69
Otros m�todos de b�squeda heur�stica               72
B�squeda con adversario: los juegos              .. 74
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
Decisiones perfectas                       ..Resoluci�n de problemas y b�squeda
� FUOC   PID_00267997
5.1.1.
La poda  -                        .. 86
5.2. Decisiones imperfectas                      . 92
5.3. Juegos con elementos de azar                  .. 94

### Problema del laberinto

https://www.linkedin.com/pulse/explorando-la-inteligencia-artificial-en-resoluci%C3%B3n-de-limon-peralta-xffie/

Ejercicios de autoevaluaci�n

1. Considerad el problema siguiente:
   
Dado un laberinto, encontrad la secuencia de movimientos que permite ir de la entrada a la
salida. Responded las cuestiones siguientes:

a) Formulad el problema de forma que pueda ser resuelto mediante los **m�todos de b�squeda**.



b) De acuerdo con la formulaci�n, describid el espacio de estados del problema.
c) Mostrad c�mo se aplica esta formulaci�n al laberinto de la figura.
d) �Qu� m�todos de b�squeda podemos utilizar para resolver el problema 
e) Si queremos que el n�mero de posiciones del laberinto atravesadas sea m�nimo, �podemos
aplicar el algoritmo A*  Indicad una funci�n heur�stica admisible para este problema.

[METODOS_BUSQUEDA]


## Bibliograf�a

Bibliograf�a
Russell, S. J., & Norvig, P. (2020). Artificial Intelligence: A Modern Approach (4th Edition). Pearson.
Thrun, S., Burgard, W., & Fox, D. (2005). Probabilistic Robotics. MIT Press.
Cormen, T. H., Leiserson, C. E., Rivest, R. L., & Stein, C. (2009). Introduction to Algorithms (3rd Edition). MIT Press.
