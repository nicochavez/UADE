---
subject: modelado-y-simulacion
topic: Condición de Lipschitz y contracciones
sources:
  - 01B conjuntos compactos.pdf
  - 01A Metodos de aproximación Introducción.pdf
  - 01D Lectura 2.pdf
  - Geometric_Root_Finding (1).pdf
updated: 2026-08-21
---

# Condición de Lipschitz

## Definición

Una función $g: K \to \mathbb{R}$ satisface una **condición de Lipschitz** con
constante $L > 0$ si para todo $x, y$ en un conjunto compacto $K$:

$$
|g(x) - g(y)| \le L \cdot |x - y|
$$

La constante $L$ actúa como un "límite de velocidad" global de la función:
limita la amplificación de la distancia entre las imágenes de dos puntos.
Garantiza que la función no cambia de manera demasiado abrupta.

## Vínculo con la compacidad

Si $g \in C^1(K)$ y $K$ es [[conjuntos-compactos|compacto]], la derivada $g'$ es
continua sobre un cerrado y acotado, por lo que está acotada. Entonces podemos
tomar $L = \max |g'(x)|$. La compacidad **garantiza** que una sola $L$ funcione
uniformemente en todo el conjunto.

## Contracción (el caso especial L < 1)

Una función $f: X \to X$ es una **contracción** (aplicación contractiva) si existe
una constante $k \in [0, 1)$ tal que para todo $x, y$:

$$
d(f(x), f(y)) \le k \cdot d(x, y)
$$

Intuición: una contracción es una "máquina de encoger" — al aplicarla, la
distancia entre cualquier par de puntos se reduce por un factor garantizado $k$.

Cuando $L < 1$ la función es contractiva, y esa es la **clave de la
convergencia**: la iteración $x_{n+1} = g(x_n)$ converge (ver
[[teorema-del-punto-fijo-de-banach]]).

### Ejemplo

$f(x) = \tfrac{1}{2}x$ en $X = [0,1]$: $|f(x) - f(y)| = \tfrac{1}{2}|x - y|$,
luego $k = \tfrac{1}{2} < 1$. Es contractiva y su único punto fijo es $x^* = 0$.

Relacionado: [[iteracion-y-convergencia]], [[metodo-del-punto-fijo]].
