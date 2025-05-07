# Estructura

![Estructura](./figuras/01-estructura.png)

## Análisis

Para facilitar el análisis de la estructura anterior, podemos considerar
un caso similar pero más simple.

![Estructura simplificada](./figuras/02-estructura.png)

Podemos descomponer la estructura en diferentes juegos de líneas rectas,
que podemos resolver por separado y simplificar la construcción.

Líneas A:

![Líneas A](./figuras/03-estructura.png)

Líneas B:

![Líneas B](./figuras/04-estructura.png)

Líneas C:

![Líneas C](./figuras/05-estructura.png)

Líneas D:

![Líneas D](./figuras/06-estructura.png)

Líneas E:

![Líneas E](./figuras/07-estructura.png)

Para crear las líneas, necesitamos dos juegos de puntos.

Puntos P:

![Puntos P](./figuras/08-estructura.png)

Puntos Q:

![Puntos Q](./figuras/09-estructura.png)

Para crear los puntos P, necesitamos una superficie base, además del número
de puntos que habrá en cada dirección.

![Superficie base](./figuras/10-estructura.png)

Para crear los puntos Q, necesitamos también la altura de la estructura.

![Altura](./figuras/11-estructura.png)

## Implementación

Ponemos en el lienzo los parámetros que definimos:

- superficie base
- divisiones en U (número entero)
- divisiones en V (número entero)
- altura (número real)

![Parámetros](./figuras/12-estructura.png)

### Puntos P

Para crear los puntos P, necesitamos dividir la superficie base con el número
de divisiones que definimos en los parámetros.

![Puntos P](./figuras/13-estructura.png)

Cuando dividimos la superficie, los puntos quedan organizados en un árbol
en el que el número de ramas está definido por las divisiones en U,
y el número de puntos por rama, por el número de divisiones en V.
Dicho de otro modo, los puntos quedan organizados en columnas.

![Puntos P](./figuras/14-estructura.png)

### Líneas A

La organización de los puntos P nos sirven para crear las líneas A
de manera directa mediante polilíneas.

![Líneas B](./figuras/15-estructura.png)

### Líneas B

Las líneas B también se pueden crear a partir de los puntos P,
sin embargo, antes tenemos que organizarlos de otro modo.

![Líneas B](./figuras/16-estructura.png)

![Líneas B](./figuras/17-estructura.png)

### Puntos Q

Los puntos Q se crean a partir de los puntos P, por lo tanto,
necesitamos encontrar una relación entre estos.

Podemos notar que cada punto Q se encuentra en el centro de 4 puntos P que
se forman un cuadrilátero. A continuación, se muestra la relación de cada
punto Q con los puntos P, es decir, de qué puntos P depende cada punto Q
para poder ser creado.

![Puntos Q](./figuras/18-estructura.png)

Con este análisis, vemos que necesitamos reorganizar el árbol de puntos P
para agruparlos de este modo.

![Puntos Q](./figuras/19-estructura.png)

En este ejemplo, necesitaríamos los puntos organizados en un árbol
de este modo:

```
Rama 0:
  {0;0}
  {0;1}
  {1;1}
  {1;0}

Rama 1:
  {0;1}
  {0;2}
  {1;2}
  {1;1}

Rama 2:
  {0;2}
  {0;3}
  {1;3}
  {1;2}

Rama 3:
  {1;0}
  {1;1}
  {2;1}
  {2;0}

Rama 4:
  {1;1}
  {1;2}
  {2;2}
  {2;1}

Rama 5:
  {1;2}
  {1;3}
  {2;3}
  {2;2}
```

Podemos tomar como referencia el primer punto de cada rama que queremos formar
y obtener los demás puntos con su dirección relativa respecto a este.

```
Rama 0:
  {0;0}  {+0;+0} dirección de referencia
  {0;1}  {+0;+1} dirección relativa
  {1;1}  {+1;+1} dirección relativa
  {1;0}  {+1;+0} dirección relativa

Rama 1:
  {0;1}  {+0;+0} dirección de referencia
  {0;2}  {+0;+1} dirección relativa
  {1;2}  {+1;+1} dirección relativa
  {1;1}  {+1;+0} dirección relativa

Rama 2:
  {0;2}  {+0;+0} dirección de referencia
  {0;3}  {+0;+1} dirección relativa
  {1;3}  {+1;+1} dirección relativa
  {1;2}  {+1;+0} dirección relativa

Rama 3:
  {1;0}  {+0;+0} dirección de referencia
  {1;1}  {+0;+1} dirección relativa
  {2;1}  {+1;+1} dirección relativa
  {2;0}  {+1;+0} dirección relativa

Rama 4:
  {1;1}  {+0;+0} dirección de referencia
  {1;2}  {+0;+1} dirección relativa
  {2;2}  {+1;+1} dirección relativa
  {2;1}  {+1;+0} dirección relativa

Rama 5:
  {1;2}  {+0;+0} dirección de referencia
  {1;3}  {+0;+1} dirección relativa
  {2;3}  {+1;+1} dirección relativa
  {2;2}  {+1;+0} dirección relativa
```

![Agrupas puntos P](./figuras/20-estructura.png)

Ya que tenemos agrupados los puntos P, podemos calcular el promedio
de cada grupo de puntos y moverlos en dirección perpendicular a la superficie.

![Puntos Q](./figuras/21-estructura.png)

Teniendo los puntos P y los puntos Q, podemos crear los juegos de líneas C.

![Líneas C](./figuras/22-estructura.png)

De manera similar a las líneas A y B, vamos a construir las líneas D y E,
pero usando los puntos Q.

![Líneas D](./figuras/23-estructura.png)

![Líneas E](./figuras/24-estructura.png)

![Estructura](./figuras/25-estructura.png)

[Volver »](..)
