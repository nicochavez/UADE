---
subject: modelado-y-simulacion
topic: Calendario de exámenes y ejercicios de práctica
sources:
  - Viernes TN 2026-II.pdf
  - 01C Búsqueda_Binaria_de_Raíces.pdf
  - 01D Lectura 2.pdf
  - simulador_metodos_numericos-6.html
  - 05C Lectura 1 Erraor_acotado_vs_confianza_probabilística.pdf
  - 06A Metodos_de_Runge_Kutta.pdf
updated: 2026-09-18
---

# Parciales y práctica

## Calendario de evaluación

| Instancia | Fecha | Clase |
|-----------|-------|-------|
| 1° Parcial | 18/09/2026 | 7 |
| 2° Parcial | 13/11/2026 | 15 |
| Recuperatorio / Final adelantado | 27/11/2026 | 17 |
| Final regular | 11/12/2026 | — |

Detalle completo del cronograma en [[programa-del-curso]].

## Temario aproximado por parcial

- **1° Parcial (clases 1-6):** fundamentos ([[iteracion-y-convergencia]],
  [[analisis-de-error]], [[conjuntos-compactos]], [[condicion-de-lipschitz]]),
  [[busqueda-de-raices]] ([[metodo-de-biseccion]], [[metodo-de-newton-raphson]],
  [[metodo-del-punto-fijo]], [[metodo-de-aitken]]),
  interpolación/derivación, [[integracion-numerica]] (incluido
  [[metodo-de-monte-carlo|Monte Carlo]] e [[intervalo-de-confianza|intervalos de confianza]]) y
  [[ecuaciones-diferenciales-ordinarias]] ([[metodo-de-euler]], [[metodo-de-heun]],
  [[metodo-de-runge-kutta-4]]).
- **2° Parcial (clases 8-13):** [[sistemas-dinamicos]], [[bifurcaciones]],
  sistemas lineales 2D, sistemas no lineales y [[modelos-aplicados]].

## Ejercicios de práctica

### Búsqueda binaria de raíces (`01C`)

Usar el [[teorema-de-bolzano]] para determinar si existe una raíz en el intervalo
dado y, en caso afirmativo, aplicar [[metodo-de-biseccion|bisección]] (manual o
con código) para aproximarla:

1. $f(x) = x^3 - x - 2$, en $[1, 2]$
2. $f(x) = x^2 - 3$, en $[1, 2]$
3. $f(x) = e^x - 2 - x$, en $[1, 2]$
4. $f(x) = \cos(x) + 1 - x$, en $[1, 2]$
5. $f(x) = \ln(x) + x - 5$, en $[3, 4]$
6. $f(x) = x - \cos(x)$, en $[0, 1]$

### Desafío de bisección (`01D Lectura 2`)

Encontrar la raíz de $f(x) = x^3 + 4x^2 - 10$ en $[1, 2]$:

1. Usar una tolerancia $\varepsilon = 10^{-5}$.
2. Calcular *teóricamente* cuántas iteraciones $n$ se necesitan usando la fórmula
   de la cota de error $|p_n - p| \le \dfrac{b - a}{2^n}$ (ver [[analisis-de-error]]).

### Ejercicios de la guía cargados en el simulador (`simulador_metodos_numericos-6.html`)

El [[simulador-de-raices]] trae precargados estos ejercicios de la guía
*Fundamentos de Modelado y Simulación* de la cátedra. Sirven como banco de
práctica aunque no se use la herramienta.

**Búsqueda binaria** — [[metodo-de-biseccion]], con intervalo $[a, b]$:

| Ej. | $f(x)$ | Intervalo |
|-----|--------|-----------|
| 2 | $3(x+1)(x-\tfrac{1}{2})(x-1)$ | $[-1.25, 2.5]$ |
| 3a | $\sqrt{x} - \cos(x)$ | $[0, 1]$ |
| 3e | $x\cos(x) - 2x^2 + 3x - 1$ | $[0.2, 0.3]$ |
| 4a | $x^4 - 2x^3 - 4x^2 + 4x + 4$ | $[-2, -1]$ |
| 4c | $x^4 - 2x^3 - 4x^2 + 4x + 4$ | $[2, 3]$ |

