---
subject: modelado-y-simulacion
topic: Método de Aitken (aceleración Δ²)
sources:
  - 02A Introducción Metodos Numéricos Aitken y Newton Raphson.pdf
  - Geometric_Root_Finding (1).pdf
  - simulador_metodos_numericos-6.html
updated: 2026-08-21
---

# Método de Aitken (proceso Δ²)

No es un método de búsqueda de raíces en sí mismo, sino una técnica de
**aceleración de convergencia**: toma una sucesión que ya converge (típicamente
de forma lenta, como el [[metodo-del-punto-fijo]]) y calcula un nuevo término
que está mucho más cerca del límite real, sin más iteraciones del proceso
original.

## Mecanismo

A partir de tres términos consecutivos de la sucesión original $x_n, x_{n+1},
x_{n+2}$, extrapola un valor acelerado $x_n^*$:

$$
x_n^* = x_n - \frac{(x_{n+1} - x_n)^2}{x_{n+2} - 2x_{n+1} + x_n}
$$

- **Numerador $(x_{n+1} - x_n)^2$:** el cuadrado del "paso" que está dando la
  sucesión.
- **Denominador $x_{n+2} - 2x_{n+1} + x_n$:** la segunda diferencia; mide la
  curvatura o el cambio en la velocidad de la sucesión. Cuanto más pequeño, más
  lineal (y más lenta) es la convergencia original.

## Condiciones para que funcione

- La sucesión original debe ser **convergente** (idealmente monótona); no
  sirve si diverge u oscila caóticamente.
- Requiere al menos **tres términos consecutivos** para iniciar la primera
  extrapolación.
- El denominador debe ser **distinto de cero** (si no, no se puede aplicar esa
  extrapolación).
- Ofrece la mayor ventaja cuando la sucesión original converge **lentamente**
  (p. ej. [[metodo-del-punto-fijo|punto fijo]] con $p = 1$); si ya converge
  rápido, la mejora es marginal.
- Asume estabilidad numérica: errores de cálculo grandes en la sucesión
  original producen resultados acelerados no confiables.

## Implementación (Python)

```python
def g(x):
    return (2 * x - 1) ** (1 / 2)

x1 = g(x)
x2 = g(x1)
denominador = x2 - 2 * x1 + x
if denominador != 0:
    x_acelerado = x - (x1 - x) ** 2 / denominador
else:
    x_acelerado = x2
x = x_acelerado
```

## Aitken vs. Newton-Raphson

Ambos aceleran la búsqueda de una solución, pero resuelven problemas distintos:

| | Aitken | [[metodo-de-newton-raphson|Newton-Raphson]] |
|---|---|---|
| Objetivo | Acelerar una sucesión ya convergente | Encontrar la raíz de $f(x) = 0$ |
| Se aplica a | Sucesiones numéricas de un proceso iterativo (ej. punto fijo) | Funciones diferenciables |
| Mecanismo | Extrapolación con tres términos consecutivos | Aproximación lineal con la tangente |
| Ideal para | Convergencia garantizada pero lenta, sin conocer $f(x) = 0$ | Alta precisión, cuando se puede calcular $f'(x)$ |
| Riesgo | Ineficaz si la sucesión oscila caóticamente | Falla catastróficamente si $f'(x_n) = 0$ |

Relacionado: [[iteracion-y-convergencia]], [[metodo-del-punto-fijo]],
[[busqueda-de-raices]].
