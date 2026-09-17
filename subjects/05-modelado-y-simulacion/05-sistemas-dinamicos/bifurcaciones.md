---
subject: modelado-y-simulacion
topic: Bifurcaciones y puntos de inflexión
sources:
  - 01A Introducción Modelado y Simulación.pdf
  - 01D Lectura 1.pdf
  - Viernes TN 2026-II.pdf
updated: 2026-08-07
---

# Bifurcaciones

Una **bifurcación** es un cambio suave y continuo en un parámetro $r$ que
desencadena una transformación súbita y cualitativa en el comportamiento a largo
plazo de un [[sistemas-dinamicos|sistema dinámico]]. Los equilibrios pueden
aparecer, desaparecer o cambiar su estabilidad. Permite identificar "puntos de
inflexión" (*tipping points*), umbrales críticos y cambios de régimen. Se estudia
en la Clase 9.

## Ejemplos

- **Bifurcación pitchfork:** $\dot{x} = rx - x^3$. Para $r < 0$ el origen es estable;
  al cruzar $r = 0$ (punto de bifurcación) aparecen dos nuevos equilibrios
  estables $x = \pm\sqrt{r}$ y el origen se vuelve inestable.
- **Bifurcación saddle-node:** $\dot{x} = r + x^2$, con equilibrios $x = \pm\sqrt{-r}$.

## Análisis en 1D

Para sistemas de una variable ($dx/dt = f(x)$) se analiza la estabilidad y cómo
cambia la estructura de equilibrios al variar $r$:

- **Diagrama de fase (línea de fase):** ej. $dx/dt = 4x - x^2$ tiene equilibrios
  $x = 0$ (inestable) y $x = 4$ (estable).
- **Diagrama de bifurcación:** grafica los equilibrios $x$ en función del
  parámetro $r$.

Relacionado: [[sistemas-dinamicos]], [[modelos-aplicados]].
