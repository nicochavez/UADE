---
subject: modelado-y-simulacion
topic: Diferencias finitas (derivación numérica)
sources:
  - "03A Modelado_con_Lagrange_y_Diferencias_Finitas.pdf"
  - "03B Interpolación_y_Derivación_de_Datos_Discretos.pdf"
---

# Diferencias finitas

Una vez resuelto cómo interpolar valores entre datos discretos
([[polinomio-de-lagrange]]), queda una pregunta distinta: en ingeniería y
ciencia a menudo no importa solo el valor de la función sino su **tasa de
cambio** (la derivada). Las diferencias finitas (o diferencias divididas)
aproximan derivadas usando únicamente los valores de la función en puntos
cercanos, sin conocer la función subyacente.

La idea parte de que la derivada es el límite de la pendiente de una
secante: si se tienen puntos suficientemente cercanos, la pendiente de la
recta que los une aproxima la pendiente de la tangente.

## Los tres enfoques

Con paso constante $h$ entre puntos, hay tres formas de elegir qué puntos
vecinos usar para estimar $f'(x_i)$:

| Enfoque | Usa | Primera derivada | Segunda derivada | Uso ideal |
|---|---|---|---|---|
| **Progresivas** (adelante) | $x_i$ y $x_{i+1}$ | $f'(x_i) \approx \dfrac{f(x_{i+1})-f(x_i)}{h}$ | $f''(x_i) \approx \dfrac{f(x_{i+2})-2f(x_{i+1})+f(x_i)}{h^2}$ | Punto inicial de un conjunto de datos |
| **Regresivas** (atrás) | $x_i$ y $x_{i-1}$ | $f'(x_i) \approx \dfrac{f(x_i)-f(x_{i-1})}{h}$ | $f''(x_i) \approx \dfrac{f(x_i)-2f(x_{i-1})+f(x_{i-2})}{h^2}$ | Punto final de un conjunto de datos |
| **Centrales** | $x_{i-1}$ y $x_{i+1}$ | $f'(x_i) \approx \dfrac{f(x_{i+1})-f(x_{i-1})}{2h}$ | $f''(x_i) \approx \dfrac{f(x_{i+1})-2f(x_i)+f(x_{i-1})}{h^2}$ | Puntos intermedios; suelen ser las más precisas |

Las centrales promedian el cambio a ambos lados de $x_i$ y, en general, dan
la mejor aproximación al valor real de la derivada.

## Implementación (Python, diferencias centradas)

```python
def f(x):
    return x**3 - 2*x + 1

x, h = 2, 0.1

def primera_derivada(f, x, h):
    return (f(x + h) - f(x - h)) / (2 * h)

def segunda_derivada(f, x, h):
    return (f(x + h) - 2*f(x) + f(x - h)) / (h**2)
```

Con $f(x)=x^3-2x+1$, $x=2$, $h=0.1$: la primera derivada aproximada da
`10.01` (real: $f'(2)=10$) y la segunda da `12.00000000000002` (real:
$f''(2)=12$). Un `h` más pequeño generalmente mejora la precisión, hasta los
límites de precisión numérica de la máquina.

## Fundamento: conexión con la serie de Taylor

Las fórmulas de diferencias finitas no son arbitrarias: se derivan de
truncar la serie de Taylor de $f$ alrededor de $x_i$.

- Orden cero: $f(x_{i+1}) \approx f(x_i)$ (aproximación constante).
- Primer orden: $f(x_{i+1}) \approx f(x_i) + f'(x_i)h$ — reordenando esta
  igualdad se obtiene la diferencia progresiva para $f'(x_i)$.
- Segundo orden: $f(x_{i+1}) \approx f(x_i) + f'(x_i)h + \frac{f''(x_i)}{2!}h^2$.

El **error de truncamiento** de cada fórmula de diferencias finitas proviene
justamente de los términos de la serie de Taylor que se ignoran al truncar.
Esto conecta con la [[analisis-de-error|cota de error]] de la interpolación:
funciones más simples (derivadas de orden superior más chicas) producen
menos error.

Relacionado: [[interpolacion-polinomica]], [[polinomio-de-lagrange]],
[[analisis-de-error]].