**Punto fijo** — [[metodo-del-punto-fijo]]; nótese la reformulación de $f(x) = 0$
como $x = g(x)$:

| Ej. | $f(x)$ original | $g(x)$ a iterar | $x_0$ |
|-----|-----------------|-----------------|------|
| 1 | $2e^{x^2} - 5x$ | $\tfrac{2}{5}e^{x^2}$ | $0$ |
| 2 | $\cos(x)$ | $\cos(x)$ | $1$ |
| 3 | $e^{-x} - x$ | $e^{-x}$ | $0$ |
| 4 | $x^3 - x - 1$ | $\sqrt[3]{x + 1}$ | $1$ |
| 5 | — | $\pi + 0.5\sin(x/2)$ | $0$ |

**Newton-Raphson** — [[metodo-de-newton-raphson]]:

| Ej. | $f(x)$ | $x_0$ | Detalle |
|-----|--------|------|---------|
| 1 | $(x - 1)^2$ | $0$ | raíz doble: la convergencia deja de ser cuadrática |
| 2 | $x^3 - 2x - 5$ | $1.5$ | |
| 3 | $x^5 - x - 1$ | $1$ | |
| 5 | $e^x + x^2 - 4$ | $0.5$ | |
| 7 | $\ln(x) - 1$ | $2$ | la raíz es $e$ |
| 9 | $x^3 - 2x + 1$ | $-1.5$ | punto inicial negativo |

**Aitken ($\Delta^2$)** — [[metodo-de-aitken]], acelerando la iteración $x = g(x)$:

| Ej. | $f(x)$ original | $g(x)$ a iterar | $x_0$ |
|-----|-----------------|-----------------|------|
| 1 | $\tfrac{\pi}{2}x^2 - x - 2$ | $\sqrt{\tfrac{2}{\pi}(x + 2)}$ | $1.4$ |
| 2 | $\cos(x) - x$ | $\cos(x)$ | $0.5$ |
| 3 | — | $\sqrt[3]{3x^2 - 4x + 1}$ | $0.3$ |
| 6 | — | $\ln(x + 1)$ | $0.5$ |
| 7 | — | $1 - x^3$ | $0.5$ |
| 9 | — | $(\sin(x) + 5)/x^2$ | $2$ |

### Integral con tolerancia: determinista vs. Monte Carlo (`05C`)

Calcular $\int_0^4 x e^{-x}\,dx$ (exacto: $1 - 5e^{-4} \approx 0.908422$):

1. Con rectángulos, trapecios y Simpson: usar la cota de error de cada método
   para despejar el $h$ máximo que garantiza $|\text{Error}| \le \tau$ (ver
   [[error-de-truncamiento-y-redondeo]]).
2. Repetir reteniendo solo **3 cifras decimales** en los valores de $f$. ¿Se
   sigue pudiendo alcanzar la tolerancia? ¿Por qué existe un $h$ óptimo?
3. Estimarla por [[integracion-por-monte-carlo|Monte Carlo]] (aciertos en la caja
   $[0,4]\times[0,0.6]$ o valor medio) y construir un
   [[intervalo-de-confianza]] al 95%. ¿Cuántos puntos hacen falta para que el
   semiancho sea menor que $\tau$?

### EDO: Euler vs. Heun vs. RK4 (`06A`)

Resolver $y' = x + y$, $y(0) = 1$ en $[0, 1]$ con $h = 0.1$ usando
[[metodo-de-euler]], [[metodo-de-heun]] y [[metodo-de-runge-kutta-4]], y
comparar con la solución exacta $y = 2e^x - x - 1$. Los valores de referencia
están en [[ecuaciones-diferenciales-ordinarias]].

### Exploración con IA sugerida (`01D Lectura 2`)

- Comparar la convergencia lineal de bisección con la cuadrática de
  Newton-Raphson y generar un gráfico comparativo.
- Generar un script en Python que visualice las primeras 5 iteraciones de
  bisección para $f(x) = e^x - 2$ en $[0, 1]$.
- Explicar en qué escenarios bisección sería preferible al método de la secante,
  y viceversa.
