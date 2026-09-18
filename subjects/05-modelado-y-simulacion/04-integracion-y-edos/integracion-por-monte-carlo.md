---
subject: modelado-y-simulacion
topic: Integración por Monte Carlo
sources:
  - 05A Introducción al metodo de Monte Carlo.pdf
  - 05B Repaso Monte_Carlo.pdf
  - 05C Lectura 1 Erraor_acotado_vs_confianza_probabilística.pdf
updated: 2026-09-18
---

# Integración por Monte Carlo

Aplicación del [[metodo-de-monte-carlo]] al cálculo de integrales definidas
$I = \int_a^b f(x)\,dx$, sobre todo cuando no hay primitiva o la dimensión es
alta. Hay dos variantes en el material.

## Variante 1: valor medio (estimador de la media)

**Idea:** reescribir la integral como un **valor esperado**. Si
$X \sim U[a,b]$, entonces $E[f(X)] = \frac{1}{b-a}\int_a^b f(x)\,dx$, por lo tanto

$$
I = (b-a) \cdot E[f(X)] = \text{Volumen} \cdot E[f(X)]
$$

donde el "volumen" del dominio en 1D es la longitud $(b-a)$. La
[[ley-de-los-grandes-numeros]] permite estimar $E[f(X)]$ promediando $f$ en
puntos aleatorios.

**Estimador 1D:** con $x_1, \dots, x_n$ uniformes en $[a,b]$,

$$
\hat{I} = (b-a) \cdot \frac{1}{n}\sum_{i=1}^{n} f(x_i)
$$

$(b-a)$ es el volumen del dominio y la suma es el valor promedio de $f$ en
las muestras.

**Extensión 2D:** para $\iint f(x,y)\,dy\,dx$ sobre $[a,b]\times[c,d]$, con
$(x_i, y_i)$ uniformes en el rectángulo:

$$
\hat{I} = (b-a)(d-c) \cdot \frac{1}{n}\sum_{i=1}^{n} f(x_i, y_i)
$$

El volumen pasa a ser el área del rectángulo contenedor. En $d$ dimensiones
la fórmula es la misma, con el volumen del hiperrectángulo.

## Variante 2: aciertos ("dardos", hit-or-miss)

Presentada en `05C` con $f(x) = x e^{-x}$ en $[0,4]$:

1. **Dibujar la caja:** encerrar la curva en un rectángulo de área
   $A_{\text{rect}}$. En el ejemplo, $[0,4]\times[0,0.6]$, válido porque
   $\max f = f(1) = 1/e \approx 0.368 < 0.6$.
2. **Lanzar dardos:** generar $N$ puntos $(x, y)$ uniformes en el rectángulo.
3. **Contar aciertos:** $k$ = cantidad de puntos con $y \le f(x)$.

$$
\text{Área} \approx A_{\text{rect}} \cdot \frac{k}{N}
$$

Así un problema de cálculo se convierte en un **experimento estadístico**. La
[[estimacion-de-pi-por-monte-carlo]] es exactamente esta variante.

## Comparación (resumen de `05A`)

| Característica | Valor medio (1D) | Aciertos (área bajo curva, 2D) |
|----------------|------------------|--------------------------------|
| Muestreo | puntos $x_i$ en 1D | puntos $(x_i, y_i)$ en 2D |
| Dominio | intervalo $[a,b]$ | rectángulo contenedor |
| Cálculo | promedio de $f(x_i)$ | proporción de puntos bajo $f(x)$ |
| Volumen | longitud $(b-a)$ | área del rectángulo |

## Precisión: intervalo de confianza

Cada ejecución da un resultado ligeramente distinto, así que se reporta un
rango en vez de un número. Con $\sigma$ la desviación estándar muestral de los
$f(x_i)$:

$$
IC = \hat{I} \pm z_{\alpha/2}\,\frac{\sigma}{\sqrt{n}}
$$

La deducción, la tabla de valores $z$ y una observación sobre el factor
$(b-a)$ están en [[intervalo-de-confianza]]. Para reducir el ancho del
intervalo, lo más directo es aumentar $n$.

## Fortaleza: alta dimensión

Los métodos de malla ([[formulas-de-newton-cotes]]) sufren la **maldición de
la dimensionalidad**: con $m$ puntos por eje, $d$ dimensiones requieren $m^d$
evaluaciones, un costo que crece exponencialmente. En Monte Carlo el error
escala como $1/\sqrt{n}$ **independientemente de la dimensión**, así que su
costo crece de forma mucho más manejable (`05B`).

## Implementación (Python, esquema propio basado en las fórmulas)

```python
import random, math

def monte_carlo_integral(f, a, b, n=100_000, z=1.96, seed=None):
    rng = random.Random(seed)
    muestras = [f(rng.uniform(a, b)) for _ in range(n)]
    media = sum(muestras) / n
    sigma = math.sqrt(sum((m - media)**2 for m in muestras) / (n - 1))
    I_hat = (b - a) * media
    margen = z * (b - a) * sigma / math.sqrt(n)   # EE del estimador de I
    return I_hat, (I_hat - margen, I_hat + margen)

I, ic = monte_carlo_integral(lambda x: x * math.exp(-x), 0, 4, seed=42)
# valor exacto: 1 - 5e^{-4} ≈ 0.908422
```

Relacionado: [[integracion-numerica]], [[generacion-de-numeros-aleatorios]],
[[error-acotado-vs-confianza-probabilistica]].
