---
subject: modelado-y-simulacion
topic: Integración numérica
sources:
  - 01A Introducción Modelado y Simulación.pdf
  - 01D Lectura 1.pdf
  - 04A Newton Cotes.pdf
  - newton-cotes-simulador.html
  - Viernes TN 2026-II.pdf
  - 05A Introducción al metodo de Monte Carlo.pdf
  - 05B Repaso Monte_Carlo.pdf
  - 05C Lectura 1 Erraor_acotado_vs_confianza_probabilística.pdf
updated: 2026-09-18
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
discretizaciones óptimas (ver [[analisis-de-error]], [[notacion-big-o]] y
[[error-de-truncamiento-y-redondeo]]).

## Enfoque probabilístico: Monte Carlo (Clase 5)

Estima el área mediante **muestreo aleatorio** en lugar de una malla. Su
fortaleza está en los problemas complejos y de **alta dimensión**, donde el
error escala como $1/\sqrt{n}$ sin importar la dimensión. Desarrollado en:

- [[metodo-de-monte-carlo]] — qué es y la receta de 4 pasos.
- [[estimacion-de-pi-por-monte-carlo]] — el ejemplo clásico,
  $\pi \approx 4 \cdot \text{dentro}/\text{total}$.
- [[integracion-por-monte-carlo]] — estimador de valor medio
  $\hat{I} = (b-a)\frac{1}{n}\sum f(x_i)$ y método de aciertos.
- [[ley-de-los-grandes-numeros]] y [[teorema-central-del-limite]] — por qué
  converge y a qué ritmo.
- [[intervalo-de-confianza]] — $\hat{I} \pm z_{\alpha/2}\,\sigma/\sqrt{n}$.
- [[generacion-de-numeros-aleatorios]] — `random.uniform` y semilla.

Comparación entre ambos enfoques: [[error-acotado-vs-confianza-probabilistica]]
(y el límite práctico de los deterministas en
[[error-de-truncamiento-y-redondeo]]).

## Herramienta

- [[simulador-de-newton-cotes]] — simulador de cátedra con los ocho métodos,
  tabla iterativa, comparación de errores y aplicaciones reales.

Relacionado: [[metodos-numericos]], [[ecuaciones-diferenciales-ordinarias]],
[[interpolacion-polinomica]].
