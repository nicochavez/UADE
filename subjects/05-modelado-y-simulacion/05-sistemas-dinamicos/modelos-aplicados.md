---
subject: modelado-y-simulacion
topic: Modelos aplicados (Lotka-Volterra, Lanchester, SIR, Lorenz)
sources:
  - 01A Introducción Modelado y Simulación.pdf
  - 01D Lectura 1.pdf
  - Viernes TN 2026-II.pdf
updated: 2026-08-07
---

# Modelos aplicados

El poder predictivo de los [[sistemas-dinamicos]] se extiende a la biología, la
física y las ciencias sociales. Se ven en la Clase 13 ("modelos interpretados").

## Depredador-presa (Lotka-Volterra)

Describe la relación cíclica entre presas ($x$) y depredadores ($y$):

$$
\begin{aligned}
\dot{x} &= ax - bxy \\
\dot{y} &= cxy - dy
\end{aligned}
$$

Más presas alimentan a más depredadores; más depredadores reducen las presas;
menos presas llevan a la inanición de los depredadores, permitiendo que las
presas se recuperen. El resultado es una oscilación perpetua y desfasada (el
retrato de fase muestra órbitas cerradas).

## Modelos de combate (Lanchester)

Modelan el desgaste de fuerzas en combate (ej. $dx/dt = -ay$). Permiten analizar
cómo las estrategias y refuerzos determinan el resultado de un conflicto.

## Epidemiología (SIR)

Divide la población en Susceptibles (S), Infectados (I) y Recuperados (R). Revela
un **umbral epidemiológico** que determina si una enfermedad se convierte en
epidemia.

## Romance (modelo de Strogatz)

Captura las emociones oscilantes de una relación amorosa (Romeo y Julieta):
$\dfrac{d(\text{Romeo})}{dt} = a \cdot \text{Romeo} + b \cdot \text{Julieta}$.

## Caos: el sistema de Lorenz y el efecto mariposa

El **sistema de Lorenz** (modelo simplificado de convección atmosférica) reveló
que algunos sistemas deterministas son fundamentalmente impredecibles:

$$
\begin{aligned}
\dot{x} &= \sigma(y - x) \\
\dot{y} &= x(\rho - z) - y \\
\dot{z} &= xy - \beta z
\end{aligned}
$$

Diferencias infinitesimales en las condiciones iniciales crecen exponencialmente,
llevando a resultados completamente distintos. Esa es la esencia del **caos**
(efecto mariposa); su atractor tiene la forma característica de mariposa.

Relacionado: [[ecuaciones-diferenciales-ordinarias]], [[bifurcaciones]].
