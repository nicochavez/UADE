---
subject: modelado-y-simulacion
topic: Método de bisección (búsqueda binaria de raíces)
sources:
  - 01C Búsqueda_Binaria_de_Raíces.pdf
  - 01D Lectura 2.pdf
updated: 2026-08-07
---

# Método de bisección

La **búsqueda binaria de raíces** o método de bisección es una estrategia
iterativa simple y robusta para localizar raíces: "dividir para conquistar".
Se apoya en el [[teorema-de-bolzano]] y en el Teorema del Valor Intermedio.

## El algoritmo en pasos

1. **Seleccionar intervalo:** escoger $[a, b]$ tal que $f(a) \cdot f(b) < 0$ (garantiza
   al menos una raíz).
2. **Calcular punto medio:** $c = (a + b) / 2$.
3. **Condición de parada:** si $f(c) \approx 0$ (dentro de una tolerancia), $c$ es la
   raíz y el proceso termina.
4. **Actualizar límite superior:** si $f(a) \cdot f(c) < 0$, la raíz está en $[a, c]$ →
   hacer $b = c$.
5. **Actualizar límite inferior:** si $f(b) \cdot f(c) < 0$, la raíz está en $[c, b]$ →
   hacer $a = c$.

Los pasos 2 a 5 se repiten hasta alcanzar la precisión deseada. La longitud del
intervalo $(b - a)$ se reduce a la mitad en cada paso.

## Convergencia y cota de error

Convergencia **lineal** (siempre converge, pero lento). Cota de error explícita:

$$
|p_n - p| \le \frac{b - a}{2^n}
$$

Sirve para calcular *a priori* cuántas iteraciones $n$ hacen falta para una
tolerancia dada (ver [[analisis-de-error]]).

## Caso de estudio: $f(x) = x^3 - x - 2$ en $[1, 2]$

$f(1) = -2$ (negativo), $f(2) = 4$ (positivo) $\Rightarrow$ $f(1) \cdot f(2) = -8 < 0$, hay raíz.

| Iteración | a | b | c = (a+b)/2 | f(c) | Nuevo intervalo |
|-----------|-----|-------|--------|--------|-----------------|
| 1 | 1.0 | 2.0 | 1.5 | −0.125 | [1.5, 2.0] |
| 2 | 1.5 | 2.0 | 1.75 | 1.609 | [1.5, 1.75] |
| 3 | 1.5 | 1.75 | 1.625 | 0.666 | [1.5, 1.625] |
| 4 | 1.5 | 1.625 | 1.5625 | 0.252 | [1.5, 1.5625] |

## Implementación (Python, esquema de `01C`)

```python
import numpy as np

def biseccion(f, a, b, iteraciones=100, tolerancia=1e-6, precision=5):
    if f(a) * f(b) >= 0:
        raise ValueError("La función debe tener signos opuestos en a y b")
    for i in range(iteraciones):
        c = round((a + b) / 2.0, precision)
        fc = round(f(c), precision)
        if abs(fc) < tolerancia or (b - a) / 2.0 < tolerancia:
            return c
        if f(a) * f(c) < 0:
            b = c
        else:
            a = c
    raise ValueError("El método no convergió")
```

## Ejercicio del desafío (`01D Lectura 2.pdf`)

Encontrar la raíz de $f(x) = x^3 + 4x^2 - 10$ en $[1, 2]$ con tolerancia
$\varepsilon = 10^{-5}$, y calcular teóricamente cuántas iteraciones $n$ se necesitan usando
la fórmula de la cota de error.

Relacionado: [[busqueda-de-raices]], [[metodo-de-newton-raphson]].
