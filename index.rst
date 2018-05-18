:title: Programacion funcional y logica
:data-transition-duration: 0

----

Hoja Presentacion:
========================

* Mauricio Cortazar
* Programacion funcional y logica

----

Que es una funcion?
========================

Se define funcion a aquel conjunto de instrucciones finitas que se ejecuta solo cuando es llamada (puede ser llamada multiple veces) y hace parte de una aplicacion mas grande.

Puede compararse con las funciones matematicas de tal forma que tenemos la funcion


.. math:: f(x) = x^2

La funcion anterior tiene un nombre(f), recive unos parametros(x) y retorna un valor de salida.

Las funciones en la programacion funcionan exactamente igual, a excepcion que no tengan parametros de entrada o no retornen algun valor.

----

Recursividad
=====================

Para entender el concepto de recursividad, tenemos que tener claro que son funciones y como funcionan. Primero veamos como luce la serie *fibonacci* con funciones matematicas:

.. math:: T(n) =
  \begin{cases}
                                   0 & \text{if $n=0$} \\
                                   1 & \text{if $n=1$} \\
  T({n-1}) + T({n-2}) & \text{if $n>1$}
  \end{cases}


Dejemos de lado las funciones matematicas y usemos programacion para mostrar esta funcion recursiva en python:

.. code:: python

	def T(n):
		  if n == 0: return 0
		  elif n == 1: return 1
		  else: return T(n-1)+T(n-2)

La palabra def corresponde a `Define Function`. Como observamos la funcion T retorna 0 cuando su parametro n es igual a 0, pasa igual cuando n es igual a 1, pero diferente a esos valores, la funcion T por un lado retorna la suma de la funciones T restando en 1 y 2 su argumento respectivamente.

Es recursiva por que T se llama a si misma sin parar hasta que una condicion la detenga. En este caso que su argumento(n) sea igual ya sea a 0 o a 1, de otra forma se ejecutaria infinitas veces colapsando la computadora

----


Historia lenguaje funcional
==============================


Todo empezo con Gottfried Leibniz, quien creó la máquina mecánica de cálculo en el siglo XVII. Esta máquina fue el primer prototipo del dispositivo soñado por Leibniz: una máquina capaz de manipular símbolos y determinar si una frase matemática era o no un teorema, es decir, si una proposición que partía de un supuesto (hipótesis), afirmaba una verdad (tesis) que no es evidente por sí misma.

Para el año de 1928, los matemáticos David Hilbert y Wilhelm Ackermann propusieron el problema de la decisión, que consiste en encontrar un proceso o algoritmo (aún no se tenía la definición formal de algoritmo como tal) general, que decidiera si una fórmula de cálculo de primer orden es un teorema retomando la idea desarrollada por Leibniz.

En 1936, Alonzo Church desarrolló la definición formal de algoritmo bajo el concepto de “calculabilidad efectiva” y diseñó una solución al problema planteado por Hilbert y Ackermann utilizando un modelo de computación denominado por él mismo como Cálculo Lambda, la base fundamental de este paradigma.

En este mismo año, Alan Turing -al igual que Church- desarrollaba una definición de algoritmo y daba solución al problema de la decisión, pero usando las máquinas de Turing, otro modelo de computación que se convertiría en la base de la computación actual, bajo un concepto completamente diferente al cálculo lambda: el problema de la parada. Cabe aclarar que los dos modelos computacionales son equivalentes ya que ambos pueden dar solución a los mismos tipos de problemas.

El paradigma funcional se empezó a desarrollar por el matemático John McCarthy en 1956, para programar los primeros proyectos de inteligencia artificial sobre un computador IBM 704, esto se realizó mediante la implementación de LISP en 1958, lenguaje que aunque no era puramente funcional(Primer lenguaje multiparadigma), todas las características introducidas por él, se convirtieron en las bases para lo que hoy llamamos Paradigma funcional.


----


Enfoque lenguaje funcional
==========================

Los lenguajes funcionales estan enfocados a manipulacion de estructuras de datos siendo estas modificadas a traves de expresiones y no a traves de declaraciones como lo hacen los lenguajes imperativos, se enfocan mas en hacer la tarea y no especificando el como.

Este nuevo enfoque te permite abstraer todas las declaraciones imperativas a un mas alto nivel pero te obligan a pensar a traves de funciones. Muchos lenguajes multiparadigma implementan este esquema funcional, por ejemplo python y muchos lenguajes mas soportan una caracteristica muy comun en los lenguajes funcionales como lo es map, filter, etc.

