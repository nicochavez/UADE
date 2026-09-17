---
subject: modelado-y-simulacion
topic: Regla de Simpson 3/8
sources:
  - 04A Newton Cotes.pdf
  - newton-cotes-simulador.html
updated: 2026-08-28
---

# Regla de Simpson 3/8

Refinamiento adicional dentro de las [[formulas-de-newton-cotes]]: usa un
polinomio de **grado 3**, definido por **cuatro puntos equidistantes**, para
aproximar la función en cada panel.

## Fórmula simple (3 segmentos, $n = 3$)

Con $h = \dfrac{b-a}{3}$ y nodos $a, x_1, x_2, b$:

$$
\int_a^b f(x)\,dx \approx \frac{3h}{8}\left[f(a) + 3f(x_1) + 3f(x_2) + f(b)\right]
$$

Error:

$$
E_t = -\frac{3h^5}{80}\, f^{(4)}(\xi)
$$

## Fórmula compuesta

Se repite el panel cúbico sobre grupos de tres subintervalos, con
$h = \dfrac{b-a}{n}$ y $m = n/3$ paneles:

$$
\int_a^b f(x)\,dx \approx \frac{3h}{8}\sum_{k=0}^{m-1}\Big[f_{3k} + 3f_{3k+1} + 3f_{3k+2} + f_{3k+3}\Big]
$$

Desarrollando la suma, el patrón de pesos es $1, 3, 3, 2, 3, 3, 2, \dots, 3, 3, 1$:
los dos nodos interiores de cada panel pesan 3, y los nodos que son frontera
entre dos paneles pesan 2.

### Restricción clave

**$n$ debe ser múltiplo de 3.** Cada panel consume tres subintervalos.

### Error de truncamiento

$$
E_t = -\frac{(b-a)\,h^4}{80}\, f^{(4)}(\xi)
\qquad\Longleftrightarrow\qquad
E_t = -\frac{(b-a)^5}{80\,n^4}\, f^{(4)}(\xi)
$$

Para el caso $n = 3$ el denominador queda en $80 \cdot 3^4 = 6480$, que es la
forma en que aparece escrito en las diapositivas de la clase.

Es $O(h^4)$: **el mismo orden que la [[regla-de-simpson-1-3]]**, pero con una
constante de error peor ($1/80$ contra $1/180$) y un punto más por panel. A
igual $h$, Simpson 1/3 es más precisa y más barata: por eso 3/8 no la
reemplaza.

### Para qué sirve entonces

Su utilidad real es **de compatibilidad**: cuando $n$ es impar, Simpson 1/3 no
se puede aplicar. La receta estándar es usar un panel de 3/8 sobre los tres
últimos (o primeros) subintervalos y 1/3 sobre el resto, que ahora sí queda
par.

## Implementación (Python, `04A Newton Cotes.pdf`)

```python
import numpy as np

# n debe ser múltiplo de 3
h = (b - a) / n
x = np.linspace(a, b, n + 1)
y = funcion(x)
S = y[0] + y[-1] + 3*np.sum(y[1:n:3]) + 3*np.sum(y[2:n:3]) + 2*np.sum(y[3:n-1:3])

integral = (3 * h / 8) * S
```

Relacionado: [[integracion-numerica]], [[regla-de-simpson-1-3]],
[[formulas-de-newton-cotes]].
