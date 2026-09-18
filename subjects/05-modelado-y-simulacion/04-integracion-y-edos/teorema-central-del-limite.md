---
subject: modelado-y-simulacion
topic: Distribución normal y Teorema Central del Límite
sources:
  - 05C Lectura 1 Erraor_acotado_vs_confianza_probabilística.pdf
updated: 2026-09-18
---

# Teorema Central del Límite (TCL)

El vínculo entre un muestreo aleatorio y una predicción cuantificable. Es la
base estadística para interpretar los resultados del [[metodo-de-monte-carlo]].

## Prerrequisito: la distribución normal

Una población normal $N(\mu_x, \sigma_x)$ queda descripta por su media
$\mu_x$ y su desviación estándar $\sigma_x$. Su densidad de probabilidad es

$$
\delta(x) = \frac{1}{\sigma_x\sqrt{2\pi}}\, e^{-\frac{(x-\mu_x)^2}{2\sigma_x^2}}
$$

**Percentil:** la probabilidad de que $x$ sea menor o igual a un valor es el
área bajo la curva hasta ese punto. El valor $z_u$ es el que cumple

$$
P\{x \le \mu_x + z_u\,\sigma_x\} = u
$$

## El teorema

Si se toma una muestra suficientemente grande de tamaño $n$ de **cualquier**
distribución (aunque no sea normal), la media muestral

$$
\bar{x} = \frac{1}{n}\sum_{k=1}^{n} x_k
$$

es **asintóticamente normal**:

$$
\bar{x} \sim N\!\left(\mu_x,\ \frac{\sigma_x}{\sqrt{n}}\right)
$$

Los parámetros de la media muestral son:

- **Media de las medias:** $\mu_{\bar{x}} = \mu_x$, así que el estimador está
  centrado en el valor verdadero.
- **Desviación de las medias (error estándar):**
  $\sigma_{\bar{x}} = \dfrac{\sigma_x}{\sqrt{n}}$

## Consecuencia práctica

La estimación se vuelve más predecible y menos variable a medida que crece
$n$. En `05C` se ilustra con una población exponencial: con $n = 5$ la
distribución de $\bar{x}$ ya es acampanada, y con $n = 30$ se vuelve mucho más
angosta.

Como el ancho escala con $1/\sqrt{n}$, **reducir el error a la mitad requiere
cuadruplicar $n$**.

Con el TCL se construye el [[intervalo-de-confianza]]. Complementa a la
[[ley-de-los-grandes-numeros]], que solo asegura la convergencia; el TCL
además da su velocidad y su forma.

Relacionado: [[integracion-por-monte-carlo]],
[[error-acotado-vs-confianza-probabilistica]].
