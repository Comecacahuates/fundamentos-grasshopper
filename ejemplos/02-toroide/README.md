# Toroide

Una manera de caracterizar un toriode es definiendo su **radio interior**
y **radio exterior**.

![Parámetros de un toroide](./figuras/01-toriode.png)

Ponemos en el lienzo nuestros parámetros: el radio interior
y el radio exterior.

![Parámetros del toroide](./figuras/02-toriode.png)

Podemos crear el toroide como una superficie de revolución,
para lo que necesitamos una sección de la superficie,
que tiene forma circular.

![Sección del toroide](./figuras/03-toroide.png)

El centro de la sección es un valor derivado del radio interior
y el radio exterior.

```
centro = punto(x_centro, 0, 0)
x_centro = promedio(radio_interior, radio_exterior)
```

![Centro de la sección](./figuras/04-toroide.png)

El radio de la sección también se deriva de los parámetros iniciales.

```
radio = (radio_exterior - radio_interior) / 2
```

![Radio de la sección](./figuras/05-toroide.png)

Con estos datos, podemos crear el círculo de la sección.

![Sección del toroide](./figuras/06-toroide.png)

Para corregir la orientación del círculo,
creamos un plano XZ en el centro de la sección,
y lo usamos como base para el círculo.

![Orientación de la sección del toroide](./figuras/07-toroide.png)

Ahora podemos crear un arreglo polar de la sección para obtener la forma
general del toroide.

![Eje de revolución](./figuras/08-toroide.png)

Con el arreglo de las secciones, creamos una superficie de transición.

![Toroide](./figuras/09-toroide.png)

Modificamos las opciones de la superficie de transición para crear una
superficie cerrada.

![Toroide](./figuras/10-toroide.png)
