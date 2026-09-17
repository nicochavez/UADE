---
subject: modelado-y-simulacion
topic: Cuadratura de Gauss-Legendre
sources:
  - newton-cotes-simulador.html
updated: 2026-08-28
---

# Cuadratura de Gauss-Legendre

Familia de cuadratura **distinta** a las [[formulas-de-newton-cotes]],
presentada como contraste en el [[simulador-de-newton-cotes]].

La diferencia es de grados de libertad:

- **Newton-Cotes** fija los nodos equiespaciados y solo optimiza los pesos.
- **Gauss-Legendre** elige **tanto la ubicación de los nodos como los pesos**
  para maximizar la exactitud.

## La ganancia

Con $n$ puntos (no equiespaciados), la regla es **exacta para polinomios de
grado $2n-1$** — el doble que un Newton-Cotes con la misma cantidad de nodos.
Duplicar el orden de exactitud sin evaluar más veces la función es lo que la
hace atractiva.

$$
\int_a^b f(x)\,dx \approx \sum_{i=1}^{n} w_i\, f(x_i)
$$

Los nodos $x_i$ y pesos $w_i$ están tabulados para el intervalo canónico
$[-1, 1]$ y se trasladan a $[a, b]$ con un cambio de variable lineal.

Su error:

$$
E_n = \frac{2^{2n+1}(n!)^4}{(2n+1)\,[(2n)!]^3}\, f^{(2n)}(\xi), \qquad \xi \in (-1,1)
$$

## El precio

Exige **poder evaluar $f$ en puntos arbitrarios**. Si solo se dispone de una
tabla de datos muestreados en una malla regular —el caso habitual cuando los
datos vienen de un sensor— Gauss-Legendre no es aplicable y hay que volver a
Newton-Cotes.

## Dónde aparece

En el simulador se la usa para los casos que exigen alta precisión con muy
pocas evaluaciones: el trabajo mecánico de un actuador robótico
($\int \tau(\theta)\,d\theta$ con 4 nodos, pensado para control en tiempo real)
y la evidencia de un modelo bayesiano ($\int P(D|\theta)P(\theta)\,d\theta$ con
5 nodos).

Relacionado: [[integracion-numerica]], [[formulas-de-newton-cotes]],
[[simulador-de-newton-cotes]].
