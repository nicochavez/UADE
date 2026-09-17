---
subject: modelado-y-simulacion
topic: Qué son los métodos numéricos
sources:
  - 01A Introducción Modelado y Simulación.pdf
  - 01D Lectura 1.pdf
  - 01D Lectura 2.pdf
updated: 2026-08-07
---

# Métodos numéricos

Cuando las soluciones analíticas son impracticables, recurrimos a la
computación. Los **métodos numéricos** son el motor que permite encontrar
soluciones *aproximadas* de alta precisión, paso a paso.

## Las tres tareas clave

Según `01A Introducción Modelado y Simulación.pdf`, los métodos numéricos nos
ayudan a:

1. **Encontrar equilibrios** → [[busqueda-de-raices]] de ecuaciones ($f(x)=0$).
2. **Acumular cambios** → [[integracion-numerica]].
3. **Simular la evolución** → resolver [[ecuaciones-diferenciales-ordinarias]].

## Por qué son clave

Permiten transformar la complejidad del mundo real en conocimiento práctico:
desde la órbita de un planeta hasta la propagación de una epidemia o un circuito
eléctrico. Son la base para encontrar equilibrios, óptimos y soluciones de estado
estacionario.

## Cómo se miden y controlan

Todo método numérico útil requiere garantías:

- **[[iteracion-y-convergencia]]** — que las aproximaciones se acerquen a la solución.
- **[[notacion-big-o]]** — cómo escala el costo con el tamaño de los datos.
- **[[analisis-de-error]]** — cuán buena es la aproximación y cuándo detenerse.
- **[[conjuntos-compactos]]** y **[[condicion-de-lipschitz]]** — la estructura
  que *garantiza* la existencia y unicidad de la solución.

> La precisión no es un punto de partida; es un destino que se construye.

Relacionado: [[modelado-y-simulacion]], [[programa-del-curso]].
