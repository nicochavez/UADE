---
subject: modelado-y-simulacion
topic: Fórmulas de Newton-Cotes (familia)
sources:
  - 04A Newton Cotes.pdf
  - newton-cotes-simulador.html
updated: 2026-08-28
---

# Fórmulas de Newton-Cotes

Familia de reglas de **cuadratura numérica** que aproximan $\int_a^b f(x)\,dx$
reemplazando $f$ por un **polinomio interpolante de grado $n$ que pasa por
$n+1$ nodos equiespaciados**, e integrando ese polinomio de forma exacta.
Es el contenido central de la Clase 4 y la vía determinista de la
[[integracion-numerica]].

## El problema que resuelven

Muchas funciones no tienen primitiva elemental. El ejemplo con el que abre la
clase es

$$
\int_0^2 \frac{2+\cos\left(1+x^{3/2}\right)}{\sqrt{1+0.5\sin x}}\, e^{0.5x}\,dx
$$

No existe solución exacta simple, y muchas veces ni siquiera se dispone de la
fórmula de $f$: solo de una tabla de pares $(x_i, f(x_i))$. En ambos casos la
única salida es aproximar.

## La estrategia fundamental

> Si no podemos integrar la función original, la sustituimos por un polinomio
> más simple (una recta, una parábola) que sí sea fácil de integrar.

El pipeline conceptual es siempre el mismo (`04A Newton Cotes.pdf`):

**función continua → puntos discretos → aproximación polinomial → área**

Mecánicamente:

1. Se divide $[a,b]$ en $n$ subintervalos de ancho $h = \dfrac{b-a}{n}$,
   generando los nodos $x_0=a,\ x_1,\ \dots,\ x_n=b$ con $x_i = a + ih$.
2. Se interpola $f$ con un [[polinomio-de-lagrange]] que pasa exactamente por
   esos nodos.
3. Se integra ese polinomio en forma cerrada. El resultado es siempre una
   **suma ponderada de valores de la función**:

$$
\int_a^b f(x)\,dx \approx \sum_{i=0}^{n} c_i\, f(x_i)
$$

Los pesos $c_i$ son constantes fijas por regla (por ejemplo $1,4,2,4,\dots,1$
en Simpson 1/3): no dependen de $f$, solo del grado del polinomio elegido.
Esto es lo que las hace baratas de implementar — ver [[interpolacion-polinomica]].

## Simple vs. compuesta

- **Fórmula simple**: se usa un único polinomio sobre todo $[a,b]$.
- **Fórmula compuesta**: se repite un panel de bajo orden (grado 1, 2 o 3)
  sobre varios subintervalos y se suman las contribuciones.

Las compuestas son las que se usan en la práctica. Subir el grado del
polinomio en una fórmula *simple* con muchos nodos no es buena idea: reaparece
el **fenómeno de Runge** (oscilaciones del interpolante de alto grado, ver
[[interpolacion-polinomica]]). "Dividir para conquistar" es preferible a
"un polinomio gigante".

## Error de truncamiento

Toda regla de Newton-Cotes tiene un error de la forma

$$
E_t = C \cdot h^{\,k} \cdot f^{(m)}(\xi), \qquad \xi \in [a,b]
$$

donde $\xi$ es un punto **desconocido** del intervalo — por eso se lo llama
error de truncamiento *local*, y en la práctica se lo usa como **cota**
acotando $|f^{(m)}|$ en $[a,b]$ (ver [[analisis-de-error]]).

La lectura importante es el exponente de $h$: dice cómo mejora la aproximación
al refinar la malla (ver [[notacion-big-o]]). Si el error compuesto es
$O(h^4)$, duplicar $n$ divide el error por $\approx 16$.

## Tabla comparativa

Resumen del cierre de la clase (`04A Newton Cotes.pdf`):

| Regla | Grado del polinomio | Puntos por panel | Error compuesto | Restricción sobre $n$ |
|---|---|---|---|---|
| [[regla-del-rectangulo]] (punto medio) | 0 (constante) | 1 | $O(h^2)$ | ninguna |
| [[regla-del-trapecio]] | 1 (lineal) | 2 | $O(h^2)$ | ninguna |
| [[regla-de-simpson-1-3]] | 2 (cuadrático) | 3 | $O(h^4)$ | $n$ **par** |
| [[regla-de-simpson-3-8]] | 3 (cúbico) | 4 | $O(h^4)$ | $n$ **múltiplo de 3** |
| Boole | 4 (cuártico) | 5 | $O(h^6)$ | $n$ **múltiplo de 4** |

### Regla de Boole

El siguiente escalón de la familia, disponible en el
[[simulador-de-newton-cotes]] en su versión simple ($n = 4$, $h = (b-a)/4$):

$$
\int_a^b f(x)\,dx \approx \frac{2h}{45}\left[7f_0 + 32f_1 + 12f_2 + 32f_3 + 7f_4\right],
\qquad E_t = -\frac{8h^7}{945}\,f^{(6)}(\xi)
$$

## Conclusiones de la clase

- **Aproximar es poder**: sustituir la función por polinomios simples permite
  resolver integrales que no tienen primitiva.
- **La precisión escala con la complejidad**: rectángulo → trapecio → Simpson
  mejora significativamente la exactitud.
- **Dividir para conquistar**: las reglas compuestas son la clave de los
  resultados precisos en la práctica.
- **No hay una "mejor" regla**: la elección balancea precisión deseada
  (Simpson > trapecio), costo computacional y las restricciones sobre $n$
  ($n$ par, $n$ múltiplo de 3).

Una familia distinta —que rompe la restricción de nodos equiespaciados y gana
mucha precisión— es la [[cuadratura-de-gauss-legendre]].

Relacionado: [[integracion-numerica]], [[metodos-numericos]],
[[simulador-de-newton-cotes]].
