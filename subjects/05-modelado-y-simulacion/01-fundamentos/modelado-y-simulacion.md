---
subject: modelado-y-simulacion
topic: Modelo matemático vs. simulación
sources:
  - 01A Introducción Modelado y Simulación.pdf
  - 01A Metodos de aproximación Introducción.pdf
  - 01D Lectura 2.pdf
updated: 2026-08-07
---

# Modelado y simulación

Los dos pilares de la materia son inseparables: usamos el lenguaje de los
**modelos** para escribir *cómo* cambian los fenómenos, y el motor de los
**métodos numéricos** para *dar vida* a esa historia mediante simulaciones.

## Modelo matemático

Un **modelo matemático** es una simplificación de la realidad que captura su
esencia y la expresa en términos matemáticos. Se representa como una relación
funcional:

$$
\text{Variable dependiente} = f(\text{Variables independientes}, \text{Parámetros}, \text{Funciones de fuerza})
$$

Ejemplo clásico: el péndulo se abstrae en la EDO $\dfrac{d^2\theta}{dt^2} + \dfrac{g}{L}\sin(\theta) = 0$.

## Simulación

La **simulación** es el proceso de *ejecutar* el modelo para estudiar el
comportamiento del sistema a través del tiempo o bajo distintas condiciones.

## El desafío: por qué aproximar

Muchas ecuaciones fundamentales de la ciencia, la ingeniería y las finanzas **no
tienen solución analítica simple**: sabemos que la solución existe pero no
podemos "despejar la x". El ejemplo típico es $\cos(x) = x$, imposible de
resolver algebraicamente.

- **Mundo analítico:** soluciones exactas y elegantes (ej. $y = mx + b$).
- **Mundo real:** sistemas físicos, biológicos y económicos demasiado complejos.
- **Puente:** los [[metodos-numericos]] construyen soluciones *aproximadas* con
  gran poder predictivo (ver `01D Lectura 2.pdf`).

## Idea central

> La estructura del espacio determina el destino del proceso.

Modelar → simular → comprender. La aproximación permite resolver problemas
intratables analíticamente; la simulación es el laboratorio para experimentar; y
el análisis cualitativo ([[sistemas-dinamicos]], estabilidad, [[bifurcaciones]])
convierte los números en sabiduría.

Relacionado: [[metodos-numericos]], [[iteracion-y-convergencia]], [[programa-del-curso]].
