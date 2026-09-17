---
subject: evaluacion-de-proyectos
topic: Escudo fiscal y costo de la deuda neto de impuestos
sources:
  - EPT Clase 5_Matematica Financiera - Parte III.pdf
  - EPT_Clase6_EjerciciosRepasoWACC_CAPM_Soluciones.pdf
updated: 2026-09-14
tags:
  - evaluacion-de-proyectos/tasa-de-descuento
  - formula
  - parcial-1
---

# Escudo fiscal

> [!abstract] En una frase
> Los intereses de la deuda **se restan antes de pagar Ganancias**, así que el
> Estado "te devuelve" parte de ellos. Por eso la deuda cuesta menos de lo que dice
> el contrato: $K_p = K_d(1-t)$.

**Prerrequisitos:** [[ecuacion-contable-fundamental]], qué es la deuda.
**Sigue con:** [[wacc]], donde entra $K_p$.

---

## El problema que resuelve

Si pedís un préstamo al $20\%$, ¿la deuda te cuesta $20\%$? **No.** Esos intereses
bajan la utilidad sobre la que se paga Impuesto a las Ganancias, así que parte del
costo lo absorbe el ahorro impositivo.

## Intuición: antes y después de la deuda

Una empresa gana $\$100$ antes de intereses e impuestos. Tasa de Ganancias
$35\%$.

```
SIN deuda                                CON deuda (intereses de $20)
Ganancia antes de intereses   $100       Ganancia antes de intereses   $100
Intereses                      -$0       Intereses                     -$20
Base imponible                $100       Base imponible                 $80
Impuesto (35%)                -$35       Impuesto (35%)                -$28
                                                                ─────────────
                                         Ahorro de impuesto: $35 - $28 = $7
```

Los $\$20$ de intereses **en realidad cuestan $\$13$**: $\$20$ pagados menos
$\$7$ que no se pagan de impuesto. Esos $\$7$ son el **escudo fiscal**.

> [!example] Analogía: un reintegro sobre los intereses
> Es como si el Estado tuviera una promoción: "por cada peso de intereses que
> pagues, te reintegro $t$ pesos de impuesto". Con $t = 35\%$, pagás $\$1$ de
> interés y te vuelven $\$0{,}35$. El costo efectivo es $\$0{,}65$.

---

## Fórmula

$$
K_p = K_d \cdot (1 - t)
$$

| Símbolo | Nombre | Qué es |
|---|---|---|
| $K_d$ (o $T_p$) | Costo de la deuda **antes** de impuestos | La tasa del contrato con el acreedor |
| $K_p$ | Costo de la deuda **neto** de impuestos | El costo real para la empresa |
| $t$ (o $T_{iigg}$) | Tasa de impuesto a las ganancias | La tasa efectiva del impuesto |
| $t \cdot K_d$ | Escudo fiscal | Lo que se ahorra por deducir intereses |

**Por qué tiene esta forma:** de cada peso de interés, se recupera $t$ en
impuestos. Lo que queda es $1 - t$.

> [!danger] En el WACC va $K_p$, nunca $K_d$
> Este es el error número uno de los ejercicios de WACC.

## Ejemplo

$K_d = 20\%$, $t = 35\%$:

$$
K_p = 20\% \times (1 - 0{,}35) = 20\% \times 0{,}65 = 13\%
$$

Los 7 puntos de diferencia son el escudo fiscal: $t \cdot K_d = 0{,}35 \times 20\% = 7\%$.

---

## El resultado contraintuitivo

> [!warning] Un impuesto más alto abarata la deuda
> Cuanto más alto es Ganancias, **más ahorro** genera deducir intereses, así que
> el costo neto de la deuda **baja**.
>
> Con $K_d = 20\%$, $D = \$80$, $PN = \$20$, $K_e = 27\%$:
>
> | $t$ | $K_p$ | WACC |
> |---|---|---|
> | $35\%$ | $13\%$ | $15{,}8\%$ |
> | $45\%$ | $11\%$ | $14{,}2\%$ |
>
> Esto no significa que a la empresa le convenga pagar más impuestos en total;
> solo que **la deuda, en relación**, se vuelve más barata.

---

## Errores comunes

| Error | Lo correcto |
|---|---|
| Usar $K_d$ en el WACC. | Usar $K_p = K_d(1-t)$. |
| Calcular $K_d \cdot t$ y usarlo como costo. | Eso es el **ahorro**; el costo es $K_d(1-t)$. |
| "Más impuesto, deuda más cara." | Más impuesto, deuda **más barata**. |
| Aplicar $(1-t)$ también a $K_e$. | Los dividendos no son deducibles; $K_e$ no se ajusta. |

---

## Autoevaluación

1. $K_d = 18\%$, $t = 35\%$. ¿$K_p$ y escudo fiscal?
   > [!question]- Respuesta
   > $K_p = 18\% \times 0{,}65 = 11{,}7\%$. Escudo: $0{,}35 \times 18\% = 6{,}3$ puntos.

2. ¿Por qué el $(1-t)$ se aplica a la deuda y no al capital propio?
   > [!question]- Respuesta
   > Porque los **intereses** son un gasto deducible de Ganancias, mientras que lo
   > que se paga a los accionistas (dividendos) sale de la utilidad **después** de
   > impuestos.

---

## Relacionado

- [[wacc]]: donde se usa $K_p$.
- [[ecuacion-contable-fundamental]]: la deuda como fuente de financiamiento.
- [[ejercicios-wacc-capm]]: ejercicios 1 y 4.
