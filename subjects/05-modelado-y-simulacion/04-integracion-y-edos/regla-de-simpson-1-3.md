---
subject: modelado-y-simulacion
topic: Regla de Simpson 1/3
sources:
  - 04A Newton Cotes.pdf
  - newton-cotes-simulador.html
updated: 2026-08-28
---

# Regla de Simpson 1/3

¿Qué se ajusta mejor a una curva que una recta? Otra curva. La regla de Simpson
1/3 usa **tres puntos para definir una parábola** (polinomio de grado 2) que
interpola la función. Es la regla de referencia de las
[[formulas-de-newton-cotes]]: la mejor relación precisión/costo para funciones
suaves.

## Fórmula simple (2 segmentos, $n = 2$)

Con $h = \dfrac{b-a}{2}$:

$$
\int_a^b f(x)\,dx \approx \frac{h}{3}\left[f(a) + 4f\!\left(\frac{a+b}{2}\right) + f(b)\right]
$$

Error:

$$
E = -\frac{h^5}{90}\, f^{(4)}(\xi)
\qquad\text{equivalentemente}\qquad
E = -\frac{(b-a)^5}{2880}\, f^{(4)}(\xi)
$$

(las dos formas coinciden al sustituir $h=(b-a)/2$; la primera aparece en las
diapositivas y la segunda en el [[simulador-de-newton-cotes]]).

## Fórmula compuesta (a revisar)

Se aplica la aproximación parabólica de forma iterativa sobre **pares de
subintervalos** consecutivos, con $h = \dfrac{b-a}{n}$:

$$
\int_a^b f(x)\,dx \approx \frac{h}{3}\Big[f_0 + 4\!\!\sum_{i\ \text{impares}}\!\! f_i \;+\; 2\!\!\sum_{i\ \text{pares}}\!\! f_i \;+\; f_n\Big]
$$

El patrón de pesos es $1, 4, 2, 4, 2, \dots, 4, 1$: los nodos **impares** (centros
de cada parábola) pesan 4, los **pares** interiores (compartidos entre dos
paneles) pesan 2.

### Restricción clave

**$n$ debe ser par.** Cada panel consume dos subintervalos, así que el
intervalo tiene que poder repartirse en pares completos.

### Error de truncamiento

$$
E_{\text{comp}} = -\frac{(b-a)^5}{180\,n^4}\, f^{(4)}(\xi)
\qquad\text{equivalentemente}\qquad
E_{\text{comp}} = -\frac{(b-a)\,h^4}{180}\, f^{(4)}(\xi)
$$

Es $O(h^4)$: duplicar $n$ divide el error por $\approx 16$, frente al factor 4
de la [[regla-del-trapecio]].

Como el error depende de $f^{(4)}$, la regla es **exacta para polinomios hasta
grado 3** — un grado más de lo que sugiere su construcción cuadrática. Ese
"grado extra gratis" es la razón por la que Simpson 1/3 domina en la práctica
sobre la [[regla-de-simpson-3-8]], que también es $O(h^4)$ pero necesita un
punto más por panel.

## Implementación (Python, `04A Newton Cotes.pdf`)

```python
import numpy as np

# n debe ser par
h = (b - a) / n
x = np.linspace(a, b, n + 1)
y = funcion(x)
S = y[0] + y[-1] + 4 * np.sum(y[1:n:2]) + 2 * np.sum(y[2:n-1:2])

integral = (h / 3) * S
```

Relacionado: [[integracion-numerica]], [[regla-del-trapecio]],
[[regla-de-simpson-3-8]], [[formulas-de-newton-cotes]].
