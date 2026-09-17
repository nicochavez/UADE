---
subject: evaluacion-de-proyectos
topic: ROI y ROA (rendimiento contable)
sources:
  - EPT Clase 2_Matematica Financiera - Parte I.pdf
  - EPT_Clase3y4_MatematicaFinanciera_II_Ejercicios_Soluciones.xlsx
updated: 2026-09-14
tags:
  - evaluacion-de-proyectos/tecnicas
  - indicador
  - enfoque-contable
  - parcial-1
---

# ROI y ROA

> [!abstract] En una frase
> El ROI dice **cuánto ganaste en total** respecto a lo que pusiste, pero no
> **cuándo** lo ganaste. Es rápido y engañoso.

**Prerrequisitos:** [[flujo-de-fondos]], de donde sale la suma de flujos.
**Sigue con:** [[payback]], el otro indicador contable.

---

## Intuición

> [!example] Analogía: medir un viaje solo por los kilómetros
> Dos autos recorren 500 km. Uno tardó 5 horas y el otro 5 días. Si solo mirás
> los kilómetros, "rindieron igual". El ROI hace eso: mira el **total** y se olvida
> del **tiempo**.

---

## ROI (Return on Investment)

Mide el rendimiento obtenido en relación con el capital invertido originalmente.

$$
ROI = \frac{\text{Resultado neto}}{C_0}
= \frac{\sum FF_t - C_0}{C_0}
= \frac{\sum FF_t}{C_0} - 1
$$

| Parte          | Significado                                              |
| -------------- | -------------------------------------------------------- |
| $\sum FF_t$    | Suma **nominal** de los flujos positivos (sin descontar) |
| $C_0$          | Inversión inicial                                        |
| Resultado neto | Lo que sobra después de recuperar la inversión           |

Las tres formas son equivalentes. La primera aparece en la teoría; la tercera es
la de la planilla de Excel (`=SUMA(flujos)/Inversión-1`).

**Ejemplo:** inversión de $\$10.000$ con flujo neto acumulado de $\$5.000$:
$ROI = 5.000/10.000 = 50\%$.

## ROA (Return on Assets)

Mide la eficacia de los **activos totales** de la empresa para generar
utilidades.

$$
ROA = \frac{\text{Utilidad}}{\text{Activo total}}
$$

**Ejemplo ilustrativo:** una empresa con activos por $\$2.000.000$ que gana
$\$200.000$ en el año tiene $ROA = 10\%$.

| | ROI | ROA |
|---|---|---|
| Qué mira | Un **proyecto** puntual | **Toda la empresa** |
| Numerador | Resultado neto del proyecto | Utilidad de la empresa |
| Denominador | Inversión inicial | Activo total |
| Considera el tiempo | ❌ | ❌ |

---

## La limitación central: el ROI no ve el calendario

```
Proyecto 1: invierto $10.000, recibo $15.000 en el AÑO 1   -> ROI 50%
Proyecto 2: invierto $10.000, recibo $15.000 en el AÑO 5   -> ROI 50%

ROI dice: son iguales.
VAN al 10%:  Proyecto 1 = +$3.636  (conviene)
             Proyecto 2 =   -$686  (NO conviene)
```

Mismo ROI, **decisión opuesta**. Esa es exactamente la limitación que resuelve el
[[valor-actual-neto]]. El ROI tampoco dice si la inflación afectó el resultado.

> [!danger] En el parcial
> En el Ejercicio 1 de Matemática Financiera II el ROI da $33{,}3\%$ (atractivo a
> primera vista) y sin embargo el proyecto **destruye valor** porque el VAN es
> negativo. Si te piden "concluir", nunca lo hagas solo con el ROI.

---

## Errores comunes

| Error | Lo correcto |
|---|---|
| Incluir la inversión (negativa) en $\sum FF_t$ y además restar $C_0$. | O sumás solo los flujos positivos y restás 1, o usás el resultado neto. No las dos cosas. |
| "ROI positivo, entonces conviene." | Solo dice que se recupera más de lo invertido en valores nominales. |
| Confundir ROI con ROA. | ROI es un proyecto; ROA, la empresa entera. |

---

## Autoevaluación

1. Inversión $\$25.000$; flujos $\$8.000$, $\$8.000$, $\$9.000$, $\$9.000$. ¿ROI?
   > [!question]- Respuesta
   > $\sum FF_t = 34.000$. $ROI = 34.000/25.000 - 1 = 36\%$.

2. Dos proyectos tienen el mismo ROI. ¿Qué información falta para decidir?
   > [!question]- Respuesta
   > **Cuándo** llegan los flujos y **a qué tasa** hay que descontarlos. Con eso se
   > calcula el VAN, que sí puede diferenciarlos.

---

## Relacionado

- [[payback]]: el otro indicador contable, con la misma debilidad.
- [[valor-actual-neto]]: corrige la limitación del ROI.
- [[tecnicas-de-evaluacion-de-proyectos]]: comparación de los cinco indicadores.
- [[flujo-de-fondos]]: la planilla de donde sale.
