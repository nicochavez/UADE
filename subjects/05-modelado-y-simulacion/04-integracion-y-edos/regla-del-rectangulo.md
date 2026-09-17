---
subject: modelado-y-simulacion
topic: Regla del rectángulo (punto medio)
sources:
  - 04A Newton Cotes.pdf
updated: 2026-08-28
---

# Regla del rectángulo (punto medio)

La aproximación más fundamental de las [[formulas-de-newton-cotes]]: el área
bajo la curva se estima sumando áreas de **rectángulos**. La altura de cada
rectángulo se define por el valor de la función en el **punto medio** de su
base, no en un extremo.

Es una fórmula de grado 0 (el polinomio interpolante es una constante) y usa
**un solo punto por panel**.

## Fórmula compuesta

Con $h = \dfrac{b-a}{n}$:

$$
\int_a^b f(x)\,dx \approx h \sum_{i=0}^{n-1} f\!\left(a + \left(i + \tfrac{1}{2}\right)h\right)
$$

## Precisión

Error compuesto $O(h^2)$, **el mismo orden que la [[regla-del-trapecio]]** pese
a usar un polinomio de grado menor y la mitad de evaluaciones. El motivo es la
elección del punto medio: los errores por exceso y por defecto de cada
rectángulo se compensan parcialmente dentro del panel.

No tiene ninguna restricción sobre $n$: cualquier $n \ge 1$ sirve.

## Implementación (Python, `04A Newton Cotes.pdf`)

```python
import numpy as np

h = (b - a) / n
x_medio = np.linspace(a + h/2, b - h/2, n)
integral = h * np.sum(funcion(x_medio))
```

Nótese que solo evalúa la función en los puntos medios: nunca necesita $f(a)$
ni $f(b)$. Eso la vuelve útil cuando la función es singular en algún extremo
del intervalo.

Relacionado: [[integracion-numerica]], [[regla-del-trapecio]],
[[formulas-de-newton-cotes]].
