# Práctica 6. Análisis de Datos. JSON. Módulos.
### Factor de ponderación: 7

### Objetivos
Los objetivos de esta práctica son:
  
* Conocer el formato JSON y las herramientas de JS que permiten su tratamiento
* Trabajar con arrays y los métodos correspondientes a este tipo de objetos
* Ser capaz de procesar ficheros de texto en JavaScript
* Practicar la documentación de programas usando JSDoc
* Practicar el uso de ESLint para garantizar la coherencia del estilo del código desarrollado
* Practicar la depuración de programas JS en Visual Studio Code

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

Puesto que en la práctica anterior ya se ha trabajado con módulos CommonJS se propone aquí que
la aplicación que desarrolle se organice utilizando
[módulos ES6](https://blog.logrocket.com/es-modules-in-node-today/)

Configure un fichero `package.json` en el directorio raíz de su repositorio de modo que ejecutando 
`npm install` queden instaladas todas las dependencias de su proyecto.

### Análisis de Datos. Formato JSON.

En esta práctica se trabajará con datos estadísticos correspondientes a un partido de baloncesto de la NBA.
Los datos del partido se han obtenido en formato JSON de 
[stats.nba.com's Box Score](https://stats.nba.com/scores/03/05/2020) 
y corresponden al partido Pacers vs Hawks del 2/5/2016. 
El objeto de este programa es usar esos datos para extraer información estadística sobre el partido.

En cada ejercicio, el programa deberá imprimir en consola cierta información estadística sobre el partido.
Haga que cada uno de los pasos siguientes se implemente a través de una función diferente.
Las diferentes funciones han de extraer y procesar la información requerida en cada caso y entregarla a otra
función *orquestadora* del proceso que será la encargada de imprimir la información obtenida en pantalla.

## El partido
**1.-** Comience por acceder a los datos que se encuentran en el fichero 
[20160502_Hawks-Pacers-game-data.json](https://github.com/fsande/PAI-Labs-Public-Data/blob/master/20160502_Hawks-Pacers-game-data.json).
Utilice el [visualizador on-line de JSON](http://jsonviewer.stack.hu/) para una primera toma de contacto con
los datos de ese partido.

Almacene los datos en una estructura de datos adecuada para su procesamiento.
La estructura contendrá un vector con objetos jugador *player*. 

Desarrolle programa `pai-lab-06-basket-stats.js` que imprima en pantalla:

* El identificador del partido (debería ser algo como `Game ID: 0021500750`).
* La relación de atributos (*properties*) asociadas con cada jugador.

## El Resultado
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

## Máximo reboteador
**3.-** El programa imprimirá ahora el nombre del jugador con mayor número de rebotes, y la cantidad
realizada:

```
* Most rebounds: Michael Jordan with 14
```
El número de rebotes es la suma de rebotes defensivos (`reboundsDefensive`) y ofensivos (`reboundsOffensive`).

## Escolta con mejor porcentaje de tiros libres
**4.-** El programa imprimirá el Escolta (**Guard**, G), con el mejor porcentaje de tiros triples:

```
 * Guard (G) with highest 3 point percentage: Larry Bird at %50.00 (1/2)
```

Se imprimirá el nombre del escolta (jugador que contenga "G" en `positionShort`) que haya intentado al menos un
triple y que tenga el mayor porcentaje de triples en el juego.
El porcentaje de triples es el número de triples logrados dividido por el número de los intentados.

## Jugadores con al menos una asistencia
**5.-** El programa imprimirá el número total de de jugadores con al menos una asistencia:

```
There were 14 players that had at least one assist

```

## Equipo que realizó más tiros libres
**6.-** El programa imprimirá el equipo que dispuso de más tiros libres:

```
Hawks attempted the most free throws... Pacers: 9 Hawks: 20
```

Tal como se muestra, se ha de imprimir el nombre del equipo que intentó más tiros libres que el otro
así como el número de tiros libres realizados por cada equipo.

## Jugadores con más pérdidas de balón que asistencias
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
