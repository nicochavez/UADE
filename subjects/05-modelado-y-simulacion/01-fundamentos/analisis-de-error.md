---
subject: modelado-y-simulacion
topic: Error absoluto/relativo y criterios de detención
sources:
  - 01A Metodos de aproximación Introducción.pdf
  - 01D Lectura 2.pdf
updated: 2026-08-07
---

# Análisis de error

## Cota de error

Una **cota de error** es una estimación del error máximo que se comete en un
proceso iterativo o aproximación. Garantiza que el resultado queda dentro de una
tolerancia aceptable.

## Error absoluto vs. error relativo

- **Error absoluto:** diferencia entre el valor exacto $x^*$ y la aproximación
  $x_n$. Fórmula práctica entre iteraciones:

  $$
  E_{abs} \approx |x_{n+1} - x_n|
  $$

- **Error relativo:** cuantifica la precisión *en comparación* con el valor
  (fracción o porcentaje):

  $$
  E_{rel} \approx \frac{|x_{n+1} - x_n|}{|x_{n+1}|}
  $$

La distinción importa: un error absoluto de 1 mm es enorme en un engranaje de
10 mm pero despreciable en una viga de 1000 mm (mismo error absoluto, impacto
relativo muy distinto — ejemplo de `01A Metodos de aproximación`).

## Criterios de detención

Reglas que definen cuándo un método iterativo debe parar:

1. **Tolerancia en error absoluto:** $|x_{n+1} - x_n| \le \varepsilon$
2. **Tolerancia en error relativo:** $\dfrac{|x_{n+1} - x_n|}{|x_{n+1}|} \le \varepsilon$
3. **Condición sobre el residuo:** $|f(x_n)| \le \varepsilon$
4. **Número máximo de iteraciones:** $n > N_{max}$ (evita bucles infinitos)

## Cota de error del método de bisección

Para [[metodo-de-biseccion|bisección]], la cota es explícita y sirve para
calcular *a priori* cuántas iteraciones hacen falta:

$$
|p_n - p| \le \frac{b - a}{2^n}
$$

Relacionado: [[iteracion-y-convergencia]], [[metodos-numericos]].
