---
subject: evaluacion-de-proyectos
topic: CAPM (Capital Asset Pricing Model)
sources:
  - EPT Clase 5_Matematica Financiera - Parte III.pdf
  - EPT_Clase5_MatematicaFinancieraIII_Calculadora_CAPM.xlsx
  - EPT_Clase6_EjerciciosRepasoWACC_CAPM_Soluciones.pdf
updated: 2026-09-14
tags:
  - evaluacion-de-proyectos/tasa-de-descuento
  - formula
  - parcial-1
---

# CAPM

> [!abstract] En una frase
> El CAPM arma la tasa que exigen los accionistas **por capas**: el piso sin riesgo,
> más la prima del mercado escalada por el beta, más el riesgo país.

**Prerrequisitos:** [[tasa-libre-de-riesgo]] y [[wacc]], donde el resultado se usa como $K_e$.
**Sigue con:** [[beta]] y [[riesgo-pais]], los dos datos más delicados.

---

## El problema que resuelve

El [[wacc]] necesita $K_e$, el costo del capital propio. Pero **nadie te lo
dicta**: los accionistas no firman un contrato con una tasa. Hace falta un método
para estimar cuánto deberían exigir, **comparando el riesgo del proyecto con el
del mercado**.

> [!important] $E(r_i) = K_e$
> El resultado del CAPM y el costo del capital propio del WACC son **el mismo
> concepto** con dos nombres, según desde qué fórmula se lo mire.

## Intuición

> [!example] Analogía: la tarifa de un envío a domicilio
> Una app de delivery calcula el costo del envío en tres capas:
>
> | Delivery | CAPM |
> |---|---|
> | **Tarifa base:** la paga cualquier pedido | $r_f$: el piso sin riesgo |
> | **Recargo por distancia:** tarifa por km multiplicada por los km | $\beta \times$ prima de mercado |
> | **Recargo por zona:** fijo para ese barrio, sin importar la distancia | $RP$: igual para toda empresa del país |
>
> El recargo por zona **no se multiplica** por los km. Igual el riesgo país: **no
> se multiplica por $\beta$**.

---

## Fórmula

$$
E(r_i) = r_f + \beta\,[\,E(r_m) - r_f\,] + RP
$$

```
┌───────────────────────────────────────────┐
│ RP              riesgo país (aditivo)     │  5,05%
├───────────────────────────────────────────┤
│ beta x [E(rm) - rf]  prima de mercado     │  4,79%
├───────────────────────────────────────────┤
│ rf              tasa libre de riesgo      │  4,72%
└───────────────────────────────────────────┘
                     total E(ri) = 14,56%
```

| Variable | Significado |
|---|---|
| $E(r_i)$ | Rentabilidad esperada del activo o proyecto ($= K_e$) |
| $r_f$ | [[tasa-libre-de-riesgo]] (bono del Tesoro de EE.UU. a 10 años) |
| $E(r_m)$ | Rentabilidad esperada del mercado de referencia (p. ej. S&P 500) |
| $[E(r_m) - r_f]$ | **Prima de riesgo de mercado**: lo que el mercado paga en promedio sobre el activo sin riesgo |
| $\beta$ | Sensibilidad del activo respecto a su *benchmark* (ver [[beta]]) |
| $RP$ | [[riesgo-pais]]: término **aditivo**, no se multiplica por $\beta$ |

**Por qué tiene esta forma:** invertir en el mercado paga una prima sobre $r_f$.
Un activo más volátil que el mercado ($\beta > 1$) tiene que pagar **más** que esa
prima; uno más estable ($\beta < 1$), menos. El riesgo país es un costo extra de
operar en ese país, igual para todos.

---

## De dónde sale cada dato

| Dato | Fuente | ¿Cambia seguido? |
|---|---|---|
| $r_f$ | FRED, serie DGS10 | Todos los días |
| $E(r_m)$ | $r_f$ + ERP de Damodaran | Periódicamente |
| $\beta$ | Damodaran, dataset **Global**, sector más afín | Una vez al año (enero) |
| $RP$ | EMBI+ de JP Morgan (Ámbito) | Todos los días |

### Cómo se estima $E(r_m)$

A diferencia de $r_f$, $E(r_m)$ **no es observable**: es una expectativa. La
solución práctica es estimar la diferencia $[E(r_m) - r_f]$, llamada **ERP**
(*Equity Risk Premium*):

1. Entrar a la web de Damodaran: `pages.stern.nyu.edu/~adamodar` (NYU Stern).
2. Buscar **"Equity Risk Premiums"** y localizar la línea
   *"Implied ERP on [fecha] ="*, que muestra 5 variantes.
3. Usar **siempre** la opción **"Trailing 12 month cash yield"** (retornos por
   dividendos y recompras). Las otras cuatro no se evalúan; se usa siempre la
   misma para ser consistentes.
