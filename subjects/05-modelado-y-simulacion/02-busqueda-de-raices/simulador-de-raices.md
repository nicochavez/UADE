---
subject: modelado-y-simulacion
topic: Simulador interactivo de raíces (herramienta de cátedra)
sources:
  - simulador_metodos_numericos-6.html
updated: 2026-08-21
---

# Simulador de raíces

Herramienta web de la cátedra (Ing. Omar Cáceres, UADE) que integra los cuatro
métodos de [[busqueda-de-raices]] vistos hasta la Clase 2. Es un archivo HTML
autocontenido: se abre directamente en el navegador desde
`raw/clase 2/simulador_metodos_numericos-6.html`.

> Hay dos copias idénticas del archivo en `raw/clase 2/`
> (`simulador_metodos_numericos-6.html` y `simulador_metodos_numericos-6 1.html`).

## Qué permite hacer

- Definir la función $f(x)$ o $g(x)$ con un teclado de funciones (`sin`, `cos`,
  `tan`, `exp`, `ln`, `sqrt`, `cbrt`, `pi`, …), usando `^` para potencias y `*`
  para producto.
- Fijar parámetros de iteración —intervalo $[a,b]$ o valor inicial $x_0$,
  tolerancia e iteraciones máximas—, admitiendo **valores negativos**.
- Observar la convergencia con gráficos, tabla de iteraciones y reproducción
  paso a paso.
- Cargar ejemplos precargados que corresponden a los ejercicios de la guía
  *Fundamentos de Modelado y Simulación* de la cátedra (ver
  [[parciales-y-practica]]).

## Pestañas y valores por defecto

| § | Método | Entrada por defecto | Nota de la herramienta |
|---|--------|---------------------|------------------------|
| §1 | [[metodo-de-biseccion|Bisección]] | $f(x) = x^3 - x - 2$, $[1, 2]$ | Requiere $f(a) \cdot f(b) < 0$ ([[teorema-de-bolzano]]) |
| §2 | [[metodo-del-punto-fijo|Punto fijo]] | $g(x) = \sqrt[3]{x + 2}$, $x_0 = 1.5$ | Ideal $\lvert g'(x) \rvert < 1$ cerca de $x_0$ |
| §3 | [[metodo-de-newton-raphson|Newton-Raphson]] | $f(x) = x^3 - x - 2$, $x_0 = 1.5$ | $f'(x)$ se calcula numéricamente por diferencia central |
| §4 | [[metodo-de-aitken|Aitken ($\Delta^2$)]] | $g(x) = \sqrt[3]{x + 2}$, $x_0 = 1.5$ | Aplica $\Delta^2$ sobre cada terna $(x_n, x_{n+1}, x_{n+2})$ |

En las cuatro pestañas la tolerancia por defecto es `0.0001` y el máximo de
iteraciones `50`.

Relacionado: [[busqueda-de-raices]], [[analisis-de-error]].
