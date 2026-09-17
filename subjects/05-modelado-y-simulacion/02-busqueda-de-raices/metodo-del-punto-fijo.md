---
subject: modelado-y-simulacion
topic: Método del punto fijo
sources:
  - 01D Metodo del punto Fijo.pdf
  - 01A Metodos de aproximación Introducción.pdf
  - Geometric_Root_Finding (1).pdf
  - simulador_metodos_numericos-6.html
updated: 2026-08-21
---

# Método del punto fijo

Método iterativo para hallar raíces reformulando $f(x) = 0$ como un problema de
[[teorema-del-punto-fijo-de-banach|punto fijo]] $g(x) = x$.

## Definición

Un **punto fijo** $x^*$ de la función iteradora $g$ cumple $g(x^*) = x^*$: al
evaluarlo en $g$ se obtiene el mismo punto. Bajo el
[[teorema-del-punto-fijo-de-banach]] (espacio completo + función contractiva)
existe un único punto fijo y la iteración converge a él.

## Preparación de la función

Se parte de la función original $f(x)$ (cuyas raíces buscamos) y se la
transforma en una función a iterar $g(x)$. Para aplicar Banach, $g: X \to X$ debe
ser **contractiva** (ver [[condicion-de-lipschitz]]); entonces el punto fijo de
$g$ es la solución buscada.

## Mecánica de la convergencia

Partiendo de un $x_0$ arbitrario, se genera la sucesión por iteración:

$$
x_{n+1} = g(x_n) \quad \to \quad \lim_{n\to\infty} x_n = x^*
$$

Convergencia **lineal** ($p = 1$). La condición suficiente es que la derivada
esté acotada en todo el compacto $K$: si $g \in C^1(K)$ y $|g'(x)| < L < 1$ para
todo $x \in K$, la iteración converge infaliblemente al atractor (fuente:
`Geometric_Root_Finding (1).pdf`). Si $|g'(x)| \ge 1$ la iteración **diverge**.

## Interpretación geométrica

La raíz real $x^*$ se materializa como el punto donde la curva $y = g(x)$ corta
la recta identidad $y = x$. Cada iteración da dos "saltos": uno vertical hasta
la curva (evaluar $g(x_n)$) y uno horizontal hasta la recta identidad
(proyectar $x_{n+1}$), tejiendo una trayectoria en "telaraña" (*cobweb*) que
converge hacia el punto fijo.

Si esta convergencia lenta resulta un problema, se la puede acelerar con el
[[metodo-de-aitken]] sin cambiar la función $g(x)$.

## Caso de estudio: función trigonométrica

Para resolver $\cos(x) = 0$:

1. Función original: $f(x) = \cos(x)$
2. Igualando a cero: $0 = \cos(x)$
3. Sumando $x$ a ambos lados: $x = \cos(x) + x$
4. Función a iterar: $g(x) = \cos(x) + x$

## Implementación (Python, `01D Metodo del punto Fijo.pdf`)

```python
def g(x):
    return math.cos(x) + x

def fixed_point_iteration(x0, tol=1e-5, max_iter=100):
    x = x0
    iter_values = [x0]
    for i in range(max_iter):
        x_new = g(x)
        iter_values.append(x_new)
        if abs(x_new - x) < tol:
            break
        x = x_new
    return x_new, iter_values

x0 = 1.0  # valor inicial arbitrario
root, iter_values = fixed_point_iteration(x0)
```

La iteración sucesiva de $g(x)$ converge a la raíz de $f(x)$, demostrando el
cumplimiento del Teorema de Banach.

Relacionado: [[busqueda-de-raices]], [[metodo-de-newton-raphson]],
[[metodo-de-aitken]].
