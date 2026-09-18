---
subject: modelado-y-simulacion
topic: Ecuaciones diferenciales ordinarias (EDOs)
sources:
  - 01A Introducción Modelado y Simulación.pdf
  - 01D Lectura 1.pdf
  - Viernes TN 2026-II.pdf
  - 06A Metodos_de_Runge_Kutta.pdf
updated: 2026-09-18
---

# Ecuaciones diferenciales ordinarias (EDOs)

Métodos para resolver $\dfrac{dy}{dx} = f(x, y)$: predecir el estado futuro de
un sistema a partir de su estado actual y sus reglas de cambio. Es el
**corazón del modelado dinámico**: permite simular desde la órbita de un
planeta hasta la propagación de una epidemia, y es el motor interno de la
simulación (Clase 6).

## El problema de valor inicial (problema de Cauchy)

Una EDO describe un sistema en cambio, pero su solución general (por ejemplo
$y = F(x) + C$) es una **familia infinita de curvas**, una por cada valor de
$C$. Para anclar la solución a la realidad se fija un punto de partida
conocido:

$$
y' = f(x, y), \qquad y(x_0) = y_0
$$

Esto selecciona la **única** curva de la familia que pasa por $(x_0, y_0)$.
El desafío numérico es trazar esa curva cuando no hay solución analítica.

## La idea fundamental: un paso a la vez

Si se conoce un punto de la curva y la pendiente ahí, se puede predecir el
siguiente punto avanzando una distancia $h$ a lo largo de esa pendiente:

$$
y_{i+1} = y_i + \phi\, h
$$

donde $y_{i+1}$ es el valor predicho, $y_i$ el valor conocido, $h$ el tamaño
del paso y $\phi$ la pendiente estimada. **Los métodos de Runge-Kutta se
diferencian únicamente en cómo calculan $\phi$:**

| Método | Pendiente $\phi$ | Evaluaciones de $f$ por paso | Orden global* |
|--------|------------------|------------------------------|---------------|
| [[metodo-de-euler]] | una sola, al inicio del intervalo | 1 | $O(h)$ |
| [[metodo-de-heun]] (Euler mejorado) | promedio de inicio y final (predictor-corrector) | 2 | $O(h^2)$ |
| [[metodo-de-runge-kutta-4]] | promedio ponderado de 4 pendientes | 4 | $O(h^4)$ |

\*Los órdenes son el resultado teórico estándar; las diapositivas de `06A`
los muestran empíricamente pero no los enuncian.

**Lección de la clase:** una estimación más inteligente de la pendiente
dentro de cada paso lleva a una aproximación global mucho mejor.

## Comparación numérica: $y' = x + y$, $y(0) = 1$, $h = 0.1$

Solución exacta: $y = 2e^x - x - 1$. Tabla de `06A` (verificada):

| $n$ | $x$ | Exacta | Euler | Heun (Euler M) | RK4 |
|-----|-----|--------|-------|----------------|-----|
| 0 | 0.0 | 1.000000 | 1.000000 | 1.000000 | 1.000000 |
| 1 | 0.1 | 1.110342 | 1.100000 | 1.110000 | 1.110342 |
| 2 | 0.2 | 1.242806 | 1.220000 | 1.242050 | 1.242805 |
| 3 | 0.3 | 1.399718 | 1.362000 | 1.398465 | 1.399717 |
| 4 | 0.4 | 1.583649 | 1.528200 | 1.581804 | 1.583649 |
| 5 | 0.5 | 1.797443 | 1.721020 | 1.794894 | 1.797441 |
| 6 | 0.6 | 2.044238 | 1.943122 | 2.040857 | 2.044236 |
| 7 | 0.7 | 2.327505 | 2.197434 | 2.323150 | 2.327503 |
| 8 | 0.8 | 2.651082 | 2.487178 | 2.645561 | 2.651079 |
| 9 | 0.9 | 3.019206 | 2.815896 | 3.012249 | 3.019203 |
| 10 | 1.0 | 3.436564 | 3.187485 | 3.428162 | 3.436559 |

Errores en $x = 1$: Euler $\approx 0.249$, Heun $\approx 0.0084$, RK4
$\approx 4.2 \times 10^{-6}$.

> El gráfico de la diapositiva 13 de `06A` exagera la separación (muestra a
> Euler cerca de 1.9 en $x = 1$). Para cualquier dato numérico, usar la tabla.

## Precisión vs. costo

La precisión no es gratis: RK4 hace 4 evaluaciones de $f$ por paso. Aun así,
al comparar el error contra el **trabajo computacional total**, los métodos de
orden superior alcanzan un error objetivo con muchos menos pasos, y por eso
suelen resultar **más baratos** en total.

## Otros temas del programa

El cronograma también menciona los métodos de Taylor, los órdenes de
aproximación local y global, y esquemas en diferencias para ecuaciones en
derivadas parciales con valores en la frontera (`Viernes TN 2026-II.pdf`).

## Conexión con dinámica

Resolver EDOs numéricamente permite **simular** la evolución de un sistema; el
análisis cualitativo de esas soluciones es el objeto de los
[[sistemas-dinamicos]].

Relacionado: [[integracion-numerica]], [[modelos-aplicados]], [[metodos-numericos]].
