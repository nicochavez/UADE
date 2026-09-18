---
subject: modelado-y-simulacion
topic: Método de Runge-Kutta de 4° orden (RK4)
sources:
  - 06A Metodos_de_Runge_Kutta.pdf
updated: 2026-09-18
---

# Runge-Kutta de 4° orden (RK4)

"La obra maestra": lleva la idea de **muestrear pendientes** a un nivel
superior. En vez de usar solo el punto inicial y el final (como el
[[metodo-de-heun]]), calcula **cuatro pendientes** en ubicaciones estratégicas
del intervalo y las combina en un **promedio ponderado**. Es el estándar de la
industria por su equilibrio entre precisión y costo.

## Las fórmulas

**Paso 1: calcular las pendientes**

$$
\begin{aligned}
k_1 &= f(x_n,\ y_n) \\
k_2 &= f\!\left(x_n + \tfrac{1}{2}h,\ y_n + \tfrac{1}{2}k_1 h\right) \\
k_3 &= f\!\left(x_n + \tfrac{1}{2}h,\ y_n + \tfrac{1}{2}k_2 h\right) \\
k_4 &= f\!\left(x_n + h,\ y_n + k_3 h\right)
\end{aligned}
$$

**Paso 2: avanzar**

$$
y_{n+1} = y_n + \frac{h}{6}\left(k_1 + 2k_2 + 2k_3 + k_4\right)
$$

## Qué representa cada pendiente

| $k$ | Dónde se evalúa | Significado |
|-----|-----------------|-------------|
| $k_1$ | $(x_i, y_i)$ | pendiente al **inicio** (idéntica a la de Euler) |
| $k_2$ | punto medio, usando $k_1$ | **primera** estimación de la pendiente en el punto medio |
| $k_3$ | punto medio, usando $k_2$ | **segunda** estimación, más refinada, en el mismo punto medio |
| $k_4$ | $x_{i+1}$, usando $k_3$ | pendiente al **final** del intervalo |

La pendiente final es
$\phi = \dfrac{k_1 + 2k_2 + 2k_3 + k_4}{6}$. Los pesos $1, 2, 2, 1$ dan **más
peso a las estimaciones del punto medio**, igual que la
[[regla-de-simpson-1-3]] con sus pesos $1, 4, 1$. De hecho, si $f$ depende
solo de $x$, RK4 se reduce exactamente a Simpson 1/3 sobre $[x_n, x_{n+1}]$.

## Precisión

Ejemplo $y' = x + y$, $y(0) = 1$, $h = 0.1$ (`06A`): RK4 coincide con la
solución exacta hasta la **quinta o sexta cifra decimal** en todo $[0, 1]$. En
$x = 1$ da $3.436559$ contra el exacto $3.436564$, con un error de
$\approx 4 \times 10^{-6}$, unas **60 000 veces menor** que el de Euler.

Dato estándar (no figura en las diapositivas): error local $O(h^5)$ y global
$O(h^4)$. Al dividir $h$ a la mitad, el error baja $\approx 16$ veces.

## Costo vs. precisión

RK4 cuesta **4 evaluaciones** de $f$ por paso (Euler, 1; Heun, 2). Pero al
comparar el **error contra el trabajo computacional total**, los métodos de
orden superior suelen ser **más eficientes**: alcanzan un error objetivo con
muchos menos pasos. El gráfico de `06A` (error relativo porcentual vs.
trabajo) muestra que para errores de $\sim 10^{-6}$, RK4 (y Butcher, de orden
5) requiere mucho menos trabajo que Euler, Heun o RK-3.

## Implementación (Python, esquema propio)

```python
def rk4(f, x0, y0, h, n):
    x, y = x0, y0
    for _ in range(n):
        k1 = f(x, y)
        k2 = f(x + h/2, y + h/2 * k1)
        k3 = f(x + h/2, y + h/2 * k2)
        k4 = f(x + h, y + h * k3)
        y = y + h/6 * (k1 + 2*k2 + 2*k3 + k4)
        x = x + h
    return y
```

Relacionado: [[ecuaciones-diferenciales-ordinarias]], [[metodo-de-euler]],
[[sistemas-dinamicos]], [[modelos-aplicados]].
