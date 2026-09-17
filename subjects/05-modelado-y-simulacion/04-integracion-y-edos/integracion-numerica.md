---
subject: modelado-y-simulacion
topic: Integración numérica
sources:
  - 01A Introducción Modelado y Simulación.pdf
  - 01D Lectura 1.pdf
  - 04A Newton Cotes.pdf
  - newton-cotes-simulador.html
  - Viernes TN 2026-II.pdf
updated: 2026-08-28
---

# Integración numérica

Aproximar el valor de una integral definida $\int f(x)\,dx$ cuando la solución
analítica es imposible o los datos son discretos. Es "el efecto acumulado de una
acción" y el núcleo de los solucionadores de [[ecuaciones-diferenciales-ordinarias]].
Se ve en las Clases 4 y 5 del curso.

## Enfoques deterministas (Newton-Cotes)

Aproximan la función con formas geométricas simples y suman sus áreas sobre una
rejilla de puntos equidistantes. Es el contenido de la Clase 4, desarrollado en
[[formulas-de-newton-cotes]]:

- [[regla-del-rectangulo]] — polinomio de grado 0, altura en el punto medio.
- [[regla-del-trapecio]] — polinomio de grado 1; sin restricciones sobre $n$.
- [[regla-de-simpson-1-3]] — parábolas; $O(h^4)$ con $n$ par. La opción por
  defecto para funciones suaves.
- [[regla-de-simpson-3-8]] — cúbicas; $n$ múltiplo de 3, útil para completar
  mallas impares.

Una familia distinta, que además optimiza la **posición** de los nodos, es la
[[cuadratura-de-gauss-legendre]].

Temas asociados: estimación de las incertidumbres, orden de aproximación y
discretizaciones óptimas (ver [[analisis-de-error]] y [[notacion-big-o]]).

## Enfoque probabilístico: Monte Carlo

Estima el área mediante **muestreo aleatorio**: se generan miles de puntos
aleatorios en una región conocida y se cuenta la proporción que cae bajo la
curva. Su poder reside en problemas complejos y de **alta dimensión**.

Ejemplo clásico: estimar $\pi$ lanzando puntos aleatorios en un cuadrado que
circunscribe un cuarto de círculo ($\pi \approx 4 \cdot \text{puntos\_dentro} / \text{total}$). Temas
asociados (Clase 5): estimadores puntuales, intervalos de confianza, estimación
de varianza y tamaño de la generación pseudoaleatoria.

## Herramienta

- [[simulador-de-newton-cotes]] — simulador de cátedra con los ocho métodos,
  tabla iterativa, comparación de errores y aplicaciones reales.

Relacionado: [[metodos-numericos]], [[ecuaciones-diferenciales-ordinarias]],
[[interpolacion-polinomica]].
