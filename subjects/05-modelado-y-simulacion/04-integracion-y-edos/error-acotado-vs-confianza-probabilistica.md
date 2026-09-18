---
subject: modelado-y-simulacion
topic: Error acotado vs. confianza probabilística
sources:
  - 05C Lectura 1 Erraor_acotado_vs_confianza_probabilística.pdf
updated: 2026-09-18
---

# Error acotado vs. confianza probabilística

Lectura de la Clase 5 (`05C`): dos caminos para calcular una misma integral.
Uno es determinista (malla y cota de error) y el otro probabilístico (muestreo
y nivel de confianza).

## El problema guía

$$
\int_0^4 x\,e^{-x}\,dx
$$

No basta con aproximar: se busca un resultado que cumpla una **tolerancia de
error $\tau$ predefinida**.

Valor exacto (por partes, cálculo propio para verificar):
$\int_0^4 x e^{-x}\,dx = \left[-(x+1)e^{-x}\right]_0^4 = 1 - 5e^{-4} \approx 0.908422$.

> El gráfico de la diapositiva 2 muestra la curva con máximo cercano a 4, lo
> cual es incorrecto: $f(x) = xe^{-x}$ alcanza su máximo en $x = 1$ con
> $f(1) = 1/e \approx 0.368$. El gráfico de la diapositiva 7 (caja de altura
> 0.6) sí es consistente.

## Parte 1: el camino determinista

Se aplican los métodos clásicos: [[regla-del-rectangulo]],
[[regla-del-trapecio]] y [[regla-de-simpson-1-3]]. Con la cota teórica de
cada uno se despeja el $h$ máximo que garantiza $|\text{Error}| \le \tau$ (ver
[[error-de-truncamiento-y-redondeo]]).

**Pregunta guía 1:** ¿cómo calcular la integral con precisión garantizada, y
cuáles son los límites prácticos?

**Complicación del mundo real:** si solo se retienen **3 cifras decimales** en
los valores de la función, aparece el error de redondeo, que crece al achicar
$h$. Existe un $h$ óptimo con un error mínimo alcanzable, y la "garantía" de
precisión **tiene un límite**.

## Parte 2: el salto a la probabilidad

**Pregunta guía 2:** ¿se puede usar la probabilidad para resolver integrales?
Y si la respuesta es aleatoria, ¿cómo confiar en ella?

1. **Integración por dardos:** encerrar $f$ en una caja, lanzar $N$ puntos y
   contar $k$ aciertos, de modo que $\text{Área} \approx A_{\text{rect}}\cdot k/N$
   (ver [[integracion-por-monte-carlo]]).
2. **Fundamento estadístico:** distribución normal y
   [[teorema-central-del-limite]].
3. **Confianza:** [[intervalo-de-confianza]]
   $\left[\bar{x} \pm z_u\,\sigma_x/\sqrt{n}\right]$ con $u = 1 - \alpha/2$.

## Las dos filosofías

| | Métodos clásicos (deterministas) | Monte Carlo (probabilístico) |
|---|---|---|
| **Filosofía** | aproximación geométrica y sistemática | muestreo aleatorio y convergencia estadística |
| **Resultado** | un único valor aproximado | un intervalo de confianza |
| **Garantía** | cota superior del error de truncamiento: $\lvert\text{Error}\rvert \le \text{Cota}$ | probabilidad $1-\alpha$ de que el valor verdadero esté en el intervalo |
| **Limitación / ventaja** | vulnerable al redondeo acumulativo; la cota teórica puede ser inalcanzable | robusto frente a la dimensionalidad y la complejidad; se gana precisión aumentando $n$ |

**Cuándo usar cada uno:** si hace falta una garantía de error acotado en un
sistema ideal (función suave, baja dimensión), conviene el determinista. Si
hace falta una estimación confiable en un contexto complejo, aleatorio o de
alta dimensión, conviene Monte Carlo.

Relacionado: [[integracion-numerica]], [[metodo-de-monte-carlo]],
[[formulas-de-newton-cotes]].
