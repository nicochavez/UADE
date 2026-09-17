---
subject: modelado-y-simulacion
topic: Teorema del punto fijo de Banach
sources:
  - 01B conjuntos compactos.pdf
  - 01D Lectura 3.pdf
  - 01D Metodo del punto Fijo.pdf
  - 01A Metodos de aproximación Introducción.pdf
updated: 2026-08-07
---

# Teorema del punto fijo de Banach

Es "la cima del ascenso a la certidumbre": si combinamos un espacio con la
estructura adecuada y una función con el comportamiento adecuado, obtenemos
certeza absoluta.

## Punto fijo

Un **punto fijo** $x^*$ de una función satisface $f(x^*) = x^*$: al evaluarlo en la
función se obtiene el mismo punto.

## Enunciado

Si:

1. $X$ es un espacio métrico **completo** (todo compacto en un espacio métrico
   lo es), y
2. $f: X \to X$ es una función **contractiva** (ver [[condicion-de-lipschitz]]),

entonces:

1. **Existencia y unicidad:** existe un *único* punto fijo $x^* \in X$ tal que
   $f(x^*) = x^*$.
2. **Convergencia garantizada:** para *cualquier* punto inicial $x_0$, la
   sucesión $x_{n+1} = f(x_n)$ converge a $x^*$.

## Garantía de velocidad

El teorema no solo asegura que se llega al destino, sino cuán rápido. La prueba
da una cota explícita del error en cada paso:

$$
d(x_n, x^*) \le k^n \cdot d(x_0, x^*)
$$

El error disminuye **exponencialmente**; una constante de contracción $k$ más
pequeña significa convergencia mucho más rápida (comparar $k = 0.3$ vs $k = 0.8$).

## Ejemplo numérico

$T(x) = \tfrac{1}{2}x + 1$ en $\mathbb{R}$: es contractiva con $k = \tfrac{1}{2}$. Su punto fijo es
$x = \tfrac{1}{2}x + 1 \Rightarrow x = 2$. Partiendo de $x_0 = 10$, la sucesión 10, 6, 4, 3, 2.5, …
converge a 2.

Es el fundamento teórico del [[metodo-del-punto-fijo]] y explica por qué los
[[conjuntos-compactos]] "transforman la posibilidad en certeza".

Relacionado: [[iteracion-y-convergencia]], [[teorema-de-weierstrass]].
