# Armadura

Si observamos la siguiente armadura, podemos notar que está formada por
varias estructuras cuya forma es parecida.

![Armadura](./figuras/01-armadura.png)
![Armadura](./figuras/02-armadura.png)

Podemos darnos cuenta de que la lógica de la creación de cada una de estas
estructuras es la misma, así que podemos enfocarnos en analizar una sola.

![Una estructura de la armadura](./figuras/03-armadura.png)

Para facilitar el análisis de esta estructura,
podemos utilizar una representación más abstracta de su forma.

![Estructura](./figuras/04-armadura.png)

Podemos notar que la forma de estas estructuras está formada por líneas
y polilíneas. Para esto, necesitamos identificar las vértices que vamos
a utilizar para crearlas.

![Listas de puntos](./figuras/05-armadura.png)

Los puntos están organizados en dos listas de puntos: A y B.

Para crear las líneas verticales, basta con crear líneas iniciando
en cada punto de A a su correspondiente punto de B.

![Líneas verticales](./figuras/06-armadura.png)

```
línea(A0, B0)
línea(A1, B1)
línea(A2, B2)
línea(A3, B3)
línea(A4, B4)
línea(A5, B5)
línea(A6, B6)
```

Para crear las líneas superiores, podemos crear una polilínea
con los puntos de la lista A.

![Líneas superiores](./figuras/07-armadura.png)

```
polilínea([A0, A1, A2, A3, A4, A5, A6])
```

Para crear las líneas inferiores, podemos crear una polilínea
con los puntos de la lista B.

![Líneas inferiores](./figuras/08-armadura.png)

```
polilínea([B0, B1, B2, B3, B4, B5, B6])
```

Los líneas inclinadas están formadas por puntos de ambas listas.
Para crearlas como una polilínea, necesitamos extraer ciertos puntos
de cada una de las listas y en cierto orden.

![Líneas inclinadas](./figuras/09-armadura.png)

| A      | B      | Elemento seleccionado |
| ------ | ------ | --------------------- |
| A0     | **B0** | B0                    |
| **A1** | B1     | A1                    |
| A2     | **B2** | B2                    |
| **A3** | B3     | A3                    |
| A4     | **B4** | B4                    |
| **A5** | B5     | A5                    |
| A6     | **B6** | B6                    |

Ahora podemos definir los parámetros que vamos a utilizar
para crear la estructura. Para que la estructura pueda tener diferentes formas,
necesitamos poder amoldarla a una curva, así que necesitamos una **curva base**.

Por simplicidad, podemos utilizar el plano universal para determinar
la altura que tendrá la estructura, así que no necesitamos definir otro
parámetro para esto.

Por último, necesitamos el **número de divisiones**
que va a tener la estructura.

Podemos estos parámetros en el lienzo.

![Parámetros](./figuras/10-armadura.png)

Para obtener los puntos superiores, podemos dividir la curva base.

![Puntos superiores](./figuras/11-armadura.png)

Los puntos inferiores los podemos obtener si proyectamos los puntos superiores
sobre el plano base.

![Puntos inferiores](./figuras/12-armadura.png)

Las líneas verticales las podemos crear fácilmente
con estas dos listas de puntos.

![Líneas verticales](./figuras/13-armadura.png)

Para las líneas superiores, se puede crear una polilínea a través
de la lista de puntos A y se explota en líneas individuales.

![Líneas superiores](./figuras/14-armadura.png)

Las líneas inferiores se pueden crear del mismo modo pero usando
la lista de puntos B.

![Líneas inferiores](./figuras/15-armadura.png)

Para crear las líneas inclinadas, primero necesitamos extraer los vértices
utilizando las listas A y B. Para esto, necesitamos crear un patrón
para seleccionar los puntos con la lógica que definimos anteriormente.

| Índice | Lista 0 (A) | Lista 1 (B) | Elemento seleccionado | Patrón de selección |
| ------ | ----------- | ----------- | --------------------- | ------------------- |
| 0      | ~~A0~~      | **B0**      | B0 (lista 1)          | 1                   |
| 1      | **A1**      | ~~B1~~      | A1 (lista 0)          | 0                   |
| 2      | ~~A2~~      | **B2**      | B2 (lista 1)          | 1                   |
| 3      | **A3**      | ~~B3~~      | A3 (lista 0)          | 0                   |
| 4      | ~~A4~~      | **B4**      | B4 (lista 1)          | 1                   |
| 5      | **A5**      | ~~B5~~      | A5 (lista 0)          | 0                   |
| 6      | ~~A6~~      | **B6**      | B6 (lista 1)          | 1                   |

El patrón que se repite es **1, 0**, que se repite hasta alcanzar
el número de puntos que hay en cada lista, así que primero calculamos el número
de puntos.

![Número de puntos](./figuras/16-armadura.png)

Ahora escribimos el patrón base y lo repetimos según el número de puntos.

![Patrón de selección](./figuras/17-armadura.png)

Ahora podemos utilizar el patrón para seleccionar los puntos
de las listas A y B.

![Puntos para líneas inclinadas](./figuras/18-armadura.png)

Con los puntos de las líneas, podemos crear las polilíneas
como en los casos anteriores.

![Líneas inclinadas](./figuras/19-armadura.png)

Para crear la armadura completa, necesitamos una curva base
para cada estructura.

![Superficie](./figuras/20-armadura.png)

![Superficie](./figuras/21-armadura.png)

Los datos que necesitamos para crear estar curvas,
necesitamos una superficie base y el número de divisiones
que queremos a lo largo de la superficie.

Ponemos estos parámetros en el lienzo.

![Parámetros](./figuras/22-armadura.png)

De la superficie base, podemos extraer las isocurvas en la dirección U.
Para esto, necesitamos crear puntos a lo largo del dominio U de la superficie
para indicar en qué posición de la curva queremos extraer las curvas.

Primero, extraemos el dominio U de la superficie y lo dividimos
en el número de divisiones que definimos al inicio.

![Coordenadas U](./figuras/23-armadura.png)

Con estas coordenadas, podemos crear los puntos que queremos mapear
sobre la superficie. Para esto, usamos las coordenadas U como coordenadas X.

![Puntos UV](./figuras/24-armadura.png)

Ahora podemos utilizar estos puntos para extraer las isocurvas
de la superficie.

![Isocurvas](./figuras/25-armadura.png)

Podemos utilizar estas curvas, que están amoldadas a la superficie,
como curvas base para crear una estructura en cada una.

![Armadura](./figuras/26-armadura.png)

[Volver »](..)
