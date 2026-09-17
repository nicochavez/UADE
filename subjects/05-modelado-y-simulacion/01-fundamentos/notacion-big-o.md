---
subject: modelado-y-simulacion
topic: Notación Big O
sources:
  - 01D Lectura 2.pdf
updated: 2026-08-07
---

# Notación Big O

La **notación Big O** no mide el tiempo en segundos, sino **cómo responde un
algoritmo al crecimiento de los datos**. Permite comparar la eficiencia de
distintos métodos de forma abstracta y universal.

La pregunta que responde: ¿es una solución escalable o se colapsará con datos
reales?

## Jerarquía intuitiva de crecimiento

De mejor a peor comportamiento cuando crece el tamaño de entrada $n$:

- **Excelente / Muy bueno** — crecimiento sub-lineal o logarítmico.
- **Bueno** — crecimiento lineal.
- **Peligroso** — crecimiento que se dispara (exponencial/cuadrático alto).

Es uno de los "fundamentos" del análisis numérico (Nivel 1 del plan en
`01D Lectura 2.pdf`), junto con la [[iteracion-y-convergencia]] y las
[[condicion-de-lipschitz|funciones de Lipschitz]].

Relacionado: [[metodos-numericos]], [[analisis-de-error]].
