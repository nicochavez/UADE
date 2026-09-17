---
subject: modelado-y-simulacion
topic: Iteración, convergencia y orden de convergencia
sources:
  - 01A Metodos de aproximación Introducción.pdf
  - 01B conjuntos compactos.pdf
  - 01D Lectura 2.pdf
  - Geometric_Root_Finding (1).pdf
updated: 2026-08-21
---

# Iteración y convergencia

## Iterar

**Iterar** significa repetir un proceso con el objetivo de acercarse a un
resultado deseado. Muchos métodos numéricos tienen la forma:

$$
x_{n+1} = f(x_n)
$$

partiendo de un valor inicial $x_0$.

## Convergencia

La **convergencia** indica cómo las aproximaciones sucesivas se acercan a la
solución $x^*$ de una ecuación $f(x) = 0$. Es la garantía matemática de que
nuestro esfuerzo iterativo tiene un destino y no estamos perdidos en el "caos
computacional".

El **error** en la iteración $n$ es $e_n = x_n - x^*$.

## Velocidad y orden de convergencia

- **Velocidad de convergencia:** la rapidez con la que se reduce el error.
- **Orden de convergencia $p$:** describe qué tan rápido una secuencia iterativa
  se acerca a su límite. Un $p$ más alto significa convergencia más rápida:

$$
e_{n+1} \approx C \cdot (e_n)^p
$$

- **Lineal (p = 1):** el error se reduce por un factor constante en cada paso
  (ej. [[metodo-de-biseccion]], [[metodo-del-punto-fijo]]).
- **Cuadrática (p = 2):** el número de decimales correctos se duplica
  aproximadamente en cada iteración (ej. [[metodo-de-newton-raphson]]).

Una sucesión de convergencia lineal no está condenada a ser lenta: el
[[metodo-de-aitken|proceso Δ² de Aitken]] extrapola tres términos consecutivos
para saltar mucho más cerca del límite sin cambiar el proceso iterativo.

## El desafío de la garantía

La pregunta clave no es si una iteración *puede* converger, sino si podemos
**garantizar** que lo hará (unicidad) y sin importar dónde empecemos
(estabilidad). Esa garantía la aportan los [[conjuntos-compactos]], la
[[condicion-de-lipschitz]] y el [[teorema-del-punto-fijo-de-banach]].

Relacionado: [[analisis-de-error]], [[notacion-big-o]], [[metodos-numericos]].
