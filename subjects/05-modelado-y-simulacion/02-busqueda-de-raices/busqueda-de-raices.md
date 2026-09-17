---
subject: modelado-y-simulacion
topic: Búsqueda de raíces (panorama y comparación)
sources:
  - 01A Metodos de aproximación Introducción.pdf
  - 01C Búsqueda_Binaria_de_Raíces.pdf
  - 01D Lectura 1.pdf
  - Geometric_Root_Finding (1).pdf
  - 02A Introducción Metodos Numéricos Aitken y Newton Raphson.pdf
updated: 2026-08-21
---

# Búsqueda de raíces

Son técnicas para resolver $f(x) = 0$ cuando no es posible despejar $x$
algebraicamente. Son la base para encontrar equilibrios, óptimos y soluciones de
estado estacionario (Bloque 1 del curso).

Una **raíz** es un punto $c$ donde $f(c) = 0$. Para $x^2 - 4 = 0$ la solución es
trivial, pero para funciones como $\cos(x) - x = 0$ el álgebra no alcanza y hace
falta un método robusto.

## Los tres caminos hacia la solución

| Método | Orden de convergencia | Ventaja | Desventaja |
|--------|-----------------------|---------|------------|
| [[metodo-de-newton-raphson]] | Cuadrática | Muy rápido cerca de la raíz | Necesita derivadas |
| [[metodo-de-biseccion]] | Lineal | Siempre converge | Lento |
| [[metodo-del-punto-fijo]] | Lineal | Fácil de implementar | Requiere $\lvert g'(x_0) \rvert < 1$ |

Dos estrategias contrastan: **bisección** (el confiable) garantiza la raíz si
$f(a) \cdot f(b) < 0$ pero es lento; **Newton-Raphson** (el veloz) usa la tangente para
converger rápido pero requiere buena estimación inicial.

A estos tres se suma el [[metodo-de-aitken]], que no busca raíces sino que
**acelera** una sucesión que ya converge lentamente (típicamente la del punto
fijo).

## Matriz de decisión algorítmica

Cada método se distingue por su base geométrica y por el modo en que puede
fallar (fuente: `Geometric_Root_Finding (1).pdf`):

| Método | Orden | Base geométrica | Riesgo principal |
|--------|-------|-----------------|------------------|
| [[metodo-de-biseccion|Bisección]] | Lineal | División de intervalos | Lento; ineficiente para alta precisión |
| [[metodo-del-punto-fijo|Punto fijo]] | Lineal | Intersección de $y = x$ con $y = g(x)$ | Diverge si $\lvert g'(x) \rvert \ge 1$ |
| [[metodo-de-newton-raphson|Newton-Raphson]] | Cuadrática | Intersección de la tangente con el eje x | Falla catastróficamente si $f'(x_n) = 0$ |
| [[metodo-de-aitken|Aitken]] | Acelerada | Extrapolación de la sucesión | Ineficaz si la sucesión oscila caóticamente |

Elegir el método correcto exige equilibrar la **robustez matemática** (las
garantías de [[conjuntos-compactos]] y [[condicion-de-lipschitz]]) con la
**eficiencia computacional** (convergencia cuadrática).

Todos usan la [[iteracion-y-convergencia|iteración]] $x_{n+1} = f(x_n)$ y se
apoyan en [[analisis-de-error|criterios de detención]]. Los cuatro se pueden
explorar interactivamente en el [[simulador-de-raices]].

Relacionado: [[teorema-de-bolzano]], [[metodos-numericos]].
