---
subject: modelado-y-simulacion
topic: Simulador de reconstrucción de funciones (herramienta de cátedra)
sources:
  - reconstruccion_funciones_v3.html
updated: 2026-08-21
---

# Simulador de reconstrucción de funciones

Herramienta web de la cátedra (Ing. Omar Cáceres, UADE), archivo HTML
autocontenido en `raw/clase 3/reconstruccion_funciones_v3.html`. Complementa
al [[simulador-de-raices]] cubriendo el segundo bloque del curso:
[[interpolacion-polinomica]] y [[diferencias-finitas]].

## Qué permite hacer

- Cargar puntos manualmente (tabla editable, de 3 a 10 nodos) o elegir entre
  **presets** de funciones conocidas: $\sin(x)$, $e^x$, $1/(1+x^2)$ (función
  de Runge, clásica para mostrar el problema de oscilación en interpolación
  de alto grado), $\ln(x)$, $x^2-2x$, $\cos(x)$.
- Definir el rango $[a, b]$ y la cantidad de nodos a muestrear sobre la
  función verdadera elegida.
- Comparar **seis métodos** de reconstrucción sobre el mismo conjunto de
  puntos, seleccionables por pestaña:

| Método | Relacionado con |
|---|---|
| Lagrange | [[polinomio-de-lagrange]] |
| Newton ↑ (progresivas) | diferencias divididas de Newton, forma incremental |
| Newton ↓ (regresivas) | ídem, construida desde el extremo final |
| Diferencias Divididas | tabla de diferencias divididas de Newton |
| Lineal (por tramos) | interpolación lineal simple entre nodos consecutivos |
| Spline Cúbico | polinomios cúbicos por tramos con continuidad en la derivada |

- Ver en tiempo real el **grado** del polinomio, la cantidad de **nodos**, y
  el **error máximo** observado frente a la función verdadera (cuando se usa
  un preset).
- Mostrar la fórmula LaTeX explícita del polinomio construido (Lagrange,
  Newton o cota de error) según el método activo.
- Pasar el mouse sobre el gráfico para inspeccionar valores puntuales
  (tooltip interactivo).

## Secciones de contenido adicionales

Más allá del simulador interactivo, el archivo incluye dos secciones de
lectura que conectan la interpolación con aprendizaje automático:

- **Interpolación como base del aprendizaje supervisado** — el ajuste de un
  modelo a datos de entrenamiento como una generalización del problema de
  interpolación.
- **Casos de uso concretos en IA/ML** — ejemplos de dónde aparece este mismo
  problema (reconstruir una función a partir de puntos) en el entrenamiento
  de modelos.

Relacionado: [[interpolacion-polinomica]], [[polinomio-de-lagrange]],
[[diferencias-finitas]], [[simulador-de-raices]].
