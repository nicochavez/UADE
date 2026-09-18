---
subject: modelado-y-simulacion
topic: Error de truncamiento vs. error de redondeo y paso óptimo
sources:
  - 05C Lectura 1 Erraor_acotado_vs_confianza_probabilística.pdf
updated: 2026-09-18
---

# Error de truncamiento y error de redondeo

Dos fuentes de error que tiran en **direcciones opuestas** cuando se achica el
tamaño del paso $h$. Su equilibrio define un **$h$ óptimo** (los "pasos
óptimos" de la Clase 3, retomados en la lectura `05C`).

## Error de truncamiento

Es el error **inherente al método de aproximación**: aparece por reemplazar la
función por rectángulos, trapecios o parábolas, o por cortar una serie de
Taylor. Se estudia suponiendo **precisión infinita** en los cálculos.

- **Disminuye** cuando $h$ se achica: más subintervalos dan mejor aproximación.
- Cada método tiene una fórmula que lo acota en función de $h$ y de las
  derivadas de $f$. Ver [[formulas-de-newton-cotes]] y [[diferencias-finitas]].

## Error de redondeo

Proviene de la **precisión finita** de la aritmética: por ejemplo, retener solo
3 cifras decimales en cada valor de la función (el escenario de `05C`).

- **Aumenta** cuando $h$ se achica: más subintervalos implican más cálculos, y
  cada uno suma su pequeño error de redondeo.

## El dilema: existe un $h$ óptimo

$$
E_{\text{total}}(h) = E_{\text{truncamiento}}(h) + E_{\text{redondeo}}(h)
$$

La curva de error total tiene forma de "U". Su mínimo (el **error mínimo
alcanzable**) ocurre en un $h_{\text{óptimo}}$:

- Para $h > h_{\text{óptimo}}$ domina el truncamiento, y conviene achicar $h$.
- Para $h < h_{\text{óptimo}}$ domina el redondeo, y achicar $h$ **empeora**
  el resultado.

**Consecuencia:** reducir $h$ indefinidamente es contraproducente. Si la
tolerancia pedida está por debajo del error mínimo alcanzable, la precisión
garantizada **se vuelve inalcanzable**, sin importar cuántos subintervalos se
usen.

## Cómo se busca $h$ para una tolerancia (sin redondeo)

Procedimiento de `05C` para garantizar $|\text{Error}| \le \tau$:

1. **Establecer la condición:** $|\text{Error}| \le \tau$.
2. **Usar la cota teórica** del método (rectángulos, trapecios o Simpson).
3. **Despejar $h$:** resolver la inecuación para obtener el $h$ máximo
   permitido y, de ahí, el número de subintervalos $n = (b-a)/h$.

Ejemplo con trapecio compuesto: si $|E| \le \dfrac{(b-a)\,h^2}{12}\,\max|f''|$,
entonces

$$
h \le \sqrt{\frac{12\,\tau}{(b-a)\max|f''|}}
$$

Este límite práctico de los métodos deterministas es lo que motiva el salto a
Monte Carlo en [[error-acotado-vs-confianza-probabilistica]].

Relacionado: [[analisis-de-error]], [[regla-del-trapecio]], [[regla-de-simpson-1-3]].
