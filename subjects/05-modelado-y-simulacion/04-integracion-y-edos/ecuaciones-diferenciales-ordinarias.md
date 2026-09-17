---
subject: modelado-y-simulacion
topic: Ecuaciones diferenciales ordinarias (EDOs)
sources:
  - 01A Introducción Modelado y Simulación.pdf
  - 01D Lectura 1.pdf
  - Viernes TN 2026-II.pdf
updated: 2026-08-07
---

# Ecuaciones diferenciales ordinarias (EDOs)

Métodos para resolver $\dfrac{dy}{dt} = f(t, y)$: predecir el estado futuro de un sistema
a partir de su estado actual y sus reglas de cambio. Es el **corazón del modelado
dinámico** — permite simular desde la órbita de un planeta hasta la propagación
de una epidemia. Es también el motor interno de la simulación (Clase 6). El
problema de valor inicial se conoce como **problema de Cauchy**.

## Un paso en el tiempo

- **Método de Euler (el paso simple):** da un paso usando la pendiente inicial;
  asume pendiente constante. Intuitivo pero propenso a errores.
- **Runge-Kutta 4 (RK4, el paso inteligente):** estándar de la industria. En cada
  paso combina cuatro estimaciones ponderadas de la pendiente ($k_1 \dots k_4$) para
  lograr precisión extraordinaria:

  $$
  y_{n+1} = y_n + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4)
  $$

También se estudian Euler modificado y Taylor, los órdenes de aproximación local
y global, y esquemas en diferencias para ecuaciones en derivadas parciales con
valores en la frontera.

## Conexión con dinámica

Resolver EDOs numéricamente permite **simular** la evolución; el análisis
cualitativo de esas soluciones es el objeto de los [[sistemas-dinamicos]].

Relacionado: [[integracion-numerica]], [[modelos-aplicados]], [[metodos-numericos]].
