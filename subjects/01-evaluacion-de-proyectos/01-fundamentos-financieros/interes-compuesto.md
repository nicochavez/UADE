---
subject: evaluacion-de-proyectos
topic: Interés compuesto y capitalización
sources:
  - EPT Clase 2_Matematica Financiera - Parte I.pdf
  - EPT Clase2_ResolucionEjerciciosEnClase.pdf
  - EPT_Clase2_EjerciciosRepaso.pdf
updated: 2026-09-14
tags:
  - evaluacion-de-proyectos/fundamentos
  - formula
  - parcial-1
---

# Interés compuesto

> [!abstract] En una frase
> En el interés compuesto los intereses **se reinvierten**: cada período se suman
> al capital y generan nuevos intereses. Por eso crece como una curva, no como una
> recta.

**Prerrequisitos:** [[interes-simple]], la versión lineal con la que se compara.
**Sigue con:** [[ecuacion-de-fisher]], para separar la inflación, y
[[valor-actual-neto]], donde esta fórmula se usa "al revés".

---

## El problema que resuelve

El [[interes-simple]] supone que los intereses se retiran, y en la vida real casi
nadie hace eso: préstamos, plazos fijos e inversiones **capitalizan**. Hace falta
una fórmula que refleje ese crecimiento, y es la fórmula más importante de la
unidad.

## Intuición: el cajón vs. dejar todo adentro

```
SIN capitalizar (simple)                CAPITALIZANDO (compuesto)
$100 al 10%, intereses al cajón         $100 al 10%, intereses quedan adentro

Año 1: 10% de $100 = $10  -> $110       Año 1: 10% de $100    = $10    -> $110
Año 2: 10% de $100 = $10  -> $120       Año 2: 10% de $110    = $11    -> $121
Año 3: 10% de $100 = $10  -> $130       Año 3: 10% de $121    = $12,10 -> $133,10
       el interés NO cambia                    el interés CRECE cada año
```

> [!example] Analogía: la bola de nieve
> Una bola de nieve que rueda junta más nieve cuanto más grande es, porque tiene
> más superficie. El capital funciona igual: **la tasa no cambia, lo que crece es
> la base** sobre la que se aplica.
>
> - Tamaño de la bola = capital acumulado
> - Nieve que junta en cada vuelta = interés del período
> - Cada vuelta = un período de capitalización

---

## Fórmula general

$$
C_n = C_0 \cdot (1 + i)^n
$$

| Símbolo | Significado |
|---|---|
| $C_n$ | Monto o capital final (valor futuro) |
| $C_0$ | Capital inicial (valor actual) |
| $i$ | Tasa por período |
| $n$ | Número de períodos de capitalización |

**Por qué tiene esta forma:** cada período el capital se multiplica por
$(1+i)$. Después de un período es $C_0(1+i)$; después de dos,
$C_0(1+i)(1+i) = C_0(1+i)^2$. Después de $n$, se multiplicó $n$ veces.

| Período | Interés del período | Monto acumulado |
|---|---|---|
| 1 | $C_0\,i$ | $C_0(1+i)^1$ |
| 2 | $C_0(1+i)\,i$ | $C_0(1+i)^2$ |
| 3 | $C_0(1+i)^2 i$ | $C_0(1+i)^3$ |
| $n$ | $C_{n-1}\,i$ | $C_0(1+i)^n$ |

## Las cuatro fórmulas despejadas

Cada ejercicio te da tres datos y te pide el cuarto:

| Busco | Fórmula | Cuándo aparece |
|---|---|---|
| Monto $C_n$ | $C_n = C_0(1+i)^n$ | "¿Cuánto tendré?" |
| Capital $C_0$ | $C_0 = \dfrac{C_n}{(1+i)^n}$ | "¿Cuánto invertir hoy?" (esto es **descontar**) |
| Tasa $i$ | $i = \left(\dfrac{C_n}{C_0}\right)^{1/n} - 1$ | "¿A qué tasa creció?" |
| Períodos $n$ | $n = \dfrac{\ln C_n - \ln C_0}{\ln (1+i)}$ | "¿Cuántos años tarda?" |
| Interés $I$ | $I = C_0\left[(1+i)^n - 1\right]$ | "¿Cuánto gané?" |

> [!tip] La fórmula de $C_0$ es la puerta al VAN
> Despejar $C_0$ es traer un monto futuro a hoy. El [[valor-actual-neto]] hace
> eso mismo con cada flujo del proyecto y los suma.

---

## Ejemplo con variación

