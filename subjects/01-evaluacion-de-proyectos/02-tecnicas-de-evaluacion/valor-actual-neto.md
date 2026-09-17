---
subject: evaluacion-de-proyectos
topic: VAN (Valor Actual Neto)
sources:
  - EPT Clase 2_Matematica Financiera - Parte I.pdf
  - EPT_Clase3y4_MatematicaFinanciera_II_Ejercicios_Soluciones.xlsx
  - EPT Clase 5_Matematica Financiera - Parte III.pdf
updated: 2026-09-14
tags:
  - evaluacion-de-proyectos/tecnicas
  - indicador
  - enfoque-financiero
  - parcial-1
---

# VAN (Valor Actual Neto)

> [!abstract] En una frase
> El VAN trae todos los flujos del proyecto a **pesos de hoy** y les resta la
> inversión: dice **cuánto valor crea el proyecto**, ya descontado lo que exige el
> capital.

**Prerrequisitos:** [[interes-compuesto]] (despejar $C_0$) y [[flujo-de-fondos]].
**Sigue con:** [[indice-de-rentabilidad]] y [[tasa-interna-de-retorno]].

---

## El problema que resuelve

El [[roi-y-roa|ROI]] suma pesos de distintos años como si fueran iguales. Pero
$\$3.000$ del año 5 **no** valen lo mismo que $\$3.000$ de hoy. Para sumarlos
primero hay que pasarlos a la misma "moneda".

## Intuición

> [!example] Analogía: pesos de distintos años son monedas distintas
> No podés sumar 100 dólares con 100 euros y decir "tengo 200". Primero convertís
> todo a una misma moneda con el **tipo de cambio**.
>
> - "Pesos del año 3" y "pesos de hoy" son **monedas distintas**.
> - La **tasa de descuento** es el tipo de cambio entre ellas.
> - Descontar un flujo $= FF_t / (1+i)^t$ es convertirlo a pesos de hoy.
> - El VAN es el **saldo final** una vez todo convertido a la misma moneda.

---

## Fórmula

$$
VAN = -C_0 + \sum_{t=1}^{n} \frac{FF_t}{(1+i)^t}
$$

Como en la planilla el período 0 ya lleva la inversión con signo negativo, se
escribe como la suma de todos los flujos descontados:

$$
VAN = \sum_{t=0}^{n} \frac{FF_t}{(1+i)^t}
$$

| Símbolo | Significado |
|---|---|
| $C_0$ | Inversión inicial (sale hoy, no se descuenta) |
| $FF_t$ | Flujo neto del período $t$ |
| $i$ | Tasa de descuento: el costo de oportunidad del capital |
| $(1+i)^t$ | Factor que convierte pesos del año $t$ a pesos de hoy |

**Por qué tiene esta forma:** cada término es la fórmula de $C_0$ del
[[interes-compuesto]], $C_0 = C_n/(1+i)^n$, aplicada a un flujo. El VAN suma
todos esos valores actuales.

> [!tip] Dirección: tasa más alta, VAN más bajo
> La tasa está en el **denominador**. Si $i$ sube, $(1+i)^t$ crece, cada flujo
> descontado se achica y el VAN **baja**. Por eso elegir bien la tasa es crítico.

---

## Regla de decisión

| Resultado | Significado | Decisión |
|---|---|---|
| $VAN > 0$ | Rinde **más** que la tasa exigida: crea valor | ✅ Conviene |
| $VAN = 0$ | Rinde exactamente la tasa exigida | Indiferente |
| $VAN < 0$ | Rinde **menos** que la tasa exigida: destruye valor | ❌ No conviene |

> [!warning] VAN negativo no es "perder plata"
> Un VAN negativo **no significa que el proyecto dé pérdida**. Significa que rinde
> menos que la alternativa representada por la tasa (el
> [[tasa-de-interes|costo de oportunidad]]). El proyecto del ejemplo tiene VAN
> $+\$5.000$ a tasa $0\%$ y VAN negativo al $20\%$: los flujos son los mismos, lo
> que cambia es la exigencia.

