---
subject: modelado-y-simulacion
topic: Polinomio interpolante de Lagrange
sources:
  - "03A Modelado_con_Lagrange_y_Diferencias_Finitas.pdf"
  - "03B Interpolación_y_Derivación_de_Datos_Discretos.pdf"
---

# Polinomio de Lagrange

Construcción explícita del polinomio de [[interpolacion-polinomica]]: dado un
conjunto de puntos $(x_i, y_i)$, se arma como una **suma ponderada** de
polinomios base, uno por cada punto.

$$P(x) = \sum_{i=0}^{n} y_i \, L_i(x)$$

## Los polinomios base $L_i(x)$

Cada $L_i(x)$ actúa como un "interruptor matemático": vale $1$ en su propio
nodo $x_i$ y $0$ en todos los demás nodos $x_j$ ($j \ne i$). Así, al sumar,
cada término $y_i L_i(x)$ solo "se enciende" cerca de su punto y no interfiere
con los demás.

$$L_i(x) = \prod_{j=0,\, j\ne i}^{n} \frac{x - x_j}{x_i - x_j}$$

- El numerador $\prod (x-x_j)$ asegura que $L_i$ se anule en todo $x_j$ con
  $j \ne i$.
- El denominador $\prod(x_i-x_j)$ normaliza para que $L_i(x_i) = 1$.

La curva final es la suma exacta de estos términos ponderados: cada
$y_i L_i(x)$ pasa por $y_i$ en $x_i$ y es cero en los demás nodos, y su suma
reproduce todos los puntos simultáneamente.

## Implementación (Python)

```python
def polinomio_lagrange(x, x_puntos, y_puntos):
    n = len(x_puntos)
    P = 0
    for i in range(n):
        li = 1
        for j in range(n):
            if i != j:
                li *= (x - x_puntos[j]) / (x_puntos[i] - x_puntos[j])
        P += y_puntos[i] * li
    return P
```

El bucle externo (`for i`) recorre cada punto para construir la suma
$\sum y_i L_i(x)$; el bucle interno (`for j`) construye el polinomio base
$L_i(x)$.

### Ejemplo

Con `x_puntos = [0, 1, 2, 3, 4]` y `y_puntos = [1, 2, 0, 2, 3]`, el polinomio
reconstruido es:

$$P(x) = 0.5833x^4 - 4.5x^3 + 11.417x^2 - 9.5x + 1$$

## Costo y alternativa

Lagrange es directo de entender y programar, pero recalcula todo desde cero
si se agrega un nuevo punto. La forma de **diferencias divididas de Newton**
construye el mismo polinomio (por unicidad) de manera incremental — se ve en
[[simulador-de-reconstruccion-de-funciones]], que la ofrece como método
alternativo junto con spline cúbico e interpolación lineal por tramos.

Relacionado: [[interpolacion-polinomica]], [[diferencias-finitas]].
