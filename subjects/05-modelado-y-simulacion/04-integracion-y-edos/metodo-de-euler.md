---
subject: modelado-y-simulacion
topic: Método de Euler para EDOs
sources:
  - 06A Metodos_de_Runge_Kutta.pdf
updated: 2026-09-18
---

# Método de Euler

El procedimiento más directo para resolver numéricamente un problema de valor
inicial $y' = f(x, y)$, $y(x_0) = y_0$ (ver
[[ecuaciones-diferenciales-ordinarias]]). Es el Runge-Kutta de **primer orden**.

## Fórmula

Usa la pendiente calculada **exactamente al inicio** del intervalo para
proyectar el siguiente punto en línea recta:

$$
y_{n+1} = y_n + h\, f(x_n, y_n), \qquad x_{n+1} = x_n + h
$$

- $y_{n+1}$: valor en el siguiente paso.
- $y_n$: valor en el paso actual.
- $h$: tamaño del paso.
- $f(x_n, y_n)$: derivada (pendiente) en el punto actual.

En la forma general $y_{i+1} = y_i + \phi h$, Euler toma $\phi = f(x_i, y_i)$.
Su supuesto implícito es que **la pendiente es constante** en todo el
intervalo $h$.

## La falla inherente: pendiente constante

La simplicidad es también su mayor debilidad. La curva verdadera cambia de
pendiente dentro de $[x_i, x_{i+1}]$, y Euler lo ignora. La diferencia entre
la recta predicha y la curva real genera un error **en cada paso**, y ese
error **se propaga y acumula**: cada paso arranca desde un punto que ya estaba
corrido, así que la solución numérica se aleja cada vez más de la verdadera.

## Reducir $h$ ayuda, pero no alcanza

Con $h$ más chico la pendiente cambia menos en cada intervalo y la precisión
mejora (`06A` compara $h = 0.5$ con $h = 0.25$). Pero:

- el **costo computacional** aumenta drásticamente (más pasos), y
- **no se elimina** la fuente fundamental del error.

Dato estándar (no figura en las diapositivas): el error global de Euler es
$O(h)$, así que para dividir el error por 10 hacen falta 10 veces más pasos.
Por eso conviene mejorar **cómo se estima la pendiente**, que es lo que hacen
el [[metodo-de-heun]] y el [[metodo-de-runge-kutta-4]].

## Ejemplo: $y' = x + y$, $y(0) = 1$, $h = 0.1$

Primer paso: $y_1 = 1 + 0.1\cdot(0 + 1) = 1.1$ (valor exacto: $1.110342$).
Segundo paso: $y_2 = 1.1 + 0.1\cdot(0.1 + 1.1) = 1.22$ (exacto: $1.242806$).

En $x = 1$ Euler da $3.187485$ contra el exacto $3.436564$, un error de
$\approx 0.249$ (tabla completa en [[ecuaciones-diferenciales-ordinarias]]).

## Implementación (Python, esquema propio)

```python
def euler(f, x0, y0, h, n):
    x, y = x0, y0
    for _ in range(n):
        y = y + h * f(x, y)
        x = x + h
    return y
```
