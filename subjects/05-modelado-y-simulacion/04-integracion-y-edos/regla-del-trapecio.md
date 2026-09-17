---
subject: modelado-y-simulacion
topic: Regla del trapecio
sources:
  - 04A Newton Cotes.pdf
  - newton-cotes-simulador.html
updated: 2026-08-28
---

# Regla del trapecio

Primera aproximación no trivial de las [[formulas-de-newton-cotes]]: se
conectan dos puntos de la función con una **línea recta**, formando un
trapecio. Es un polinomio de interpolación de **grado 1** y usa **dos puntos
por panel**.

## Fórmula simple (1 segmento)

$$
\int_a^b f(x)\,dx \approx \frac{b-a}{2}\left[f(a) + f(b)\right]
$$

Lectura geométrica: el área es el **promedio de las alturas por el ancho del
intervalo**.

Error de la versión simple:

$$
E_t = -\frac{(b-a)^3}{12}\, f''(\xi)
$$

## Fórmula compuesta

Un solo trapecio grande genera un error considerable. Se divide $[a,b]$ en $n$
subintervalos de ancho $h = \dfrac{b-a}{n}$ y se suman $n$ trapecios pequeños:

$$
\int_a^b f(x)\,dx \approx \frac{h}{2}\left[f(a) + 2\sum_{i=1}^{n-1} f(a + ih) + f(b)\right]
$$

El patrón de pesos es $1, 2, 2, \dots, 2, 1$: los nodos interiores cuentan
doble porque son compartidos por dos trapecios contiguos.

### Error de truncamiento

$$
E_t = -\frac{(b-a)^3}{12n^2}\, f''(\xi)
\qquad\text{equivalentemente}\qquad
E_t = -\frac{(b-a)\,h^2}{12}\, f''(\xi)
$$

El error **disminuye cuadráticamente** con el número de subintervalos: duplicar
$n$ divide el error por $\approx 4$ ($O(h^2)$, ver [[notacion-big-o]]).

Como el error depende de $f''$, la regla es **exacta para rectas** ($f'' = 0$).
El signo negativo indica que subestima la integral cuando $f$ es convexa
($f'' > 0$).

## Cuándo usarla

- No impone **ninguna restricción sobre $n$** (cualquier $n \ge 1$).
- Es la más barata de implementar y de menor costo computacional por nodo, lo
  que la hace la opción típica en firmware y sistemas embebidos.
- Es la que usan las librerías de ML para calcular el **AUC-ROC** a partir de
  los puntos discretos de la curva ROC (`newton-cotes-simulador.html`).

## Implementación (Python, `04A Newton Cotes.pdf`)

```python
import numpy as np

h = (b - a) / n
x = np.linspace(a, b, n + 1)
y = funcion(x)

integral = (h / 2) * (y[0] + 2 * np.sum(y[1:n]) + y[-1])
```

Relacionado: [[integracion-numerica]], [[regla-de-simpson-1-3]],
[[regla-del-rectangulo]], [[formulas-de-newton-cotes]].
