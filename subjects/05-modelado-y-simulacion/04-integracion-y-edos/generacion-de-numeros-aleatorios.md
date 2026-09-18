---
subject: modelado-y-simulacion
topic: Generación de números aleatorios y semilla
sources:
  - 05A Introducción al metodo de Monte Carlo.pdf
  - 05B Repaso Monte_Carlo.pdf
updated: 2026-09-18
---

# Generación de números aleatorios

El motor (la "materia prima") del [[metodo-de-monte-carlo]]: la calidad de
una simulación depende de la calidad de sus números aleatorios.

## El requisito: distribución uniforme

Monte Carlo necesita generar números con **distribución uniforme**: cada valor
de un intervalo tiene la misma probabilidad de ser elegido. En Python:

```python
import random

for _ in range(5):
    print(random.uniform(0, 1))   # flotante aleatorio en [a, b] = [0, 1]
```

Cada ejecución produce una secuencia **distinta** (`05A` muestra dos corridas
consecutivas con valores diferentes: `0.5415…`, `0.0852…` vs. `0.1531…`,
`0.0006…`).

## Azar controlado: la semilla (`seed`)

**Problema:** si los resultados cambian en cada corrida, ¿cómo se depura el
código o se verifican los resultados de otra persona?

**Solución:** fijar una **semilla**. Con la misma semilla, el generador
produce siempre la misma secuencia, y el experimento se vuelve 100%
reproducible.

```python
import random

random.seed(42)          # se establece la semilla
for _ in range(5):
    print(random.uniform(0, 1))

random.seed(42)          # se restablece la MISMA semilla
for _ in range(5):
    print(random.uniform(0, 1))
# Ambas corridas imprimen: 0.6394..., 0.0250..., 0.2750..., 0.2232..., 0.7364...
```

## Pseudoaleatoriedad

Que una semilla reproduzca la secuencia exacta muestra que estos números **no
son verdaderamente aleatorios**: son *pseudoaleatorios*, generados por un
algoritmo determinista a partir del estado inicial (la semilla). Para
simulación esto es una ventaja: se tiene aleatoriedad estadística con
reproducibilidad.

Relacionado: [[estimacion-de-pi-por-monte-carlo]], [[integracion-por-monte-carlo]].
