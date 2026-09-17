---
subject: modelado-y-simulacion
topic: Conjuntos compactos y teorema de Heine-Borel
sources:
  - 01B conjuntos compactos.pdf
  - 01D Lectura 3.pdf
  - 01A Metodos de aproximación Introducción.pdf
  - Geometric_Root_Finding (1).pdf
updated: 2026-08-21
---

# Conjuntos compactos

La **compacidad** es "el territorio de la certidumbre": la propiedad estructural
que permite controlar el comportamiento global de las funciones y transforma la
*posibilidad* en *certeza*.

## Intuición

Un conjunto compacto es un espacio **sin rutas de escape**: no permite que una
sucesión de puntos se "escape al infinito" ni se acerque a un límite que esté
fuera del propio conjunto. Es un universo autocontenido.

## Definiciones equivalentes

- **Secuencial (espacios métricos):** un conjunto $K$ es compacto si toda
  sucesión en $K$ tiene una subsucesión convergente cuyo límite pertenece a $K$.
- **Cubrimiento (universal):** $K$ es compacto si todo cubrimiento abierto de $K$
  admite un subcubrimiento finito.

## Teorema de Heine-Borel (la regla de oro en $\mathbb{R}^n$)

> Un conjunto $K \subset \mathbb{R}^n$ es compacto **si y solo si** es cerrado y acotado.

- **Cerrado:** contiene todos sus puntos límite (incluye su frontera).
- **Acotado:** puede encerrarse dentro de una bola de radio finito.

Ejemplos compactos: disco cerrado $\{x^2+y^2 \le 1\}$, segmento $[a,b]$, rectángulo
$[a,b]\times[c,d]$. Contraejemplo: $[0,1] \cup (2,3)$ **no** es compacto porque $(2,3)$
no es cerrado.

## Por qué importa (las garantías de la compacidad)

Dentro de un compacto desaparecen las incertidumbres del infinito:

1. **Existencia de extremos** → [[teorema-de-weierstrass]] (toda función continua
   alcanza máximo y mínimo absolutos).
2. **Control de funciones** → si $g \in C^1(K)$, su derivada está acotada
   ($|g'(x)| \le M$), lo que da una [[condicion-de-lipschitz]] uniforme.
3. **Convergencia garantizada** → base del [[teorema-del-punto-fijo-de-banach]].
4. **Sistemas dinámicos** → un conjunto compacto invariante confina las
   trayectorias (no explotan) y garantiza atractores (ver [[sistemas-dinamicos]]).

Además, la imagen continua de un compacto es compacta, y la continuidad sobre un
compacto se vuelve **uniforme**.

Relacionado: [[condicion-de-lipschitz]], [[iteracion-y-convergencia]].
