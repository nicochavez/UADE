---
subject: modelado-y-simulacion
topic: Método de Heun (Euler mejorado / modificado)
sources:
  - 06A Metodos_de_Runge_Kutta.pdf
updated: 2026-09-18
---

# Método de Heun (Euler mejorado)

Refinamiento del [[metodo-de-euler]]: en lugar de usar una sola pendiente,
**promedia dos**, la del inicio y la del final del intervalo. También se lo
llama *Euler mejorado* o *Euler modificado* ("Euler M" en la tabla de `06A`).
Es un Runge-Kutta de **segundo orden** y un esquema **predictor-corrector**.

## Predictor y corrector

**1. Predicción:** un paso de Euler estándar da un valor preliminar para el
final del intervalo:

$$
y^*_{i+1} = y_i + h\, f(x_i, y_i)
$$

**2. Corrección:** se evalúa la pendiente en el punto predicho
$(x_{i+1}, y^*_{i+1})$, se la promedia con la pendiente inicial, y con esa
pendiente promedio se avanza **desde el punto original** $y_i$:

$$
y_{i+1} = y_i + \frac{h}{2}\left[f(x_i, y_i) + f(x_{i+1}, y^*_{i+1})\right]
$$

En la forma general $y_{i+1} = y_i + \phi h$:
$\phi = \dfrac{f(x_i, y_i) + f(x_{i+1}, y^*_{i+1})}{2}$.

## Geometría

Euler sigue una única recta tangente desde el inicio del intervalo. Heun, en
cambio, usa una pendiente que representa mejor la **trayectoria promedio** de
la curva a lo largo del intervalo. Si la curva es convexa, la tangente inicial
se queda corta y la final se pasa, así que el promedio compensa ambos errores.

Hay un paralelo con la integración: Euler equivale a la regla del rectángulo
por la izquierda, y Heun a la [[regla-del-trapecio]] aplicada a
$\int_{x_i}^{x_{i+1}} f\,dx$.

## Costo y precisión

- **2 evaluaciones** de $f$ por paso (Euler usa 1).
- Dato estándar (no figura en las diapositivas): el error global es $O(h^2)$.
- Ejemplo $y' = x + y$, $y(0) = 1$, $h = 0.1$: en $x = 1$ da $3.428162$ contra
  el exacto $3.436564$, un error de $\approx 0.0084$, **30 veces menor** que
  el de Euler.

Primer paso a mano: $f(0, 1) = 1$ y $y^* = 1.1$, luego $f(0.1, 1.1) = 1.2$,
así que $y_1 = 1 + 0.05\,(1 + 1.2) = 1.11$.

## Implementación (Python, esquema propio)

```python
def heun(f, x0, y0, h, n):
    x, y = x0, y0
    for _ in range(n):
        y_pred = y + h * f(x, y)                         # predictor (Euler)
        y = y + h / 2 * (f(x, y) + f(x + h, y_pred))     # corrector
        x = x + h
    return y
```

Relacionado: [[ecuaciones-diferenciales-ordinarias]], [[metodo-de-runge-kutta-4]].
