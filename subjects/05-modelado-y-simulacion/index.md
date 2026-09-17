# Modelado y Simulación — Índice

Vault de la materia **Modelado y Simulación** (UADE, 3.1.025). Idioma: español.
Las páginas de conocimiento se construyen a partir del material en `raw/` y se
organizan en carpetas temáticas numeradas.

- [[programa-del-curso]] — cronograma, fechas de evaluación y mapa de los 8 bloques del curso.

## 01 · Fundamentos

El lenguaje de la precisión y las garantías matemáticas.

- [[modelado-y-simulacion]] — modelo matemático vs. simulación; por qué aproximar.
- [[metodos-numericos]] — qué son, las tres tareas clave (raíces, integración, EDOs).
- [[notacion-big-o]] — cómo escala un algoritmo con el tamaño de los datos.
- [[iteracion-y-convergencia]] — iteración $x_{n+1}=f(x_n)$, convergencia y orden.
- [[analisis-de-error]] — error absoluto/relativo, cota de error y criterios de detención.
- [[conjuntos-compactos]] — compacidad, Heine-Borel; el territorio de la certidumbre.
- [[condicion-de-lipschitz]] — límite de velocidad de una función; contracciones.
- [[teorema-del-punto-fijo-de-banach]] — existencia, unicidad y convergencia garantizada.
- [[teorema-de-weierstrass]] — existencia de máximos y mínimos en un compacto.

## 02 · Búsqueda de raíces

Resolver $f(x) = 0$.

- [[busqueda-de-raices]] — panorama, comparación y matriz de decisión algorítmica.
- [[teorema-de-bolzano]] — condición que garantiza una raíz.
- [[metodo-de-biseccion]] — búsqueda binaria; algoritmo, cota de error y código.
- [[metodo-de-newton-raphson]] — tangente y convergencia cuadrática.
- [[metodo-del-punto-fijo]] — reformular $f(x)=0$ como $g(x)=x$.
- [[metodo-de-aitken]] — proceso Δ² para acelerar una sucesión que converge lento.
- [[simulador-de-raices]] — herramienta interactiva de la cátedra con los cuatro métodos.

## 03 · Interpolación y derivación numérica

Reconstruir un modelo continuo a partir de datos discretos, y estimar su tasa de cambio.

- [[interpolacion-polinomica]] — el problema, existencia/unicidad, cota de error, interpolación vs. extrapolación.
- [[polinomio-de-lagrange]] — construcción explícita $P(x)=\sum y_i L_i(x)$, código.
- [[diferencias-finitas]] — progresivas/regresivas/centrales para estimar derivadas; conexión con Taylor.
- [[simulador-de-reconstruccion-de-funciones]] — herramienta de la cátedra: Lagrange, Newton, spline y lineal por tramos.

## 04 · Integración y ecuaciones diferenciales

Calcular $\int_a^b f(x)\,dx$ cuando no hay primitiva, y resolver EDOs.

- [[integracion-numerica]] — panorama: enfoques deterministas vs. Monte Carlo.
- [[formulas-de-newton-cotes]] — la familia completa: estrategia, simple vs. compuesta, error y tabla comparativa.
- [[regla-del-rectangulo]] — polinomio de grado 0, altura en el punto medio.
- [[regla-del-trapecio]] — grado 1, simple y compuesta, error $O(h^2)$.
- [[regla-de-simpson-1-3]] — parábolas, $O(h^4)$, requiere $n$ par.
- [[regla-de-simpson-3-8]] — cúbicas, requiere $n$ múltiplo de 3.
- [[cuadratura-de-gauss-legendre]] — nodos y pesos optimizados; exacta hasta grado $2n-1$.
- [[simulador-de-newton-cotes]] — herramienta de la cátedra con los ocho métodos y sus aplicaciones reales.
- [[ecuaciones-diferenciales-ordinarias]] — Euler y Runge-Kutta 4.

## 05 · Sistemas dinámicos

- [[sistemas-dinamicos]] — espacio de fases, equilibrios, estabilidad y autovalores.
- [[bifurcaciones]] — puntos de inflexión y cambios de régimen.
- [[modelos-aplicados]] — Lotka-Volterra, Lanchester, SIR, Strogatz y Lorenz.

## exams

- [[parciales-y-practica]] — calendario de parciales/finales y ejercicios de práctica.
