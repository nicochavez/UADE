---
subject: modelado-y-simulacion
topic: Programa y cronograma del curso
sources:
  - Viernes TN 2026-II.pdf
  - 01D Lectura 1.pdf
updated: 2026-08-07
---

# Programa del curso

Datos administrativos de la materia (según `Viernes TN 2026-II.pdf`):

- **Código:** 3.1.025 — **Facultad:** FAIN — **Depto.:** DEBAS — **Horas:** 68
- **Docente:** Ing. Omar Cáceres (Adjunto)
- **Año/Cuatrimestre:** 2026, 2° cuatrimestre
- **Horario:** Viernes 18:45 a 22:15 hs.
- **Idioma del vault:** español

## Fechas clave de evaluación

- **1° Parcial:** 18/09/2026 (Clase 7)
- **2° Parcial:** 13/11/2026 (Clase 15)
- **Recuperatorio / Final adelantado:** 27/11/2026 (Clase 17)
- **Final regular:** 11/12/2026
- Nota: el 26/09 hay una clase remota sincrónica de 9 a 13 hs.

## Cronograma de clases

| Clase | Fecha | Tema principal |
|------|-------|----------------|
| 1 | 7/8 | Conceptos básicos: orden de aproximación, convergencia, errores, [[busqueda-de-raices]], [[condicion-de-lipschitz]], [[metodo-del-punto-fijo]], [[analisis-de-error]] |
| 2 | 14/8 | [[metodo-de-newton-raphson]], convergencia cuadrática, aceleración de Aitken |
| 3 | 21/8 | [[polinomio-de-lagrange]], [[diferencias-finitas]], pasos óptimos |
| 4 | 28/8 | [[integracion-numerica]]: rectángulos, trapecios, Simpson |
| 5 | 4/9 | Métodos Montecarlo para integración; intervalos de confianza |
| 6 | 11/9 | [[ecuaciones-diferenciales-ordinarias]]: Cauchy, Euler, Taylor, Runge-Kutta |
| 7 | 18/9 | **1° PARCIAL** |
| 8 | 25/9 | [[sistemas-dinamicos]]: equilibrios, espacio de estados, diagramas de fase |
| 9 | 2/10 | Escenarios y [[bifurcaciones]] |
| 10 | 9/10 | Sistemas lineales 1er orden; nodos, focos, sillas |
| 11 | 16/10 | Sistemas lineales no homogéneos |
| 12 | 23/10 | Sistemas no lineales; linealización con matriz Jacobiana |
| 13 | 30/10 | [[modelos-aplicados]]: combate, Volterra, competencia |
| 14 | 6/11 | Clase de ejercicios |
| 15 | 13/11 | **2° PARCIAL** |
| 16 | 20/11 | Clase integradora |
| 17 | 27/11 | Recuperatorio / Final adelantado |
| 18 | 4/12 | Clase integradora |

## Estructura conceptual del curso

El curso (según el mapa de `01D Lectura 1.pdf`) se organiza en 8 bloques que van
"de la aproximación estática a la predicción dinámica":

1. [[busqueda-de-raices]] — resolver $f(x)=0$
2. [[interpolacion-polinomica]] ([[polinomio-de-lagrange]]) y [[diferencias-finitas|derivación numérica]]
3. [[integracion-numerica]]
4. [[ecuaciones-diferenciales-ordinarias]] (motor de la simulación)
5. Equilibrio y [[bifurcaciones]] en 1D
6. [[sistemas-dinamicos]] lineales 2D
7. Sistemas no lineales (linealización)
8. [[modelos-aplicados]] (depredador-presa, combate, epidemiología)

## Bibliografía de referencia

- *Análisis Numérico* — R. L. Burden y J. D. Faires (referencia estándar).
- *Numerical Recipes* — W. H. Press et al. (enfoque práctico de implementación).
- Librerías: `SciPy` (Python), `Numerical.js` (JavaScript).

> Los actos de deshonestidad académica o indisciplina se sancionan según el
> régimen disciplinario correspondiente.
