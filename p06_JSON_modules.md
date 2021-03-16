# Práctica 6. JSON. Módulos.
### Factor de ponderación: 7

### Objetivos
Los objetivos de esta práctica son:
  
* Conocer el formato JSON y las herramientas de JS que permiten su tratamiento
* Trabajar con arrays y los métodos correspondientes a este tipo de objetos
* Ser capaz de procesar ficheros de texto en JavaScript
* Practicar la documentación de programas usando JSDoc
* Practicar el uso de ESLint para garantizar la coherencia del estilo del código desarrollado
* Aprender a depurar programas JS en Visual Studio Code

### Rúbrica de evaluacion del ejercicio
Se señalan a continuación los aspectos más relevantes (la lista no es exhaustiva)
que se tendrán en cuenta a la hora de evaluar esta práctica:

* El comportamiento del programa debe ajustarse a lo solicitado en este enunciado.
* Deben usarse estructuras de datos adecuadas para representar los diferentes elementos que intervienen en el problema.
* Capacidad del programador(a) de introducir cambios en el programa desarrollado.
* Se comprobará que el código que el alumnado escribe se adhiere a las reglas de la Guía de Estilo.
* El código ha de estar documentado con [JSDoc](https://jsdoc.app/). 
  Haga que la documentación del programa generada con JSDoc esté disponible a través de una web alojada en su máquina IaaS de la asignatura.
* El alumnado ha de acreditar su capacidad para configurar y ejecutar ESLint en sus programas.
* El alumnado ha de acreditar que sabe depurar sus programas usando Visual Studio Code.

### Indicaciones de caracter general
A la hora de resolver los problemas que se le proponen, trate de usar exclusivamente las características de
JavaScript que ha estudiado en clase o bien en el material que se le ha pedido que estudie.

Descarte soluciones avanzadas y nunca utilice código que no sea Ud. capaz de comprender y explicar a otra
persona.

### Lectura/Escritura de ficheros de texto en JavaScript

### Tratamiento de Datos. Formato JSON.
Comience por estudiar el capítulo 10 
[Modules](https://eloquentjavascript.net/10_modules.html) de Eloquent JavaScript y
el 
[correspondiente apartado](https://javascript.info/modules)
del Modern JS Tutorial.

Estudie a continuación el tutorial
[Read/Write JSON Files with Node.js](https://medium.com/@osiolabs/read-write-json-files-with-node-js-92d03cc82824).

**1.-** Comience por escribir diferentes módulos (ficheros `.js`; se propone usar módulos en formato CommonJS), 
uno para cada tipología de datos, en los que se incluyan en
```js
const paises = require('./paises.json')
```

[visualizador on-line de JSON](http://jsonviewer.stack.hu/) 


#####################################3


Todos los programas que se dearrollen en las prácticas de la asignatura deben:

* Tomar su entrada por línea de comandos.
  Nunca los datos de entrada a un programa se 'escribirán' en el código del mismo ni se solicitarán al usuario
	a través de 'menús'.

En estos ejercicios se trabajará con datos estadísticos correspondientes a un partido de baloncesto de la NBA.
Los datos del partido se han obtenido en formato JSON de [stats.nba.com's Box Score](https://stats.nba.com/scores/03/05/2020) 
y corresponden al partido Pacers vs Hawks del 2/5/2016. 
El objeto de estos ejercicios es usar esos datos para extraer alguna información estadística sobre el partido.

**0.-**  Comience la sesión subiendo al entregable del aula virtual el enlace al repositorio de código en el que ha desarrollado la práctica.
En ese mismo repositorio ha de colocar y subir (conmit) al final de esta sesión los ejercicios que realice en la misma.
NO OLVIDE hacer un conmit final porque de ello depende la evaluación de esta sesión.

Configure un fichero `package.json` en el directorio raíz de su repositorio de modo que ejecutando `npm install` queden instaladas todas las dependencias de su proyecto.

Realice cada ejercicio en un fichero JS diferente.

En cada ejercicio, el programa deberá imprimir en consola cierta información estadística sobre el partido.
Haga que cada programa imprima la información nueva además de la que ya entregaba el programa del ejercicio
previo.

Configure una página web estática en su máquina IaaS de la asignatura de modo que el resultado de la ejecución del programa se pueda mostrar (herramientas de desarrollo de Chrome) a través de esa página. 
Coloque en el repo un fichero README.md en el que figure la URL de la página en la que pueden verse los resultados de su programa de forma incremental.

Nombre a los diferentes ficheros con el patrón `pai-lab-05-basket-stats-x-yyy.js` donde `x`corresponde al
número de ejercicio e `yyy` es una cadena de texto (longitud arbitraria) que caracteriza al ejercicio.
P. ej., el primer ejercicio debería figurar en un fichero de nombre `pai-lab-05-basket-stats-01-game.js`

**1.-** Comience por acceder a los datos que se encuentran en el fichero [20160502_Hawks-Pacers-game-data.json](https://github.com/fsande/PAI-Labs-Public-Data/blob/master/20160502_Hawks-Pacers-game-data.json).
Utilice el [visualizador on-line de JSON](http://jsonviewer.stack.hu/) para una primera toma de contacto con
los datos de ese partido.

Utilice los métodos adecuados para almacenar los datos en un objeto JavaScript. 
El objeto resultante contendrá un vector con objetos jugador *player*. 

Desarrolle un primer programa `pai-lab-05-basket-stats-01-game.js` que imprima en pantalla:

* El identificador del partido (debería ser algo como `Game ID: 0021500750`).
* La relación de atributos (*properties*) asociadas con cada jugador.

**2.-** El programa imprimirá además de la información anterior, el resultado final del partido. 
La salida tendrá el formato:

```
Pacers 85
Hawks 99
```

El resultado de cada equipo se puede calcular sumando los siguientes valores para cada jugador de ese equipo:

* 3 puntos por cada canasta triple convertida
* 2 puntos por cada canasta de campo de dos puntos convertida
* 1 punto por cada tiro libre encestado

Nótese que el número de canastas de campo de 2 puntos realizadas es en realidad el número de tiros de campo
descontando los triples (`fieldGoalsMade - threePointersMade`) (porque `fieldGoalsMade` contabiliza canastas
tanto de dos como de tres puntos).

**3.-** El programa imprimirá ahora el nombre del jugador con mayor número de rebotes, y la cantidad
realizada:

```
* Most rebounds: Michael Jordan with 14
```
El número de rebotes es la suma de rebotes defensivos (`reboundsDefensive`) y ofensivos (`reboundsOffensive`).

**4.-** El programa imprimirá el base (**Guard**, G), con el mejor porcentaje de tiros triples:

```
 * Guard (G) with highest 3 point percentage: Larry Bird at %50.00 (1/2)
```

Se imprimirá el nombre del base (jugador que contenga "G" en `positionShort`) que haya intentado al menos un
triple y que tenga el mayor porcentaje de triples en el juego.
El porcentaje de triples es el número de triples logrados dividido por el número de los intentados.

**5.-** El programa imprimirá el número total de de jugadores con al menos una asistencia:

```
There were 14 players that had at least one assist

```

**6.-** El programa imprimirá el equipo que dispuso de más tiros libres:

```
Hawks attempted the most free throws... Pacers: 9 Hawks: 20
```

Tal como se muestra, se ha de imprimir el nombre del equipo que intentó más tiros libres que el otro
así como el número de tiros libres realizados por cada equipo.

**7.-** Imprima la lista de jugadores que hayan tenido más pérdidas de balón (**turnovers**) que asistencias
(*assists*). El formato debiera ser:

```
* Pacers players with more turnovers than assists:
    * Myles Turner has an assist to turnover ratio of 0:1
    * Jordan Hill has an assist to turnover ratio of 3:5
    * Monta Ellis has an assist to turnover ratio of 1:4
    * Lavoy Allen has an assist to turnover ratio of 2:3
    * Solomon Hill has an assist to turnover ratio of 0:1
    * C.J. Miles has an assist to turnover ratio of 1:3
* Hawks players with more turnovers than assists:
    * Paul Millsap has an assist to turnover ratio of 0:2
    * Kyle Korver has an assist to turnover ratio of 1:2
```

[//]: # (===============================================================)

# Ejercicios Práctica 3 Miércoles.

Todos los programas que se dearrollen en las prácticas de la asignatura deben:

* Tomar su entrada por línea de comandos.
  Nunca los datos de entrada a un programa se 'escribirán' en el código del mismo ni se solicitarán al usuario
	a través de 'menús'.
* Disponer de documentación para JSDoc. Esa documentación ha de hacerse disponible a través de una web.
* Utilizar, si es necesario, ESLint para garantizar que el código está formateado conforme a la Guía de Estilo de Google

En estos ejercicios se trabajará con datos estadísticos correspondientes a un partido de baloncesto de la NBA.
Los datos del partido se han obtenido en formato JSON de [stats.nba.com's Box Score](https://stats.nba.com/scores/03/05/2020) 
y corresponden al partido Pacers vs Hawks del 2/5/2016. 
El objeto de estos ejercicios es usar esos datos para extraer alguna información estadística sobre eñ partido.

**0.-**  Comience la sesión subiendo al entregable del aula virtual el enlace al repositorio de código en el que ha desarrollado la práctica.
En ese mismo repositorio ha de colocar y subir (conmit) al final de esta sesión los ejercicios que realice en la misma.
NO OLVIDE hacer un conmit final porque de ello depende la evaluación de esta sesión.

Configure un fichero `package.json` en el directorio raíz de su repositorio de modo que ejecutando `npm install` queden instaladas todas las dependencias de su proyecto.

Realice cada ejercicio en un fichero JS diferente.

En cada ejercicio, el programa deberá imprimir en consola cierta información estadística sobre el partido.
Haga que cada programa imprima la información nueva además de la que ya entregaba el programa del ejercicio
previo.

Configure una página web estática en su máquina IaaS de la asignatura de modo que el resultado de la ejecución del programa se pueda mostrar (herramientas de desarrollo de Chrome) a través de esa página. 
Coloque en el repo un fichero README.md en el que figure la URL de la página en la que pueden verse los resultados de su programa de forma incremental.

Nombre a los diferentes ficheros con el patrón `pai-lab-05-basket-stats-x-yyy.js` donde `x`corresponde al
número de ejercicio e `yyy` es una cadena de texto (longitud arbitraria) que caracteriza al ejercicio.
P. ej., el primer ejercicio debería figurar en un fichero de nombre `pai-lab-05-basket-stats-01-game.js`

**1.-** Comience por acceder a los datos que se encuentran en el fichero [20160502_Hawks-Pacers-game-data.json](https://github.com/fsande/PAI-Labs-Public-Data/blob/master/20160502_Hawks-Pacers-game-data.json).
Utilice el [visualizador on-line de JSON](http://jsonviewer.stack.hu/) para una primera toma de contacto con
los datos de ese partido.

Utilice los métodos adecuados para almacenar los datos en un objeto JavaScript. 
El objeto resultante contendrá un vector con objetos jugador *player*. 

Desarrolle un primer programa `pai-lab-05-basket-stats-01-game.js` que imprima en pantalla:

* El identificador del partido (debería ser algo como `Game ID: 0021500750`).
* La relación de atributos (*properties*) asociadas con cada jugador.

**2.-** Imprima la lista de jugadores que hayan tenido más pérdidas de balón (**turnovers**) que asistencias
(*assists*). El formato debiera ser:

```
* Pacers players with more turnovers than assists:
    * Myles Turner has an assist to turnover ratio of 0:1
    * Jordan Hill has an assist to turnover ratio of 3:5
    * Monta Ellis has an assist to turnover ratio of 1:4
    * Lavoy Allen has an assist to turnover ratio of 2:3
    * Solomon Hill has an assist to turnover ratio of 0:1
    * C.J. Miles has an assist to turnover ratio of 1:3
* Hawks players with more turnovers than assists:
    * Paul Millsap has an assist to turnover ratio of 0:2
    * Kyle Korver has an assist to turnover ratio of 1:2
```

**3.-** El programa imprimirá el equipo que dispuso de más tiros libres:

```
Hawks attempted the most free throws... Pacers: 9 Hawks: 20
```

Tal como se muestra, se ha de imprimir el nombre del equipo que intentó más tiros libres que el otro
así como el número de tiros libres realizados por cada equipo.

**4.-** El programa imprimirá el número total de de jugadores con al menos una asistencia:

```
There were 14 players that had at least one assist

```

**5.-** El programa imprimirá el base (**Guard**, G), con el mejor porcentaje de tiros triples:

```
 * Guard (G) with highest 3 point percentage: Larry Bird at %50.00 (1/2)
```

Se imprimirá el nombre del base (jugador que contenga "G" en `positionShort`) que haya intentado al menos un
triple y que tenga el mayor porcentaje de triples en el juego.
El porcentaje de triples es el número de triples logrados dividido por el número de los intentados.

**6.-** El programa imprimirá ahora el nombre del jugador con mayor número de rebotes, y la cantidad
realizada:

```
* Most rebounds: Michael Jordan with 14
```
El número de rebotes es la suma de rebotes defensivos (`reboundsDefensive`) y ofensivos (`reboundsOffensive`).

**7.-** El programa imprimirá además de la información anterior, el resultado final del partido. 
La salida tendrá el formato:

```
Pacers 85
Hawks 99
```
El resultado de cada equipo se puede calcular sumando los siguientes valores para cada jugador de ese equipo:

* 3 puntos por cada canasta triple convertida
* 2 puntos por cada canasta de campo de dos puntos convertida
* 1 punto por cada tiro libre encestado

Nótese que el número de canastas de campo de 2 puntos realizadas es en realidad el número de tiros de campo
descontando los triples (`fieldGoalsMade - threePointersMade`) (porque `fieldGoalsMade` contabiliza canastas
tanto de dos como de tres puntos).

[//]: # (===============================================================)

Soluciones Martes:

1:
Match id: 0021500750
Each players has the following properties: 
firstName
lastName
jerseyNumber
personID
positionShort
positionFull
minutes
seconds
fieldGoalsMade
fieldGoalsAttempted
playerCode
freeThrowsMade
freeThrowsAttempted
threePointersMade
threePointersAttempted
reboundsOffensive
reboundsDefensive
assists
fouls
steals
turnovers
teamTurnovers
blocks
startingPosition
teamName

2:
The result of the match was: 
Pacers -> 96
Hawks -> 102

3:
The player with most rebounds is Lavoy Allen with  14

4:
Guard (G) with highest 3 point percentage:
George Hill  with  50  %

5:
There were 14 players that had at least one assist
