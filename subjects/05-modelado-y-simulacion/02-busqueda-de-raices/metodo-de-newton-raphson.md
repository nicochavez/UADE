---
subject: modelado-y-simulacion
topic: Método de Newton-Raphson
sources:
  - 01A Introducción Modelado y Simulación.pdf
  - 01A Metodos de aproximación Introducción.pdf
  - 01D Lectura 1.pdf
  - Viernes TN 2026-II.pdf
  - 02A Introducción Metodos Numéricos Aitken y Newton Raphson.pdf
  - Geometric_Root_Finding (1).pdf
  - simulador_metodos_numericos-6.html
updated: 2026-08-21
---

# Método de Newton-Raphson

Método iterativo para encontrar las raíces de $f(x) = 0$. Su genialidad radica en
usar la **línea tangente** en cada paso para "apuntar" hacia la solución.

## Fórmula iterativa

$$
x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}
$$

## Interpretación geométrica

Cada iteración repite cuatro pasos:

1. **Punto inicial:** se parte de una aproximación $x_n$ sobre la curva $f(x)$.
2. **Trazar la tangente:** se traza la recta tangente a $f$ en $(x_n, f(x_n))$,
   cuya pendiente es $f'(x_n)$.
3. **Encontrar la intersección:** el punto donde esa tangente corta el eje $x$
   ($y = 0$) define geométricamente $x_{n+1}$.
4. **Repetir:** $x_{n+1}$ reemplaza a $x_n$ y se traza una nueva tangente, cada
   vez más cerca de la raíz real.

## Convergencia cuadrática

Su convergencia es **cuadrática** ($p = 2$, ver [[iteracion-y-convergencia]]):
el número de decimales correctos se duplica aproximadamente en cada iteración,
lo que lo hace muy rápido cuando está cerca de la raíz.

- **Ventaja:** convergencia extremadamente rápida si $x_0$ está suficientemente
  cerca de la raíz ("el veloz"); relativamente simple de implementar.
- **Desventaja:** necesita poder calcular la derivada $f'(x)$ (analítica o
  numérica) y una buena estimación inicial. Es propenso a **divergir
  catastróficamente** o fallar por completo si $f'(x_n) = 0$ o está cerca de
  cero en alguna iteración.

## Implementación (Python)

```python
def f(x):
    return x**3 - x - 4

# Dentro del bucle de iteración...
fx = round(f(x), precision)
dfx = round(derivative(f, x, dx=tolerancia), precision)
if dfx == 0:
    raise ValueError("La derivada es cero.")
x_new = round(x - fx / dfx, precision)
x = x_new
```

Ejemplo con $f(x) = x^3 - x - 4$, $x_0 = 1.0$, tolerancia $10^{-6}$: converge a
$x \approx 1.79632$ en 7 iteraciones (fuente: `02A Introducción Metodos Numéricos
Aitken y Newton Raphson.pdf`).

## Lugar en el curso

Se trata en profundidad en la Clase 2: planteo e interpretación geométrica,
condiciones suficientes de convergencia y su contraste con la **aceleración de
convergencia lineal** ([[metodo-de-aitken|método de Aitken]]) — mientras Aitken
acelera una sucesión ya convergente, Newton-Raphson busca directamente la raíz
usando la tangente.

Contrasta con la [[metodo-de-biseccion|bisección]] (lineal pero siempre
converge) y el [[metodo-del-punto-fijo]].

Relacionado: [[busqueda-de-raices]], [[iteracion-y-convergencia]],
[[metodo-de-aitken]].