4. Calcular $E(r_m) = r_f + ERP$ con la $r_f$ del mismo período.

> [!note] Dato de referencia (1 de agosto de 2026)
> $E(r_m) = 4{,}74\% + 4{,}23\% = 8{,}97\%$.

---

## Cálculo paso a paso

**Caso de la clase:** proyecto de tecnología en una empresa argentina que **no
cotiza en bolsa**, por eso se incorpora el riesgo país.

**Datos:** $r_f = 4{,}72\%$; $E(r_m) = 9{,}0\%$ (S&P 500); $\beta = 1{,}12$
(*Computer Services*, dataset Global de Damodaran, enero 2026);
$RP = 5{,}05\%$ (505 pb, EMBI+ al 21 de agosto de 2026).

**1. Prima de mercado**

$$E(r_m) - r_f = 9{,}0\% - 4{,}72\% = 4{,}28\%$$

**2. Prima ajustada por beta**

$$1{,}12 \times 4{,}28\% = 4{,}79\%$$

Con $\beta = 1{,}12$ el sector amplifica levemente el riesgo del mercado.

**3. Sumar las tres capas**

$$E(r_i) = 4{,}72\% + 4{,}79\% + 5{,}05\% = \mathbf{14{,}56\%}$$

**Interpretación:** la empresa debería exigirle a este proyecto al menos
$14{,}56\%$ anual para que valga la pena frente a otras alternativas. Ese número
es su [[trema]] y es el que reemplaza a $K_e$ si se arma el [[wacc]] completo.

---

## Sensibilidades

**Riesgo país:** con $r_f$, $E(r_m)$ y $\beta$ fijos, el $RP$ se traslada **punto
por punto**:

| $RP$ | 0 pb | 400 pb | 505 pb | 1.000 pb | 2.000 pb |
|---|---|---|---|---|---|
| $E(r_i)$ | $9{,}51\%$ | $13{,}51\%$ | $14{,}56\%$ | $19{,}51\%$ | $29{,}51\%$ |

**Beta:** cada punto de $\beta$ mueve el resultado en una prima de mercado
($4{,}28$ puntos):

| $\beta$ | $0{,}17$ | $0{,}5$ | $1{,}12$ | $1{,}8$ |
|---|---|---|---|---|
| $E(r_i)$ | $10{,}50\%$ | $11{,}91\%$ | $14{,}56\%$ | $17{,}47\%$ |

---

## Errores comunes

| Error | Lo correcto |
|---|---|
| Multiplicar $RP$ por $\beta$. | $RP$ se suma aparte. |
| Multiplicar $\beta$ por $E(r_m)$ en lugar de por la prima. | $\beta \times [E(r_m) - r_f]$. |
| Pasar $505$ pb como $50{,}5\%$. | $505$ pb $= 5{,}05\%$. |
| Usar el beta de otro sector. | Beta del sector más afín al proyecto. |
| Olvidar el $RP$ en una empresa argentina que no cotiza. | Hay que sumarlo. |

---

## Autoevaluación

1. $r_f = 4{,}3\%$, $E(r_m) = 8{,}5\%$, $\beta = 1{,}12$, $RP = 490$ pb. ¿$E(r_i)$?
   > [!question]- Respuesta
   > Prima: $8{,}5 - 4{,}3 = 4{,}2\%$. Ajustada: $1{,}12 \times 4{,}2 = 4{,}704\%$.
   > $E(r_i) = 4{,}3 + 4{,}704 + 4{,}9 = 13{,}90\%$.

2. Con los datos del caso de clase, ¿cuánto sube $E(r_i)$ si el riesgo país pasa de
   505 a 1.000 pb? ¿Depende del beta?
   > [!question]- Respuesta
   > Sube exactamente $4{,}95$ puntos (de $14{,}56\%$ a $19{,}51\%$). **No depende
   > del beta**, porque $RP$ es aditivo.

3. ¿Por qué el resultado del CAPM puede usarse en el WACC?
   > [!question]- Respuesta
   > Porque $E(r_i)$ **es** $K_e$: la rentabilidad que exigen los accionistas.

---

## Para ir más allá (fuera del programa)

En la práctica profesional el beta del sector se ajusta a la estructura de deuda
de la empresa evaluada (**apalancamiento y desapalancamiento del beta**). No entra
en la materia, pero así trabajan los analistas de valuación.

## Relacionado

- [[beta]]: el multiplicador de la prima de mercado.
- [[riesgo-pais]]: el término aditivo.
- [[tasa-libre-de-riesgo]]: el piso, que aparece dos veces.
- [[wacc-vs-capm]]: cómo se combinan.
- [[ejercicios-wacc-capm]]: Parte B.
