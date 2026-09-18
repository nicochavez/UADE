---
subject: modelado-y-simulacion
topic: Método de Monte Carlo
sources:
  - 05A Introducción al metodo de Monte Carlo.pdf
  - 05B Repaso Monte_Carlo.pdf
  - 05C Lectura 1 Erraor_acotado_vs_confianza_probabilística.pdf
updated: 2026-09-18
---

# Método de Monte Carlo

Técnica que usa **muestreo aleatorio y probabilidad** para aproximar
numéricamente problemas que son demasiado complejos (o imposibles) de resolver
de forma analítica. La paradoja aparente — ¿cómo puede el azar dar respuestas
precisas? — se resuelve con la [[ley-de-los-grandes-numeros]]: el azar, en
grandes cantidades, se vuelve ordenado.

El nombre viene del casino de Monte Carlo, por el papel central que juega el
azar en el método.

## La receta de 4 pasos

Todo Monte Carlo sigue la misma estructura (`05A`, `05B`):

1. **Definir el dominio:** el espacio de posibles valores del problema
   (ej.: el cuadrado $[-1,1] \times [-1,1]$).
2. **Generar muestras aleatorias:** muchas entradas uniformes dentro de ese
   dominio (ej.: puntos $(x, y)$). Ver [[generacion-de-numeros-aleatorios]].
3. **Evaluar:** aplicar la función del problema, o una condición de "éxito",
   a cada muestra (ej.: ¿$x^2 + y^2 \le 1$?).
4. **Calcular la estimación:** agregar los resultados (promedio o proporción
   de éxitos) para aproximar la solución.

El ejemplo canónico es la [[estimacion-de-pi-por-monte-carlo]]; la aplicación
principal en el curso es la [[integracion-por-monte-carlo]].

## Características

- **Basado en simulación:** estima resultados repitiendo miles o millones de
  experimentos aleatorios.
- **Poder para lo complejo:** brilla donde no hay fórmula cerrada y en
  **alta dimensión**, donde los métodos de malla sufren la "maldición de la
  dimensionalidad".
- **Precisión medible:** el resultado no es un número exacto sino una
  estimación con un [[intervalo-de-confianza]]. La precisión mejora
  aumentando $n$, a razón de $1/\sqrt{n}$ (ver [[teorema-central-del-limite]]).
- **Multidisciplinario:** física (de partículas), finanzas cuantitativas,
  ingeniería, inteligencia artificial, renderizado de gráficos.

## Determinista vs. probabilístico

Monte Carlo es una filosofía de cálculo distinta a la de las
[[formulas-de-newton-cotes]]: en vez de una cota superior del error, ofrece
una **probabilidad** de que el valor verdadero esté en un rango. La
comparación completa está en [[error-acotado-vs-confianza-probabilistica]].

Relacionado: [[integracion-numerica]], [[metodos-numericos]].
