---
subject: evaluacion-de-proyectos
topic: Práctica de WACC y CAPM (Clases 5 y 6)
sources:
  - EPT_Clase6_EjerciciosRepasoWACC_CAPM_Soluciones.pdf
  - EPT Clase 5_Matematica Financiera - Parte III.pdf
  - EPT_Clase5_MatematicaFinancieraIII_Calculadora_WACC.xlsx
  - EPT_Clase5_MatematicaFinancieraIII_Calculadora_CAPM.xlsx
updated: 2026-09-14
tags:
  - evaluacion-de-proyectos/exams
  - practica
  - parcial-1
---

# Ejercicios: WACC y CAPM

> [!abstract] Cómo usar esta página
> Todos tienen solución oficial de la cátedra. Cada ejercicio **cambia una sola
> variable** para aislar su efecto: antes de abrir la solución, predecí si el
> resultado sube o baja y por qué.

**Teoría:** [[wacc]], [[escudo-fiscal]], [[capm]], [[beta]], [[riesgo-pais]],
[[tasa-libre-de-riesgo]].

---

## Parte A: WACC

$$
K_p = K_d(1-t)
\qquad
WACC = \frac{D}{D+PN}K_p + \frac{PN}{D+PN}K_e
$$

**A1.** $K_d = 20\%$, $t = 35\%$. ¿$K_p$?

> [!question]- Solución
> $K_p = 13\%$. Los 7 puntos de diferencia son el [[escudo-fiscal]]:
> $t \cdot K_d = 0{,}35 \times 20\% = 7\%$.

**A2.** $D = \$95$, $PN = \$5$, $K_p = 13\%$, $K_e = 27\%$. ¿WACC? *Predicción: ¿más
cerca de $K_p$ o de $K_e$?*

> [!question]- Solución
> $WACC = 0{,}95 \times 13\% + 0{,}05 \times 27\% = 13{,}7\%$. Queda pegado a $K_p$
> porque la deuda pesa $95\%$. Si $PN = 0$, el WACC sería exactamente $K_p$.

**A3.** $K_p = 13\%$, $K_e = 27\%$. **A:** $D = 20$, $PN = 80$. **B:** $D = 80$,
$PN = 20$. ¿Cuál tiene WACC más alto?

> [!question]- Solución
> $A = 24{,}2\%$, $B = 15{,}8\%$. Financiarse más con capital propio da un WACC
> **más alto**, porque $K_e = 27\% > K_p = 13\%$. La deuda no es gratis, pero acá es
> más barata.

**A4.** $K_d = 20\%$, $D = 80$, $PN = 20$, $K_e = 27\%$. Comparar $t = 35\%$ con
$t = 45\%$. *Predicción: ¿más impuesto sube o baja el WACC?*

> [!question]- Solución
> $K_p$: $13\% \to 11\%$. WACC: $15{,}8\% \to 14{,}2\%$.
> Contraintuitivo: **un impuesto más alto agranda el escudo fiscal**, así que el
> costo neto de la deuda baja.

**A5.** $D = PN = \$50$, $K_e = 30\%$, $K_d = 18\%$, $t = 35\%$. ¿WACC?

> [!question]- Solución
> $K_p = 11{,}7\%$. $WACC = 5{,}85\% + 15\% = 20{,}85\%$.
> Con pesos idénticos, el capital ponderado ($15\%$) casi triplica al de la deuda
> ($5{,}85\%$): **la diferencia la hace la tasa, no la proporción**.

**A6.** $D = \$95$, $PN = \$5$, $K_d = 20\%$, $t = 35\%$. Comparar $K_e = 27\%$ con
$K_e = 50\%$.

> [!question]- Solución
> $13{,}7\% \to 14{,}85\%$: solo $+1{,}15$ puntos. $K_e$ subió 23 puntos y el WACC
> casi no se movió, porque el capital propio pesa apenas $5\%$.

### Integrador A: empresa de software

Activo $\$250.000$, $D = 30\%$, $PN = 70\%$, $K_e = 24\%$, $T_p = 18\%$,
$T_{iigg} = 35\%$. ¿WACC?

> [!question]- Solución
> $$K_p = 18\% \times 0{,}65 = 11{,}7\%$$
> $$WACC = 0{,}30 \times 11{,}7\% + 0{,}70 \times 24\% = 3{,}51\% + 16{,}8\% = \mathbf{20{,}31\%}$$

---

## Parte B: CAPM

