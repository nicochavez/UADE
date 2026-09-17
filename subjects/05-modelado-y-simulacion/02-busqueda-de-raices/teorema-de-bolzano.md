---
subject: modelado-y-simulacion
topic: Teorema de Bolzano
sources:
  - 01C Búsqueda_Binaria_de_Raíces.pdf
  - 01D Lectura 2.pdf
updated: 2026-08-07
---

# Teorema de Bolzano

El teorema de Bolzano da la condición matemática precisa para **garantizar la
existencia de una raíz** en un intervalo. Es el fundamento teórico del
[[metodo-de-biseccion]].

## Enunciado

- Sea $f(x)$ una función **continua** en un intervalo cerrado $[a, b]$.
- Si $f(a)$ y $f(b)$ tienen **signos opuestos** (es decir, $f(a) \cdot f(b) < 0$),
- entonces existe al menos un punto $c$ en el intervalo abierto $(a, b)$ tal que
  $f(c) = 0$.

## Intuición

Si una función continua está por debajo del eje x en `a` (negativa) y por encima
en `b` (positiva), es matemáticamente inevitable que cruce el eje en algún punto
intermedio. Es un caso particular del Teorema del Valor Intermedio.

No buscamos a ciegas: buscamos dentro de un intervalo donde la existencia de una
raíz *está garantizada*.

Relacionado: [[busqueda-de-raices]], [[metodo-de-biseccion]].
