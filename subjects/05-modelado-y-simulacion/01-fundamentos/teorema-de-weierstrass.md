---
subject: modelado-y-simulacion
topic: Teorema de Weierstrass (existencia de extremos)
sources:
  - 01D Lectura 3.pdf
updated: 2026-08-07
---

# Teorema de Weierstrass

Es el "Superpoder 1" de la [[conjuntos-compactos|compacidad]] (según
`01D Lectura 3.pdf`).

## Enunciado

Si $K$ es un conjunto **compacto** y $f: K \to \mathbb{R}$ es una función **continua**,
entonces $f$ alcanza su máximo y su mínimo absolutos en $K$. Es decir, existen
$x_m, x_M \in K$ tales que $f(x_m) = \min(f)$ y $f(x_M) = \max(f)$.

## Ejemplo

Demostrar que $f(x) = x^3 - x$ alcanza sus extremos en $[-2, 2]$:

1. $K = [-2, 2]$ es cerrado y acotado en $\mathbb{R}$, por lo tanto **compacto**.
2. $f(x)$ es un polinomio, por lo tanto **continua** en $K$.
3. Conclusión: la existencia de máximo y mínimo absolutos está garantizada.

## Por qué importa

Sin compacidad estas garantías fallan: en un intervalo abierto una función
continua puede no alcanzar un máximo o mínimo (ej. $y = 1/x$ en $(0,1]$). Es la
base de los problemas de **optimización** (garantía de existencia de óptimos).

Relacionado: [[conjuntos-compactos]], [[teorema-del-punto-fijo-de-banach]].
