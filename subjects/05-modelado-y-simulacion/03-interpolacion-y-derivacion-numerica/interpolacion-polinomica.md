---
subject: modelado-y-simulacion
topic: Interpolación polinómica
sources:
  - "03A Modelado_con_Lagrange_y_Diferencias_Finitas.pdf"
  - "03B Interpolación_y_Derivación_de_Datos_Discretos.pdf"
updated: 2026-08-21
---

# Interpolación polinómica

El mundo real casi nunca entrega una función continua: entrega **puntos de
datos discretos** — mediciones de un experimento, sensores, un muestreo. El
problema central es reconstruir un modelo continuo que permita predecir el
comportamiento del sistema entre esos puntos, o evaluar su derivada. Es el
segundo bloque conceptual del curso, entre [[busqueda-de-raices]] (resolver
$f(x)=0$) e [[integracion-numerica]].

## El problema

Dado un conjunto de $n+1$ puntos distintos $(x_0,y_0), \dots, (x_n,y_n)$, se
busca una función que pase exactamente por todos ellos. La familia de
funciones más simple y manejable para esto son los **polinomios**.

## Existencia y unicidad

El teorema fundamental de la interpolación garantiza dos cosas para $n+1$
puntos con abscisas distintas:

- **Existencia** — siempre es posible construir un polinomio de grado $\le n$
  que pase exactamente por los $n+1$ puntos.
- **Unicidad** — ese polinomio de grado $n$ es el **único** que lo logra. No
  hay ambigüedad: cualquier método de construcción (Lagrange, diferencias
  divididas de Newton, resolver el sistema de Vandermonde) llega al mismo
  polinomio, solo cambia la forma de escribirlo.

Esto es lo que distingue interpolar de un ajuste aproximado (como una
regresión): el polinomio interpolante no se "acerca" a los datos, los
**contiene** exactamente.

El [[polinomio-de-lagrange]] es la construcción explícita más usada para esta
tarea.

## Error de interpolación

El polinomio $P(x)$ coincide con la función real $f(x)$ en los nodos, pero en
cualquier otro punto queda una brecha:

$$f(x) - P(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!}\prod_{i=0}^{n}(x - x_i)$$

para algún $\xi$ desconocido dentro del intervalo de los datos. Como $\xi$ no
se conoce, no se puede calcular el error exacto, pero sí una **cota
superior**:

$$|E(x)| \le \frac{M_{n+1}}{(n+1)!}\left|\prod_{i=0}^{n}(x - x_i)\right|,
\qquad M_{n+1} = \max_{\xi \in [x_0,x_n]} |f^{(n+1)}(\xi)|$$

Procedimiento para acotar el error: (1) construir $P(x)$, (2) calcular el
producto $\prod(x-x_i)$, (3) determinar $M_{n+1}$ (el paso más difícil en la
práctica), (4) aplicar la fórmula de la cota, y (5) opcionalmente verificar
contra el error real si se conoce $f(x)$.

El error es cero exactamente en los nodos (por construcción) y crece cuanto
más lejos está $x$ de ellos.

## Interpolación vs. extrapolación

- **Interpolación** (evaluar dentro de $[x_0, x_n]$): zona de alta confianza,
  el polinomio es una aproximación razonable de la función real.
- **Extrapolación** (evaluar fuera del rango de los datos): zona de alto
  riesgo. El polinomio está optimizado para ajustar los datos conocidos, no
  para predecir fuera de ellos, y con polinomios de grado alto puede divergir
  drásticamente de la curva real.

Relacionado: [[polinomio-de-lagrange]], [[diferencias-finitas]],
[[analisis-de-error]], [[metodos-numericos]], [[simulador-de-reconstruccion-de-funciones]].