Tomemos por ejemplo una lista lista = [2, 3, 4] y queremos convertir todos sus valores internos en potencia de 2, imperativamente en python lo hariamos de esta manera:


.. code:: python

		  lista = [2, 3, 4]
		  potencias = []
		  for elemento in lista:
		      potencias.append(elemento**2)

		  >>> potencias = [4, 9, 16]

Pero python tambien nos da la funcion map que nos permite hacerlo todo en una sola linea de codigo


.. code:: python

		  lista = [2, 3, 4]
		  potencias = list(map(lambda x: x**2, lista))

		  >>> potencias = [4, 9, 16]

----


Lista de lenguajes funcionales puros e hibridos
================================================


Algunos lenguajes funcionales puros son:

* Haskell
* Mercury
* Clean
* Miranda
* Disciple

Lenguajes funcionales impuros:

* LISP
* Clojure
* F#
* OCaml
* Scheme
* Scala

----

Algoritmos con paradigma funcional
===================================


El paradigma funcional nos permite implementar a veces los mismos algoritmos que el paradigma imperativo solo que a traves de funciones. Como vimos la serie *fibonacci* la implementamos con funciones recursivas, pero tambien podemos implementarla sin funciones y en este caso el tiempo de ejecucion es mucho mejor:

.. code:: python

		  while a<n:
		      print(a)
			  a, b = b, a + b


Pero a veces la programacion funcional nos presenta alternativas que nos dan mejores resultados. Una de ellas es el famoso algoritmo merge-sort que se nos presenta de manera funcional recursiva y que hace parte de los mejores algoritmos de ordenamiento aqui el ejemplo:

.. code:: python

			def merge(a,b):
				c = []
				while len(a) != 0 and len(b) != 0:

					if a[0] < b[0]:
						c.append(a[0])
						a.remove(a[0])
					else:
						c.append(b[0])
						b.remove(b[0])

				if len(a) == 0:
					c += b
				else:
					c += a
				return c

			def mergesort(x):
				if len(x) == 0 or len(x) == 1:
					return x
				else:
					middle = int(len(x)/2)
					a = mergesort(x[:middle])
					b = mergesort(x[middle:])
					return merge(a,b)

			a = mergesort([10, 1, 20, 3, 6, 7, 6, 9, 11])
			print(a)

----


Campos de aplicacion de la programacion funcional
==================================================


La programacion funcional es muy usada para el desarrollo de software donde el procesamiento de datos es uno de sus principales objetivos, por ejemplo en los sistemas financieros, Inteligencia Artificial(el proposito inicial de LISP era ese), computacion matematica, desarrollo de videojuegos.

Pero no podemos olvidarnos de la influencia que los lenguajes funcionales han aportado en los imperativos, como vimos anteriormente muchos lenguajes implementan la funcion *map* que tiene su procedencia de los lenguajes funcionales.


----


Programacion Logica
====================



A diferencia de la programacion funcional donde es una evolucion de los predicados, en la programacion logica tratamos el concepto de cada predicado y la relacion entre cada predicado


----


Que es la logica matematica?
=============================


Para entender de que va la logica matematica podemos empezar buscando el significado de la logica. Wikipedia nos da lo siguiente: "Método o razonamiento en el que las ideas o la sucesión de los hechos se manifiestan o se desarrollan de forma coherente y sin que haya contradicciones entre ellas.". De acuerdo a lo anterior podemos inferir que la logica matematica busca la verdad a traves de razonamiento sin contradicciones.


----


Que es una proposicion logica?
===============================


Una proposicion logica es una entidad portadora de verdad que se caracteriza por su valor logico y de razonamiento por ejemplo tenemos la frase:

     "Todos los hombres son mortales"
	 "Pedro es un hombre mortal"

En los anteriores enunciados sabemos que la segunda proposicion es logica por que se desarrolla de acuerdo a la idea principal.


Que es un teorema?
===============================

Un teorema es una proposicion que afirma una verdad demostrable.


----


Que es una tabla de verdad?
===============================


Una tabla de verdad es un grafico que nos permite visualizar el valor logico de proposiciones compuestas.


Que es un axioma?
===============================


A diferencia de un teorema, un axioma es una proposición asumida dentro de un cuerpo teórico sobre la cual descansan otros razonamientos y proposiciones deducidas de esas premisas.


Que es una tautologia?
===============================

