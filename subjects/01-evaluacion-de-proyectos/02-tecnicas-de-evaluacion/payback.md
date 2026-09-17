---
subject: evaluacion-de-proyectos
topic: Payback o período de repago
sources:
  - EPT Clase 2_Matematica Financiera - Parte I.pdf
  - EPT_Clase3y4_MatematicaFinanciera_II_Ejercicios_Soluciones.xlsx
updated: 2026-09-14
tags:
  - evaluacion-de-proyectos/tecnicas
  - indicador
  - enfoque-contable
  - parcial-1
---

# Payback (período de repago)

> [!abstract] En una frase
> El payback responde **"¿en cuánto tiempo recupero lo que puse?"**. Mide
> velocidad de recupero, no rentabilidad.

**Prerrequisitos:** [[flujo-de-fondos]], sobre todo las columnas de acumulados.
**Sigue con:** [[valor-actual-neto]], el indicador que sí mide valor.

---

## Intuición

> [!example] Analogía: la cafetera de la oficina
> La oficina compra una cafetera de $\$10.000$. Cada año se ahorran $\$3.000$ de
> café comprado afuera. ¿Cuándo "se pagó" la cafetera?
>
> - Año 1: ahorro acumulado $\$3.000$. Todavía faltan $\$7.000$.
> - Año 2: $\$6.000$. Faltan $\$4.000$.
> - Año 3: $\$9.000$. Faltan $\$1.000$.
> - Año 4: $\$12.000$. **Ya se pagó**, en algún momento durante el año 4.
>
> Ese "momento" es el payback. Es un método tradicional que prioriza la
> **liquidez** y la rápida recuperación del capital expuesto.

## Cómo se ve

```
Acumulado nominal
  +2.000 |                              ● año 4
       0 |- - - - - - - - - - - - - - ╱- - - - -   <- cruza el cero en 3,33 años
  -1.000 |                     ● año 3
  -4.000 |            ● año 2
  -7.000 |   ● año 1
 -10.000 ● año 0
         +----------------------------------------> tiempo
```

---

## Cálculo

1. Acumulá los flujos hasta que el acumulado pase de negativo a positivo.
2. $t^{*}$ es el **último período con acumulado negativo**.
3. Interpolá la fracción del año siguiente:

$$
\text{Payback} = t^{*} + \frac{|\text{acumulado en } t^{*}|}{FF_{t^{*}+1}}
$$

| Parte | Significado |
|---|---|
| $t^{*}$ | Años completos en los que todavía no se recuperó |
| $\lvert\text{acumulado en } t^{*}\rvert$ | Lo que falta recuperar al final de ese año |
| $FF_{t^{*}+1}$ | Lo que entra en el año siguiente |

**Por qué tiene esta forma:** se supone que el flujo del año siguiente llega
parejo a lo largo del año. Si faltan $\$1.000$ y ese año entran $\$3.000$, hace
falta un tercio del año.

**Ejemplo:** inversión $\$10.000$ y flujos de $\$3.000$ anuales.

$$
\text{Payback} = 3 + \frac{1.000}{3.000} = 3{,}33 \text{ años, unos 3 años y 4 meses}
$$

---

## Simple vs. descontado

| | Payback simple | Payback descontado |
|---|---|---|
| Columna que usa | Acumulado **nominal** | Acumulado **descontado** |
| ¿Considera el valor tiempo? | ❌ | ✅ |
| Ejemplo ($\$10.000$, $\$3.000 \times 5$, $10\%$) | $3{,}33$ años | $4 + 490{,}40/1.862{,}76 = 4{,}26$ años |
| Resultado relativo | Más corto | **Siempre más largo** |

El descontado puede directamente **no recuperarse** dentro del horizonte aunque el
simple sí lo haga.

> [!tip] Diagnóstico rápido
> Payback simple razonable pero descontado "no se recupera" es la señal de un
> proyecto con VAN negativo. Ejercicio 1 de la práctica: simple $3{,}14$ años,
> descontado *"no se recupera en el horizonte"*, VAN $-\$1.167{,}94$.

---

## Limitaciones

> [!failure] Lo que el payback no ve
> 1. **Ignora los flujos posteriores al recupero.** Un proyecto que se repaga en
>    2 años y después no genera nada le "gana" a uno que se repaga en 3 y genera
>    20 años más.
> 2. En su versión simple **ignora el [[valor-tiempo-del-dinero]]**.
> 3. **No mide rentabilidad**, mide velocidad.

---

## Errores comunes

| Error | Lo correcto |
|---|---|
| Tomar como $t^{*}$ el primer año con acumulado positivo. | $t^{*}$ es el **último negativo**; la fracción se suma a ese. |
| Dividir por el flujo del año $t^{*}$. | Se divide por el flujo del año **siguiente**, $t^{*}+1$. |
| En el descontado, dividir por el flujo nominal. | Todo con valores **descontados**. |
| "Menor payback, entonces mejor proyecto." | Solo más rápido; puede crear menos valor. |

---

## Autoevaluación

1. Inversión $\$18.000$; flujos $\$5.000$, $\$6.000$, $\$6.000$, $\$7.000$. ¿Payback simple?
   > [!question]- Respuesta
   > Acumulado: $-13.000$, $-7.000$, $-1.000$, $+6.000$. $t^{*} = 3$.
   > $\text{Payback} = 3 + 1.000/7.000 = 3{,}14$ años.

2. ¿Por qué el payback descontado siempre es mayor o igual que el simple?
   > [!question]- Respuesta
   > Porque cada flujo futuro descontado vale menos que su valor nominal, así que
   > se tarda más en acumular la misma inversión.

---

## Relacionado

- [[roi-y-roa]]: el otro indicador contable.
- [[flujo-de-fondos]]: de dónde salen los acumulados.
- [[valor-actual-neto]]: considera todos los flujos, incluidos los posteriores al recupero.
- [[tecnicas-de-evaluacion-de-proyectos]]: comparación general.
