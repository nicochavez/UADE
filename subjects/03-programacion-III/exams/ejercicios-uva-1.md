---
subject: programacion-iii
topic: Complejidad temporal de algoritmos recursivos (UVA 1)
sources:
  - "Notion: UVA 1"
  - "Notion: Ejercicios UVA 1"
updated: 2026-09-16
tags:
  - programacion-iii/exams
  - practica
  - complejidad-temporal
---

# Examen: Complejidad temporal de algoritmos recursivos

> [!abstract] Consigna general
> Analice cada uno de los algoritmos presentados a continuación, los cuales
> solo están diseñados con el propósito del cálculo de complejidad temporal y
> no como resolución de un problema concreto, y:
>
> **a)** Determine en qué caso de resolución de complejidad temporal
> recursiva aplica (sustracción o división).
>
> **b)** Realice el cálculo de complejidad temporal, justificando
> adecuadamente la elección de cada variable ($a$, $b$, $k$) y la conclusión
> final en notación $O$ o $\Theta$.

---

## Algoritmo 1

```
Metodo_1 (var conjunto[1..n], int n) {
    bool variableCond = calcularCondicion(conjunto)
    Si (variableCond) {
        Procesar(conjunto)
        Metodo_1(conjunto, n/3)
    } sino {
        Metodo_1(conjunto, n/3)
    }
    fin sino
}
```

Donde el tiempo de `calcularCondicion` es $O(\log n)$, y el de `Procesar` es
$O(n)$.
Resolucion:
a = 1
b = 3
k = P(log n + n) = 1
$a ?  b^k \rightarrow 1 = 3^1 \rightarrow a < b^k$
Caso  $a < b^k$
Complejidad: $\Theta (n)$

> [!failure] Corrección — error en el último paso
> $a=1$, $b=3$ y $k=1$ están **bien identificados**: el peor caso hace una
> sola llamada recursiva ($a=1$), la entrada se divide por 3 ($b=3$), y
> $p(n)=O(\log n)+O(n)=O(n)$ porque $n$ domina a $\log n$, lo que da grado
> $k=1$.
>
> El paso de comparación también está bien encaminado: $a=1 < 3^1=b^k$, así
> que corresponde el caso $a<b^k$.
>
> **Pero la fórmula de ese caso es $\Theta(n^k)$, no $\Theta(\log n)$.** Con
> $k=1$:
> $$T(n) \in \Theta(n^k) = \Theta(n^1) = \Theta(n)$$
> **Respuesta correcta: $\Theta(n)$**, no $\Theta(\log n)$. El error fue
> aplicar mal la fórmula en el último renglón después de identificar
> correctamente el caso — quedó "pegado" al $\log n$ de `calcularCondicion`
> en vez de usar el $k$ ya calculado.

---

## Algoritmo 2

```
Metodo_2 (var conjunto[1..n], int n) {
    bool variableCond = calcularCondicion(conjunto)
    Si (variableCond) {
        Procesar(conjunto)
    } sino {
        Metodo_2(conjunto, n/2)
        Metodo_2(conjunto, n/2)
    }
    fin sino
}
```

Donde el tiempo de `calcularCondicion` y de `Procesar` son constantes.
a = 2
b = 2
k = P(C) = 0
$2 > 2^0$
Caso $a>b^k$
Complejidad temporal: $\Theta (n^{log_2(2)})$

> [!success] Corrección — bien, solo falta simplificar
> Todo el desarrollo es correcto: dos llamadas recursivas en el peor caso
> ($a=2$), la entrada se divide a la mitad ($b=2$), el trabajo fuera de la
> recursión es constante ($k=0$), y $2 > 2^0=1$ da el caso $a>b^k$.
>
> Solo falta el último paso: simplificar el exponente.
> $$\log_2(2) = 1 \quad\Rightarrow\quad T(n) \in \Theta(n^{\log_2(2)}) = \Theta(n^1) = \Theta(n)$$
> **Respuesta correcta: $\Theta(n)$.** Tiene sentido: es el patrón de
> "dividir en dos mitades sin costo de combinar" (como recorrer un árbol
> binario completo), que da tiempo lineal.

---

## Algoritmo 3

```
Metodo_3 (var conjunto[1..n], int n) {
    int val = calcularValor(n)
    mientras (val < n) {
        Procesar(conjunto)
        val = val + 1
    } fin mientras
    Metodo_3(conjunto, n-1)
    Metodo_3(conjunto, n-1)
}
```

Donde el tiempo de `calcularValor` es constante y el de `Procesar` es
$O(n \log n)$.
a = 2
b = 1
k = $P(C + n*(n\space log\space n))=2$ 
 Caso : $a>1$
 Complejidad temporal: $\Theta(2^{n/1})$
Exponencial

> [!success] Corrección — correcto
> $a=2$ (dos llamadas recursivas), $b=1$ (baja de a uno en $n$) y el caso
> $a>1$ están bien. La conclusión también:
> $$T(n) \in \Theta(a^{n/b}) = \Theta(2^{n/1}) = \Theta(2^n)$$
> **Respuesta correcta: $\Theta(2^n)$, exponencial.** Un detalle menor para
> pulir la justificación: en el caso $a>1$ la fórmula $\Theta(a^{n/b})$ ya no
> depende de $k$ — el exponencial domina a cualquier polinomio o
> polilogaritmo que aporte $p(n)$, así que calcular $k=2$ acá no hace falta
> (no está mal, solo es trabajo de más).
