---
subject: modelado-y-simulacion
topic: Simulador de Newton-Cotes (herramienta de cátedra)
sources:
  - newton-cotes-simulador.html
updated: 2026-08-28
---

# Simulador de Newton-Cotes

Herramienta web de la cátedra (Ing. Omar Cáceres, UADE), archivo HTML
autocontenido en `raw/clase 4/newton-cotes-simulador.html`. Es el tercero de la
serie, después del [[simulador-de-raices]] y el
[[simulador-de-reconstruccion-de-funciones]], y cubre la
[[integracion-numerica]] determinista.

Está organizado en cinco secciones: teoría, simulador, ejemplos clásicos,
aplicaciones reales y un resumen en audio (síntesis de voz del navegador).

## Qué permite hacer

- Escribir una función arbitraria $f(x)$ (sintaxis `^ + - * /`, funciones
  `sin cos tan exp log sqrt`, constante `pi`), definir los límites $a$ y $b$ y
  la cantidad de subintervalos $n$.
- Elegir entre **ocho métodos**, con validación automática de la restricción
  sobre $n$:

| Método | Restricción | Página |
|---|---|---|
| Trapecio simple | $n = 1$ | [[regla-del-trapecio]] |
| Trapecio compuesto | $n \ge 1$ | [[regla-del-trapecio]] |
| Simpson 1/3 simple | $n = 2$ | [[regla-de-simpson-1-3]] |
| Simpson 1/3 compuesto | $n$ par | [[regla-de-simpson-1-3]] |
| Simpson 3/8 simple | $n = 3$ | [[regla-de-simpson-3-8]] |
| Simpson 3/8 compuesto | $n$ múltiplo de 3 | [[regla-de-simpson-3-8]] |
| Boole simple | $n = 4$ | [[formulas-de-newton-cotes]] |
| Gauss-Legendre | 1 a 5 puntos | [[cuadratura-de-gauss-legendre]] |

- Ver la **integral aproximada**, una **referencia numérica** de alta precisión
  y el **error absoluto** resultante (ver [[analisis-de-error]]).
- Ver la **tabla iterativa** nodo a nodo: para cada $i$, el valor $x_i$, el
  valor $f(x_i)$, el coeficiente $c_i$ que le corresponde y el término
  $c_i f(x_i)$ — muy útil para reproducir el cálculo a mano en un parcial.
- Ver la **fórmula LaTeX aplicada** y su expresión de error para el método
  activo.
- Visualizar los **paneles polinomiales** sobre el gráfico (paneles pares e
  impares en distinto color) y reproducir una **animación** de su construcción.
- Comparar **todos los métodos a la vez** en una tabla y en un gráfico de error
  en **escala logarítmica**.

## Ejemplos clásicos precargados

Casos de la bibliografía estándar (Chapra & Canale, entre otros):

| Función | Intervalo | Método sugerido | Valor exacto |
|---|---|---|---|
| $0.2 + 25x - 200x^2 + 675x^3 - 900x^4 + 400x^5$ | $[0,\ 0.8]$ | Simpson 1/3 comp., $n=4$ | $1.640533$ |
| $\sin x$ | $[0,\ \pi]$ | Simpson 1/3 comp., $n=6$ | $2$ |
| $e^x$ | $[0,\ 1]$ | Trapecio comp., $n=6$ | $e-1 \approx 1.718282$ |
| $1/x$ | $[1,\ 3]$ | Simpson 3/8 comp., $n=6$ | $\ln 3 \approx 1.098612$ |
| $x^2 - 2x + 2$ | $[0,\ 4]$ | Simpson 1/3 simple, $n=2$ | $40/3 \approx 13.3333$ |
| $\sqrt{x}$ | $[1,\ 4]$ | Boole simple, $n=4$ | $14/3 \approx 4.66667$ |
| $e^x$ | $[0,\ 1]$ | Gauss-Legendre, 3 nodos | $e-1 \approx 1.718282$ |

El polinomio de 5º grado de Chapra es el ejemplo canónico para verificar
órdenes de error, y la parábola $x^2-2x+2$ sirve para comprobar que Simpson 1/3
es **exacta** para polinomios de grado $\le 3$.

## Aplicaciones reales que documenta

El simulador incluye una sección de casos de uso fuera del aula, cada uno
cargable con un clic. Todos comparten el mismo patrón: hay que integrar una
señal o una densidad que no tiene primitiva elemental, o que solo se conoce
por muestras.

**Robótica**

- **Odometría** — distancia recorrida $\int v(t)\,dt$ a partir de la velocidad
  medida por encoders de rueda.
- **Dinámica de actuadores** — trabajo mecánico $W = \int \tau(\theta)\,d\theta$
  de un eslabón de un brazo robótico (gravedad + fricción de Coulomb +
  fricción viscosa).
- **Autonomía** — energía consumida $E = \int P(t)\,dt$ en una misión de dron,
  calculada en el microcontrolador con trapecio compuesto por su bajo costo.

**Informática y datos**

- **AUC-ROC** — la métrica estándar de clasificadores binarios es literalmente
  el área bajo la curva TPR vs. FPR; scikit-learn la calcula con trapecio
  compuesto sobre los puntos discretos.
- **Probabilidad acumulada normal** — $P(-2 < Z < 2)$ exige integrar la
  densidad gaussiana, cuya primitiva (función error) no es elemental.
- **Profiling energético** — consumo acumulado de CPU integrando la curva de
  uso muestreada.

**Inteligencia artificial**

- **Evidencia bayesiana** — $P(D) = \int P(D|\theta)P(\theta)\,d\theta$ normaliza
  la posterior; se aproxima con cuadratura en baja dimensión y con Monte Carlo
  en alta dimensión (ver [[integracion-numerica]]).
- **Aprendizaje por refuerzo** — el retorno esperado de una política en un
  espacio de estados continuo, $V = \int V(s)\,p(s)\,ds$.

## Ejemplo motivador de la teoría

La sección teórica abre con un caso de **ingeniería estructural**: una viga con
carga distribuida $w(x)$ que combina un seno, una exponencial y una raíz en el
denominador. Al no tener primitiva elemental, el momento flector $M(x)$ y la
deflexión de la viga solo pueden evaluarse por cuadratura numérica.

Relacionado: [[formulas-de-newton-cotes]], [[integracion-numerica]],
[[simulador-de-raices]], [[simulador-de-reconstruccion-de-funciones]].