Una tautología es una fórmula bien formada que resulta verdadera para cualquier interpretación; es decir, para cualquier asignación de valores de verdad que se haga a sus fórmulas atómicas.1​2​ La construcción de una tabla de verdad es un método efectivo para determinar si una fórmula cualquiera es una tautología o no.

Leyes de morgan
=================

En lógica proposicional y álgebra de Boole, las leyes de De Morgan1​2​3​ son un par de reglas de transformación que son ambas reglas de inferencia válidas. Las normas permiten la expresión de las conjunciones y disyunciones puramente en términos de vía negación:

* ¬ es el operador de negación (NO)
* ^ es el operador de conjunción (Y)
* ∨ es el operador de disyunción (O)
* ⇔ es un símbolo metalógico que significa "puede ser reemplazado en una prueba lógica"

----


Historia y origenes de la programacion logica
=================================================


La lógica matemática es la manera más sencilla de expresar formalmente problemas complejos y de resolverlos mediante la aplicación de reglas, hipótesis y teoremas, para el intelecto humano. De ahí que el concepto de "programación lógica". La lógica ha estado muy relacionada históricamente con las computadoras y los lenguajes de programación. Muchas operaciones matemáticas se realizan mecánicamente es decir que existe un algoritmo para resolverse. Otras, son más difíciles de automatizar, por ejemplo, la demostración de un teorema. La invención del Cálculo por parte de Newton y Leibniz mostró a los matemáticos de la época cómo una notación adecuada podía hacer que operaciones muy complicadas se simplificaran, y surgió la idea de que "con una notación adecuada, toda la matemática se puede hacer mecánica, podría concebirse una máquina que hiciera todo el trabajo". Los circuitos de las computadoras son diseñados con la ayuda del álgebra booleana (George Boole). Datos y expresiones booleanos son usados en casi todos los lenguajes de programación para el control de acciones del programa. Proposiciones lógicas se han usado para describir formalmente la semántica de los lenguajes de programación, según el método axiomático que tuvo a Floyd y Hoare como iniciadores. Enunciados lógicos se usan para especificaciones formales que describen el comportamiento de un programa, lo que permite realizar sobre estas pruebas de corrección.

----


Bases de la programacion logica
=================================================


Como hemos visto anteriormente la logica se basa en proposiciones que son verdades obtenidas a traves de un razonamiento. La programacion logica toma todo este modelo de sentencias de muy bajo nivel para su desarrollo, a diferencia de los lenguajes funcionales que como vimos se preocupan en tener las cosas hechas, el modelo logico se nos presenta en declarar cada sentencia que tengamos usando la logica formal. Tomemos nuevamente el ejemplo de pedro y su mortalidad, para poder llegar a la conclusion de que pedro es mortal, debemos leer las 2 setencias propuesta, la primera nos muestra que todos los hombres son mortales y la segunda que pedro es un hombre por lo tanto usando la logica formal inferimos que pedro es mortal.

Esta paradigma aunque parezca simple, nos presenta un metodo distinto a otros paradigmas ya sea por su capacidad de probar o resolver problemas donde el resultado tenga que ser totalmente cierto o falso es decir cuando queremos resultados absolutos.

Entre sus caracteristicas principales, el paradigma logico nos da una validacion de la informacion muy simple comparado con otros lenguajes.

En general, una regla de inferencia es sólo una instrucción para obtener proposiciones verdaderas adicionales de una lista de proposiciones verdaderas.

----

Clausula de Horn
==================


En lógica proposicional, una fórmula lógica es una cláusula de Horn si es una cláusula (disyunción de literales) con, como máximo, un literal positivo. Se llaman así por el lógico Alfred Horn, el primero en señalar la importancia de estas cláusulas en 1951.


Una cláusula de Horn con exactamente un literal positivo es una cláusula "definite"; en álgebra universal las cláusulas "definites" resultan (aparecen) como cuasi-identidades. Una cláusula de Horn sin ningún literal positivo es a veces llamada cláusula objetivo (goal) o consulta (query), especialmente en programación lógica.

Una fórmula de Horn es una cadena textual (string) de cuantificadores existenciales o universales seguidos por una conjunción de cláusulas de Horn.


.. code:: prolog

		  hija(A,B) :- mujer(A), padre(B,A).


		  likes(mary,food).
		  likes(mary,wine).
		  likes(john,wine).
		  likes(john,mary).



		  | ?- likes(mary,food).
		  yes.
		  | ?- likes(john,wine).
		  yes.
		  | ?- likes(john,food).
		  no.