---

## Ejemplo con variación

**Caso:** inversión $\$10.000$, flujos de $\$3.000$ anuales durante 5 años, tasa
$10\%$.

| $t$ | $FF_t$ | $FF_t / 1{,}10^t$ |
|---|---|---|
| 0 | $-10.000$ | $-10.000{,}00$ |
| 1 | $3.000$ | $2.727{,}27$ |
| 2 | $3.000$ | $2.479{,}34$ |
| 3 | $3.000$ | $2.253{,}94$ |
| 4 | $3.000$ | $2.049{,}04$ |
| 5 | $3.000$ | $1.862{,}76$ |
| | **VAN** | $\mathbf{1.372{,}36}$ |

$VAN \approx \$1.372 > 0$: **el proyecto conviene**.

**Variación:** los mismos flujos a distintas tasas.

| Tasa | $0\%$ | $10\%$ | $15\%$ | $20\%$ |
|---|---|---|---|---|
| VAN | $\$5.000$ | $\$1.372$ | $\$56$ | $-\$1.028$ |

![[perfil-del-van.svg|600]]

Fijate en dónde la curva **cruza el cero**: en $15{,}24\%$. Esa tasa es la
[[tasa-interna-de-retorno|TIR]]. A la izquierda el VAN es positivo; a la
derecha, negativo.

---

## La tasa $i$ es el corazón del cálculo

La $i$ no es un dato arbitrario: es el costo de oportunidad del capital. Todo el
bloque de [[tasa-de-descuento]] responde de dónde sale ese número:
[[wacc]] si se conoce la estructura de financiamiento, [[capm]] si hay que estimar
el costo del capital propio.

> [!important] Regla de oro
> Antes de calcular cualquier VAN o TIR, hay que entender **de dónde sale la tasa**.

**En Excel:** con la planilla de [[flujo-de-fondos]], el VAN es la suma de la
columna "flujo descontado" incluyendo el período 0, o la última celda del
acumulado descontado.

---

## Errores comunes

| Error | Lo correcto |
|---|---|
| Descontar la inversión del período 0. | $(1+i)^0 = 1$: la inversión entra tal cual. |
| Usar el mismo exponente para todos los flujos. | Cada flujo se descuenta con **su** $t$. |
| Dividir por $(1 + i \cdot t)$. | Eso es simple; el descuento es compuesto, $(1+i)^t$. |
| "VAN negativo es pérdida contable." | Es rendir menos que la tasa exigida. |
| Usar la función `VNA` de Excel incluyendo el período 0. | `VNA` asume que el primer flujo está en $t=1$. Sumá la inversión aparte o usá la columna descontada. |

---

## Autoevaluación

1. Inversión $\$15.000$; flujos $\$4.000$, $\$5.000$, $\$5.000$, $\$6.000$,
   $\$6.000$; tasa $12\%$. ¿Conviene?
   > [!question]- Respuesta
   > $VAN = \$3.333{,}97 > 0$. **Sí conviene** al $12\%$.

2. Invertís $\$10.000$ y recibís $\$15.000$ dentro de 5 años. Tasa $10\%$. ¿VAN?
   > [!question]- Respuesta
   > $VAN = -10.000 + 15.000/1{,}10^5 = -10.000 + 9.313{,}82 = -\$686{,}18$.
   > No conviene, aunque el ROI sea $50\%$.

3. Si la tasa de descuento sube, ¿qué le pasa al VAN? ¿Y a la TIR?
   > [!question]- Respuesta
   > El VAN **baja** (la tasa está en el denominador). La TIR **no cambia**: es una
   > propiedad de los flujos, no depende de la tasa externa.

---

## Relacionado

- [[indice-de-rentabilidad]]: el VAN relativizado por la inversión.
- [[tasa-interna-de-retorno]]: la tasa que hace $VAN = 0$.
- [[interes-compuesto]]: la fórmula de descuento que usa cada término.
- [[tasa-de-descuento]]: de dónde sale la $i$.
- [[ejercicios-van-tir]]: práctica resuelta.
