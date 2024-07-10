# Operadores lógicos

Existen tres operadores que podemos usar para formar condiciones más complejas
combinando condiciones simples. Algunos ejemplos de estas condiciones son:

- ¿La distancia entre el $P_1$ y el origen es menor a 10 **y**
  su coordenada $x$ es positiva?
- ¿El punto $P_1$ está adentro de la curva $C_1$ **o**
  adentro de la curva $C_2$?
- ¿El plano $Pln_1$ **no** intersecta a la superficie $S_1$?

## Conjunción

La conjunción de dos o más condiciones es verdadera únicamente
si todas las condiciones son verdaderas.

$$conjunción = condición_1 \textbf{Y} condición_2$$

| $condición_1$ | $condición_2$ | $conjunción$ |
| ------------- | ------------- | ------------ |
| $F$           | $F$           | $F$          |
| $F$           | $V$           | $F$          |
| $V$           | $F$           | $F$          |
| $V$           | $V$           | $V$          |

## Disyunción

La disyunción de dos o más condiciones es verdadera siempre que
al menos una de las condiciones sea verdadera.

$$disyunción = condición_1 \textbf{O} condición_2$$

| $condición_1$ | $condición_2$ | $disyunción$ |
| ------------- | ------------- | ------------ |
| $F$           | $F$           | $F$          |
| $F$           | $V$           | $V$          |
| $V$           | $F$           | $V$          |
| $V$           | $V$           | $V$          |

## Negación

La negación de una condición es verdadera cuando la condición es falsa,
y falsa cuando la condición es verdadera.

$$negación = \textbf{NO} condición$$

| $condición$ | $negación$ |
| ----------- | ---------- |
| $F$         | $V$        |
| $V$         | $F$        |

## Ejemplo

> ¿La distancia del punto $P_1$ al origen es mayor a 10
> **y** su coordenada $x$ es positiva,
> **o** el punto $P_1$ **no** está adentro de la curva $C_1$?

$condición_1 =$ la distancia del punto $P_1$ al origen es mayor a $10$

$condición_2 =$ la coordenaa $x$ del punto $P_1$ es positiva

$condición_3 =$ el punto $P_1$ está adentro de la curva $C_1$

$$condición = (condición_1 \textbf{Y} condición_2) \textbf{O} (\textbf{NO} condición_3)$$

[Ejercicios »](./ejercicios)

[Volver »](..)