$$
E(r_i) = r_f + \beta[E(r_m) - r_f] + RP
$$

**Datos base:** $r_f = 4{,}72\%$, $E(r_m) = 9{,}0\%$, $RP = 5{,}05\%$ (salvo
indicación). Caso de referencia: $\beta = 1{,}12$, $E(r_i) = 14{,}56\%$.

**B1.** Comparar $\beta = 0{,}5$ con $\beta = 1{,}8$.

> [!question]- Solución
> $11{,}91\%$ vs. $17{,}47\%$: $5{,}56$ puntos de diferencia, que es
> $(1{,}8 - 0{,}5) \times 4{,}28\%$.

**B2.** $RP = 0\%$. *Predicción: ¿cuánto baja?*

> [!question]- Solución
> $9{,}51\%$: exactamente $5{,}05$ puntos menos, el valor del RP.

**B3.** Combinar $\beta \in \{1{,}12;\ 0{,}5\}$ con $RP \in \{4\%;\ 15\%\}$.
*Predicción: ¿el salto de RP es mayor con el beta alto?*

> [!question]- Solución
> | $\beta$ | $RP = 4\%$ | $RP = 15\%$ | Salto |
> |---|---|---|---|
> | $1{,}12$ | $13{,}51\%$ | $24{,}51\%$ | $11$ pts |
> | $0{,}5$ | $10{,}86\%$ | $21{,}86\%$ | $11$ pts |
>
> **No.** El salto es idéntico: el RP no pasa por el beta.

**B4.** Descomponer las primas con $\beta = 1{,}12$.

> [!question]- Solución
> Prima de mercado: $9{,}0 - 4{,}72 = 4{,}28\%$. Ajustada: $1{,}12 \times 4{,}28 = 4{,}79\%$.

**B5.** Usar $\beta = 0{,}17$ (General Mills) para el proyecto de tecnología.

> [!question]- Solución
> $10{,}50\%$, más de 4 puntos por debajo del correcto ($14{,}56\%$). Usar el beta
> de alimentos subestima la tasa porque la demanda de alimentos es mucho más
> estable.

**B6.** $r_f = 6{,}72\%$ en lugar de $4{,}72\%$. *Predicción: ¿sube o baja?*

> [!question]- Solución
> $14{,}32\%$: **baja $0{,}24$ puntos.**
> $r_f$ aparece dos veces: suma directo ($+2$ pts) y resta dentro de la prima, que
> se multiplica por beta ($-2 \times 1{,}12 = -2{,}24$ pts). Con $\beta > 1$ gana el
> segundo efecto. Ver [[tasa-libre-de-riesgo]].

> [!tip] Las tres lecciones de la Parte B
> 1. **Beta multiplica, RP no** (B2, B3, B4).
> 2. **El beta tiene que ser del sector correcto** (B5).
> 3. **$r_f$ son dos ingredientes con signo contrario** (B6).

### Integrador B: el mismo $K_e$, dos caminos

Misma empresa de software del integrador A, ahora estimando $K_e$ con CAPM:
$r_f = 4{,}3\%$, $E(r_m) = 8{,}5\%$, $\beta = 1{,}12$ (Computer Services),
$RP = 4{,}9\%$ (490 pb al 7/9). Calcular $K_e$ y recalcular el WACC.

> [!question]- Solución
> $$\text{Prima} = 8{,}5\% - 4{,}3\% = 4{,}2\% \;\Rightarrow\; 1{,}12 \times 4{,}2\% = 4{,}704\%$$
> $$E(r_i) = 4{,}3\% + 4{,}704\% + 4{,}9\% = \mathbf{13{,}90\%}$$
>
> | | $K_e$ | Capital ponderado | WACC |
> |---|---|---|---|
> | Original (asumido) | $24\%$ | $16{,}80\%$ | $20{,}31\%$ |
> | Con CAPM | $13{,}90\%$ | $9{,}73\%$ | $13{,}24\%$ |
> | **Diferencia** | $-10{,}10$ pts | | **$-7{,}07$ pts** |
>
> El $K_e$ asumido estaba muy por encima del estimado: es la evidencia de cuánto
> puede cambiar una decisión según de dónde salga la tasa. Ver [[wacc-vs-capm]].

---

## Relacionado

- [[wacc]] y [[capm]]: la teoría.
- [[wacc-vs-capm]]: interpretación del integrador.
- [[repaso-primer-parcial]]: fórmulas y errores típicos.
- [[parciales-y-practica]]: calendario.