**Caso:** ¿cuánto invertir hoy para tener $\$200$ en 5 años al $10\%$?

$$
C_0 = \frac{200}{(1{,}10)^5} \approx \$124{,}18
$$

**Variación:** si la tasa fuera más alta, alcanzaría con invertir **menos** hoy,
porque el dinero crece más rápido. A mayor tasa, menor valor actual. Esta
relación inversa es la que hace caer el VAN cuando sube la tasa.

---

## Simple vs. compuesto: la brecha se abre

![[interes-simple-vs-compuesto.svg|600]]

Fijate en que **la distancia entre las dos líneas no es constante**: crece con el
plazo. Mismo caso ($C_0 = \$100$, $i = 10\%$):

| Plazo | Interés simple | Interés compuesto | Brecha |
|---|---|---|---|
| 5 años | $\$50$ | $\$61$ | $\$11$ |
| 15 años | $\$150$ | $\$317{,}72$ | $\$167{,}72$ |

Otra forma de verlo: $\$1$ al $7\%$ tarda unos 10 años en llegar a $\$2$, pero
solo unos 3,5 años más en pasar de $\$2$ a $\$4$. La duplicación se acelera porque
la base es cada vez mayor.

> [!tip] Atajo mental: regla del 72 (no está en el material de la cátedra)
> Años para duplicar $\approx 72 / \text{tasa en } \%$. Al $7\%$:
> $72/7 \approx 10{,}3$ años; el valor exacto es $10{,}24$. Sirve para verificar
> resultados de $n$ rápidamente.

> [!quote] Frase popular
> "El interés compuesto es la octava maravilla del mundo. El que lo entiende, se
> beneficia; el que no, lo paga." Se la atribuye a Einstein, pero la primera
> aparición documentada es un aviso de *The New York Times* de 1983.

## Dónde aparece

Préstamos, plazos fijos e inversiones en general. Cuando un banco informa la
**TEA (Tasa Efectiva Anual)**, ese número ya incluye el efecto de la
capitalización, sin importar cada cuánto se liquide el interés durante el año.

---

## Errores comunes

| Error | Lo correcto |
|---|---|
| Multiplicar $C_0(1 + i \cdot n)$ en un ejercicio compuesto. | Eso es simple. Compuesto es $C_0(1+i)^n$: exponente, no producto. |
| Pensar que la brecha con el simple es fija. | La brecha **crece** con el plazo. |
| Creer que el compuesto siempre gana. | Con tasas distintas, un simple con tasa más alta puede ganar a plazos cortos (ver A3 de [[ejercicios-interes-e-inflacion]]). |
| Olvidar el $-1$ al despejar $i$. | $(C_n/C_0)^{1/n}$ da el **factor** $1+i$; hay que restar 1. |

---

## Autoevaluación

1. $\$12.000$ al $7\%$ compuesto durante 5 años. ¿Monto e interés?
   > [!question]- Respuesta
   > $C_5 = 12.000 \times 1{,}07^5 = \$16.830{,}62$.
   > $I = 16.830{,}62 - 12.000 = \$4.830{,}62$.

2. $\$15.000$ se convirtieron en $\$21.000$ en 4 años. ¿A qué tasa?
   > [!question]- Respuesta
   > $i = (21.000/15.000)^{1/4} - 1 = 1{,}4^{0{,}25} - 1 \approx 8{,}78\%$ anual.

3. ¿Cuántos años tardan $\$10.000$ en llegar a $\$25.000$ al $11\%$?
   > [!question]- Respuesta
   > $n = \dfrac{\ln 25.000 - \ln 10.000}{\ln 1{,}11} = \dfrac{\ln 2{,}5}{\ln 1{,}11} \approx 8{,}78$ años.

4. $\$30.000$ a 2 años: **A** simple $18\%$ vs. **B** compuesto $15\%$. ¿Cuál conviene?
   > [!question]- Respuesta
   > A: $30.000 \times (1 + 0{,}18 \times 2) = \$40.800$.
   > B: $30.000 \times 1{,}15^2 = \$39.675$.
   > A 2 años **conviene A**: el plazo es demasiado corto para que la
   > capitalización compense 3 puntos menos de tasa.

---

## Relacionado

- [[interes-simple]]: la base lineal contra la que se compara.
- [[ecuacion-de-fisher]]: qué parte del crecimiento es real y qué parte inflación.
- [[valor-actual-neto]]: la fórmula de $C_0$ aplicada a cada flujo de un proyecto.
- [[ejercicios-interes-e-inflacion]]: práctica resuelta.
