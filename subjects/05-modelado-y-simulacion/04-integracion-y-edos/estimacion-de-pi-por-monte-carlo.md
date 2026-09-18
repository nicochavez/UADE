---
subject: modelado-y-simulacion
topic: Estimación de π por Monte Carlo
sources:
  - 05A Introducción al metodo de Monte Carlo.pdf
  - 05B Repaso Monte_Carlo.pdf
updated: 2026-09-18
---

# Estimación de $\pi$ por Monte Carlo

El ejemplo clásico del [[metodo-de-monte-carlo]]: calcular $\pi$ "lanzando
dardos" al azar.

## El montaje

1. **Tablero:** un cuadrado de lado 2 centrado en el origen, $[-1,1]\times[-1,1]$.
   Área $= 4$.
2. **Objetivo:** el círculo inscripto de radio $r = 1$. Área $= \pi r^2 = \pi$.
3. **Juego:** generar $n$ puntos uniformes dentro del cuadrado.
4. **Conteo:** un punto cae dentro del círculo si $x^2 + y^2 \le 1$.

## De la proporción a $\pi$

**Paso 1 — relación de áreas:**

$$
\frac{A_{\text{círculo}}}{A_{\text{cuadrado}}} = \frac{\pi \cdot 1^2}{2^2} = \frac{\pi}{4}
$$

**Paso 2 — igualación por probabilidad:** como los puntos son uniformes, la
probabilidad de caer en el círculo es esa misma proporción de áreas:

$$
\frac{\pi}{4} \approx \frac{\text{puntos dentro}}{\text{puntos totales}}
$$

**Paso 3 — estimación final:**

$$
\pi \approx 4 \cdot \frac{\text{puntos dentro}}{\text{puntos totales}}
$$

## Convergencia observada

Resultados mostrados en las diapositivas:

| Puntos $n$ | Dentro | $\hat{\pi}$ | Fuente |
|-----------|--------|-------------|--------|
| 100 | 78 | 3.12 | `05A` |
| 1995 | 1558 | 3.1238 | `05B` |
| 3414 | 2683 | 3.1435 | `05B` |
| 5843 | 4601 | 3.1498 | `05B` |
| 10 000 | 7855 | 3.142 | `05A` |
| 10 000 | 7839 | 3.1356 | `05B` |
| 1 000 000 | — | 3.141592… | `05A` |

La convergencia no es monótona: una corrida con más puntos puede quedar
**peor** que otra con menos (compárense 5843 y 10 000 en `05B`). La
[[ley-de-los-grandes-numeros]] garantiza que la estimación converge, pero solo
en promedio. El error típico decrece como $1/\sqrt{n}$, así que ganar un dígito
de precisión cuesta $\approx 100$ veces más puntos.

## Implementación (Python, de `05A`/`05B`)

```python
import random

num_puntos = 1000000
puntos_dentro = 0

for _ in range(num_puntos):
    x = random.uniform(-1, 1)   # coordenada x en [-1, 1]
    y = random.uniform(-1, 1)   # coordenada y en [-1, 1]
    if x**2 + y**2 <= 1:        # ¿el dardo cayó dentro del círculo?
        puntos_dentro += 1

pi_estimado = (puntos_dentro / num_puntos) * 4
print(f"Estimación de π con {num_puntos} puntos: {pi_estimado}")
```

Variante equivalente (gráficos de `05B`): usar solo el primer cuadrante
$[0,1]\times[0,1]$ con el cuarto de círculo. La proporción sigue siendo $\pi/4$.

## Mapeo a la receta de 4 pasos

| Paso | En este ejemplo |
|------|-----------------|
| Definir el dominio | cuadrado de lado 2 |
| Generar muestras | puntos $(x, y)$ uniformes |
| Evaluar y contar | ¿$x^2 + y^2 \le 1$? |
| Calcular estimación | $\pi \approx 4 \cdot k/n$ |

Es un caso particular del método de "aciertos" de la
[[integracion-por-monte-carlo]] (área del círculo = integral).
