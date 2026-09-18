---
subject: modelado-y-simulacion
topic: Ley de los Grandes Números (LGN)
sources:
  - 05A Introducción al metodo de Monte Carlo.pdf
  - 05B Repaso Monte_Carlo.pdf
updated: 2026-09-18
---

# Ley de los Grandes Números (LGN)

La **garantía matemática** detrás del [[metodo-de-monte-carlo]]: su
fiabilidad no es casualidad.

## Enunciado

Si las muestras $x_1, x_2, \dots$ son **independientes e idénticamente
distribuidas** (i.i.d.), el promedio muestral se acerca al valor esperado
poblacional a medida que el tamaño de la muestra $n$ tiende a infinito:

$$
\lim_{n \to \infty} \frac{1}{n}\sum_{i=1}^{n} f(x_i) = E[f(x)]
$$

> Nota: en las diapositivas (`05A`, `05B`) la sumatoria aparece con límite
> superior $a$. Es un error tipográfico: el límite correcto es $n$.

## Lectura en términos de Monte Carlo

- Con suficientes "dardos", la estimación aleatoria **converge** al valor real.
- En integración, ese "valor promedio" está directamente ligado a la integral:
  $I = (b-a)\,E[f(X)]$ (ver [[integracion-por-monte-carlo]]).
- En la [[estimacion-de-pi-por-monte-carlo]], la proporción de puntos dentro
  del círculo converge a $\pi/4$.

## Lo que la LGN **no** dice

La convergencia es **oscilante**: para $n$ chicos la estimación salta mucho
alrededor del valor verdadero, y las oscilaciones se amortiguan a medida que
crece $n$ (gráfico de `05A`, con $n$ de 10 a $10^6$). La LGN asegura que se
llega, pero no dice **qué tan rápido** ni **cuán lejos** se está para un $n$
dado. Eso lo responde el [[teorema-central-del-limite]], que da el ritmo
$\sigma/\sqrt{n}$ y permite construir un [[intervalo-de-confianza]].

Relacionado: [[iteracion-y-convergencia]].
