---
subject: modelado-y-simulacion
topic: Intervalo de confianza para estimaciones Monte Carlo
sources:
  - 05A Introducción al metodo de Monte Carlo.pdf
  - 05B Repaso Monte_Carlo.pdf
  - 05C Lectura 1 Erraor_acotado_vs_confianza_probabilística.pdf
updated: 2026-09-18
---

# Intervalo de confianza (IC)

Como el [[metodo-de-monte-carlo]] es estocástico, cada ejecución produce un
resultado ligeramente distinto. En lugar de un único número se reporta un
**rango** que, con cierto nivel de confianza, contiene el valor verdadero.
Responde a la pregunta "¿cómo podemos confiar en un resultado aleatorio?".

## El lenguaje de la confianza

- **Nivel de confianza** $\gamma = 1 - \alpha$: probabilidad de que el
  intervalo **contenga** el verdadero parámetro $\mu_x$.
- **Nivel de significancia** $\alpha$: probabilidad de que **no** lo contenga.
  Se reparte en dos colas de $\alpha/2$ cada una.
- **Valor crítico** $z_u$ (también escrito $z_{\alpha/2}$): percentil de la
  normal estándar con probabilidad acumulada $u = 1 - \dfrac{\alpha}{2}$.

## La fórmula

Por el [[teorema-central-del-limite]], $\bar{x}$ es aproximadamente
$N(\mu_x, \sigma_x/\sqrt{n})$, entonces (`05C`):

$$
\left[\ \bar{x} - z_u\,\frac{\sigma_x}{\sqrt{n}}\ ,\ \ \bar{x} + z_u\,\frac{\sigma_x}{\sqrt{n}}\ \right]
$$

En la notación de integración de `05A`/`05B`:

$$
IC = \hat{I} \pm z_{\alpha/2}\,\frac{\sigma}{\sqrt{n}}
$$

| Símbolo | Significado |
|---------|-------------|
| $\hat{I}$ o $\bar{x}$ | estimación (el promedio de las muestras) |
| $z_{\alpha/2}$ | valor crítico según el nivel de confianza |
| $\sigma$ | desviación estándar de las muestras $f(x_i)$ (se asume conocida o se estima) |
| $n$ | número de muestras ("dardos") |
| $\sigma/\sqrt{n}$ | **error estándar (EE)** |

## Componentes

**Desviación estándar muestral:** mide la dispersión de los valores
$f(x_i)$. Se divide por $n-1$ (corrección de Bessel):

$$
\sigma = \sqrt{\frac{1}{n-1}\sum_{i=1}^{n}\left(f(x_i) - \bar{x}\right)^2}
$$

**Error estándar:** estima la desviación estándar del promedio muestral, es
decir, mide la precisión de la media estimada. Disminuye al crecer $n$:

$$
EE = \frac{\sigma}{\sqrt{n}}
$$

**Valores críticos** (hay que saberlos de memoria):

| Nivel de confianza | $z$ |
|--------------------|-----|
| 90% | 1.645 |
| 95% | 1.960 |
| 99% | 2.576 |

## Conclusión clave

Para **reducir el ancho** del IC (ganar precisión), lo más directo es
**aumentar $n$**. Como el ancho es proporcional a $1/\sqrt{n}$, reducirlo a la
mitad requiere $4n$ muestras. Subir el nivel de confianza (de 95% a 99%)
**ensancha** el intervalo.

## Observación: el factor $(b-a)$

Si $\hat{I} = (b-a)\,\bar{f}$ (ver [[integracion-por-monte-carlo]]) y $\sigma$
es la desviación de los $f(x_i)$, el error estándar **de $\hat{I}$** es
$(b-a)\,\sigma/\sqrt{n}$. Las diapositivas escriben $\hat{I} \pm z\,\sigma/\sqrt{n}$
sin ese factor, lo cual solo es exacto cuando $b - a = 1$ o cuando $\sigma$ ya
se calculó sobre los valores $(b-a) f(x_i)$. Conviene aclarar en el examen qué
$\sigma$ se está usando.

## Ejemplo numérico (propio)

Con $n = 10\,000$ muestras, $\bar{x} = 0.9080$ y $\sigma = 0.50$, al 95%:

$$
EE = \frac{0.50}{\sqrt{10\,000}} = 0.005 \quad\Rightarrow\quad IC = 0.9080 \pm 1.96 \cdot 0.005 = [0.8982,\ 0.9178]
$$

Relacionado: [[error-acotado-vs-confianza-probabilistica]], [[analisis-de-error]].
