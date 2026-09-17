---
subject: modelado-y-simulacion
topic: Sistemas dinámicos, espacio de fases y estabilidad
sources:
  - 01A Introducción Modelado y Simulación.pdf
  - 01D Lectura 1.pdf
  - 01D Lectura 3.pdf
  - Viernes TN 2026-II.pdf
updated: 2026-08-07
---

# Sistemas dinámicos

Un **sistema dinámico** se define por su **estado** (un punto en el espacio de
fases) y una **regla** (una [[ecuaciones-diferenciales-ordinarias|ecuación
diferencial]]) que dicta cómo se mueve ese punto. Pasamos de *simular* el cambio
a *entender* su comportamiento cualitativo a largo plazo.

## Retrato de fase

El **retrato de fase** es el mapa definitivo del comportamiento de un sistema:
en lugar de mostrar una sola solución, visualiza *todas* las trayectorias
posibles a la vez, revelando la "personalidad" dinámica completa del sistema.

## Puntos de equilibrio y estabilidad

Los sistemas son atraídos, repelidos o circulan alrededor de **puntos de
equilibrio** (donde $\dot{x} = 0$, $\dot{y} = 0$). La naturaleza de cada punto la determinan
los **autovalores** de la matriz Jacobiana:

| Tipo | Autovalores | Comportamiento |
|------|-------------|----------------|
| Nodo estable (atractor) | Reales negativos ($\lambda_1 < \lambda_2 < 0$) | Todas las trayectorias convergen |
| Nodo inestable (repulsor) | Reales positivos | Todas las trayectorias escapan |
| Punto de silla | Reales de signo opuesto ($\lambda_1 < 0 < \lambda_2$) | Atrae en una dirección, repele en otra |
| Centro / espiral | Complejos | Oscilación (espiral estable si $\text{Re}(\lambda) < 0$, inestable si $> 0$, centro si $= 0$) |

## Sistemas lineales, no lineales y linealización

- **Sistemas lineales 2D** (Clases 10-11): nodos, focos, sillas y centros son los
  bloques de construcción; se estudian nulclinas, espectros y autovectores.
- **Sistemas no lineales** (Clase 12): se usa **linealización** (Teorema de
  Hartman-Grobman) con la matriz Jacobiana local para entender el comportamiento
  cerca de los equilibrios; aquí emergen ciclos límite, oscilaciones
  auto-sostenidas y caos.

## Rol de la compacidad

Un [[conjuntos-compactos|conjunto compacto]] invariante (una vez que una
trayectoria entra, nunca sale) garantiza que las trayectorias no explotan y que
existen **atractores** (conjuntos $\omega$-límite no vacíos). Ejemplo: para $\dot{x} = -x + x^3$,
el intervalo $K = [-1, 1]$ es compacto e invariante porque en la frontera el
campo apunta hacia adentro ($\dot{x} = 0$ en $x = \pm 1$).

Relacionado: [[bifurcaciones]], [[modelos-aplicados]], [[ecuaciones-diferenciales-ordinarias]].
