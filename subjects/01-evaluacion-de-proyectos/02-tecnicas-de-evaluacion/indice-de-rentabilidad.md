---
subject: evaluacion-de-proyectos
topic: IR (Índice de Rentabilidad)
sources:
  - EPT Clase 2_Matematica Financiera - Parte I.pdf
  - EPT_Clase3y4_MatematicaFinanciera_II_Ejercicios_Soluciones.xlsx
updated: 2026-09-14
tags:
  - evaluacion-de-proyectos/tecnicas
  - indicador
  - enfoque-financiero
  - parcial-1
---

# IR (Índice de Rentabilidad)

> [!abstract] En una frase
> El IR responde **"¿cuánto valor crea el proyecto por cada peso invertido?"**.
> Es el VAN dividido la inversión.

**Prerrequisitos:** [[valor-actual-neto]], el numerador del IR.
**Sigue con:** [[tasa-interna-de-retorno]].

---

## El problema que resuelve

El VAN está en **pesos**, y eso favorece a los proyectos grandes. Un proyecto
enorme puede tener más VAN que uno chico solo por su tamaño, aunque use el dinero
de forma mucho menos eficiente. Para comparar proyectos de distinto tamaño hace
falta una medida **relativa**.

## Intuición

> [!example] Analogía: kilómetros totales vs. rendimiento por litro
> - El **VAN** es cuántos kilómetros recorriste en total.
> - El **IR** es cuántos kilómetros hiciste **por litro** de nafta.
>
> Un camión puede recorrer más kilómetros que un auto chico, pero si el
> combustible es limitado (**presupuesto limitado**), te importa el rendimiento
> por litro.

---

## Fórmula

$$
IR = \frac{VAN}{C_0}
$$

| Símbolo | Significado |
|---|---|
| $VAN$ | Valor actual neto del proyecto |
| $C_0$ | Inversión inicial (en valor absoluto) |

## Regla de decisión

Con la definición de la cátedra, el IR tiene el **mismo signo que el VAN**:

$$
IR > 0 \iff VAN > 0 \Rightarrow \text{conviene}
$$

> [!danger] Umbral 0, no 1
> En otra bibliografía el "índice de rentabilidad" se define como
> $\text{VP de los flujos} / C_0$, y ahí el umbral es $1$. **En esta materia se
> usa $VAN / C_0$, con umbral $0$.** Si en el parcial escribís "conviene porque
> $IR > 1$", está mal.

| Definición | Fórmula | Umbral | Ejemplo con $VAN = 1.372$ y $C_0 = 10.000$ |
|---|---|---|---|
| **Cátedra** | $VAN / C_0$ | $0$ | $0{,}137$, es decir $13{,}72\%$ |
| Otra bibliografía | $\text{VP flujos} / C_0$ | $1$ | $11.372/10.000 = 1{,}137$ |

Las dos dicen lo mismo; la segunda es simplemente la primera más 1.

---

## Ejemplos

| Caso | Inversión | VAN | IR | Lectura |
|---|---|---|---|---|
| Proyecto ejemplo del bloque | $\$10.000$ | $\$1.372$ | $13{,}72\%$ | Crea 14 centavos por peso |
| Ejercicio 3 de la práctica | $\$15.000$ | $\$3.333{,}97$ | $22{,}23\%$ | ✅ Conviene |
| Ejercicio 1 de la práctica | $\$18.000$ | $-\$1.167{,}94$ | $-6{,}49\%$ | ❌ Destruye valor |

## Para qué sirve además del signo

**Variación:** cuando hay que **elegir entre proyectos** con presupuesto limitado,
el IR ordena mejor que el VAN.

| | Proyecto A | Proyecto B |
|---|---|---|
| Inversión | $\$5.000$ | $\$50.000$ |
| VAN | $\$1.000$ | $\$1.200$ |
| IR | $20\%$ | $2{,}4\%$ |
| ¿Cuál tiene más VAN? | | ✅ |
| ¿Cuál usa mejor cada peso? | ✅ | |

B crea más valor en total, pero A es **ocho veces más eficiente**. Con
$\$50.000$ de presupuesto podrías hacer diez proyectos como A.

---

## Errores comunes

| Error | Lo correcto |
|---|---|
| Usar umbral 1. | Con la fórmula de la cátedra el umbral es **0**. |
| Dividir por la suma de flujos. | Se divide por la **inversión inicial**. |
| "IR y VAN pueden dar decisiones distintas para un proyecto." | Para aceptar o rechazar uno, siempre coinciden en signo. Solo difieren al **ordenar** varios. |

---

## Autoevaluación

1. Inversión $\$16.000$, $VAN = \$961{,}87$ al $13\%$. ¿IR y decisión?
   > [!question]- Respuesta
   > $IR = 961{,}87 / 16.000 = 6{,}01\%$. Positivo: **conviene**.

2. Un compañero dice "el IR dio $0{,}8$, entonces no conviene porque es menor que
   1". ¿Qué le respondés?
   > [!question]- Respuesta
   > Con la definición de la cátedra ($VAN/C_0$) el umbral es 0. $IR = 0{,}8$
   > significa $80\%$ de valor creado por peso invertido: **conviene mucho**.

---

## Relacionado

- [[valor-actual-neto]]: el numerador; misma regla de signo.
- [[tasa-interna-de-retorno]]: otra medida relativa, en forma de tasa.
- [[tecnicas-de-evaluacion-de-proyectos]]: cuándo usar cada indicador.
