---
subject: evaluacion-de-proyectos
topic: Riesgo país (RP) y el EMBI+
sources:
  - EPT Clase 5_Matematica Financiera - Parte III.pdf
  - EPT_Clase5_MatematicaFinancieraIII_Calculadora_CAPM.xlsx
  - EPT_Clase6_EjerciciosRepasoWACC_CAPM_Soluciones.pdf
updated: 2026-09-14
tags:
  - evaluacion-de-proyectos/tasa-de-descuento
  - concepto
  - parcial-1
---

# Riesgo país (RP)

> [!abstract] En una frase
> El riesgo país es la **sobretasa que paga un país** respecto al bono sin riesgo
> de EE.UU. En el CAPM se **suma** tal cual: es igual para todas las empresas del
> país, sin importar su beta.

**Prerrequisitos:** [[tasa-libre-de-riesgo]] y [[beta]].
**Sigue con:** [[wacc-vs-capm]], el cierre del bloque.

---

## Qué es

Mide el **diferencial** (*spread*) entre lo que rinde un bono soberano de un país
y la [[tasa-libre-de-riesgo]] internacional. A mayor *spread*, mayor es el riesgo
percibido de que el país no pague su deuda.

Ese riesgo se traslada como un **costo financiero extra para cualquier empresa
local** que opere allí y no cotice en bolsa, algo frecuente en mercados
emergentes como Argentina.

## Intuición

> [!example] Analogía: el seguro del auto según el barrio
> Dos conductores viven en el mismo barrio. Uno maneja con cuidado ($\beta$ bajo) y
> el otro es imprudente ($\beta$ alto).
>
> - Por su **forma de manejar**, el imprudente paga una prima mucho mayor: eso
>   escala con $\beta$.
> - Pero los dos pagan **el mismo recargo por el barrio** (robos, calles): eso es
>   el $RP$.
>
> Mudarse a un barrio más peligroso les sube el seguro **la misma cantidad** a los
> dos.

---

## De dónde sale el dato

Para Argentina se usa el **EMBI+** (*Emerging Markets Bond Index Plus*) de **JP
Morgan**, calculado desde 1998.

- Se consulta en tiempo real en Ámbito Financiero
  (`ambito.com/contenidos/riesgo-pais.html`) o en cualquier casa de bolsa local.
- Junto con $r_f$, es el otro dato de mercado que **cambia todos los días**.

### Puntos básicos a porcentaje

$$
100 \text{ pb} = 1\% = 0{,}01
$$

| Puntos básicos | Porcentaje (dividir por $100$) | Decimal (dividir por $10.000$) |
|---|---|---|
| $505$ pb | $5{,}05\%$ | $0{,}0505$ |
| $490$ pb | $4{,}9\%$ | $0{,}049$ |
| $1.000$ pb | $10\%$ | $0{,}10$ |

> [!note] Valores usados en clase
> $505$ pb (21 de agosto de 2026) y $490$ pb (7 de septiembre de 2026).

---

## Cómo entra en el CAPM

$$
E(r_i) = r_f + \beta\,[E(r_m) - r_f] + \underbrace{RP}_{\text{aditivo puro}}
$$

> [!danger] El RP no pasa por el beta
> La intuición falsa es que todo en la fórmula "escala" con el riesgo del
> proyecto. El riesgo país es un **piso parejo** para cualquier empresa del país,
> sin importar cuánto se mueva respecto al mercado.

**La prueba (ejercicio 3 de la práctica):** pasar de $RP = 4\%$ a $RP = 15\%$ sube
$E(r_i)$ exactamente 11 puntos **con cualquier beta**:

| $\beta$ | $RP = 4\%$ | $RP = 15\%$ | Diferencia |
|---|---|---|---|
| $1{,}12$ | $13{,}51\%$ | $24{,}51\%$ | $11{,}00$ pts |
| $0{,}50$ | $10{,}86\%$ | $21{,}86\%$ | $11{,}00$ pts |

```
            beta = 0,50                 beta = 1,12
 RP = 15%  ████████████████████ 21,86%   ████████████████████████ 24,51%
 RP =  4%  ██████████ 10,86%             █████████████ 13,51%
                  └── +11 pts ──┘                └── +11 pts ──┘
```

---

## Errores comunes

| Error | Lo correcto |
|---|---|
| $\beta \times RP$ | $RP$ se suma solo. |
| $505$ pb como $50{,}5\%$ o como $0{,}505$. | $5{,}05\%$, o $0{,}0505$ en decimal. |
| Usar un valor viejo del EMBI+. | Actualizarlo el día del cálculo. |

---

## Autoevaluación

1. Con los datos base ($r_f = 4{,}72\%$, $E(r_m) = 9\%$, $\beta = 1{,}12$), ¿cuánto
   da $E(r_i)$ sin riesgo país? ¿Cuánto bajó respecto al caso con 505 pb?
   > [!question]- Respuesta
   > $E(r_i) = 9{,}51\%$. Bajó **exactamente $5{,}05$ puntos**, el valor del RP.

2. El riesgo país pasa de 490 a 1.490 pb. ¿Cuánto sube la tasa exigida de una
   empresa con $\beta = 0{,}8$? ¿Y con $\beta = 1{,}5$?
   > [!question]- Respuesta
   > **10 puntos en ambos casos.** $1.000$ pb $= 10\%$, y el RP no se multiplica
   > por beta.

---

## Relacionado

- [[capm]]: la fórmula completa.
- [[beta]]: lo que sí multiplica.
- [[tasa-libre-de-riesgo]]: el otro dato diario.
- [[ejercicios-wacc-capm]]: ejercicios 2 y 3 de CAPM.
