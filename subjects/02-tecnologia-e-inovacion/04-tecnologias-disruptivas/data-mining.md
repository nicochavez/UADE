---
subject: tecnologia-e-innovacion
topic: Minería de datos (Data Mining)
sources:
  - Tecnología e Innovación Clase 6  martes noche 2026.pptx
updated: 2026-09-10
---

# Data Mining

La **minería de datos** es un proceso **técnico y automatizado** que analiza
grandes volúmenes de información ([[big-data]]) para descubrir **patrones,
tendencias, anomalías y correlaciones ocultas**.

Utiliza técnicas estadísticas y de inteligencia artificial para convertir datos
brutos en **conocimiento estratégico**, permitiendo predecir comportamientos,
reducir costos y tomar mejores decisiones.

El ejemplo con el que la Clase 6 abre el tema:

> "Un supermercado descubre que quienes compran pañales también compran
> gaseosas."

Nadie le preguntó eso a los datos: el patrón **emergió**. Ésa es la esencia del
data mining frente a una consulta SQL común — no se busca una respuesta
conocida, se descubre una relación que no se sospechaba.

## El proceso de minería de datos

Seis pasos, en orden:

1. **Selección** — definir los conjuntos de datos relevantes.
2. **Limpieza** — eliminar ruido, errores y datos duplicados.
3. **Reducción** — seleccionar las características más relevantes para el
   análisis.
4. **Transformación** — adaptar los datos al formato necesario para el modelado.
5. **Extracción (minado)** — aplicar los algoritmos para encontrar los patrones.
6. **Interpretación / evaluación** — analizar los patrones encontrados para
   obtener conclusiones.

Nótese que **cuatro de los seis pasos ocurren antes de aplicar el algoritmo**:
el trabajo real está en preparar los datos, no en minarlos. Esto conecta con la
**veracidad** de las 5 V ([[big-data]]).

## Las cuatro técnicas

| Técnica | Tipo | Qué hace | Ejemplo |
|---|---|---|---|
| **Clasificación** | Predictiva | Asigna elementos a **categorías predefinidas** | Determinar si un cliente "comprará" o "no comprará" |
| **Agrupamiento (*clustering*)** | Descriptiva | Agrupa datos **sin etiquetas previas** en conjuntos según similitudes | Segmentación de clientes |
| **Reglas de asociación** | Descriptiva | Encuentra qué elementos **suelen aparecer juntos** | Análisis de cestas de compra (pañales y gaseosas) |
| **Árboles de decisión** | Predictiva | Modelo **visual** de reglas de decisión para clasificar o predecir | Scoring crediticio |

La diferencia clave entre clasificación y clustering: la clasificación **ya sabe
cuáles son las categorías** y aprende a asignarlas; el clustering **descubre las
categorías** por sí mismo.

## Aplicaciones desde el área informática

- **Ciberseguridad y detección de intrusos** — análisis del tráfico de red para
  identificar patrones anómalos que indican ataques, en tiempo real.
- **Mantenimiento predictivo** — datos de sensores para predecir fallos en
  servidores o hardware **antes** de que ocurran.
- **Análisis de logs y rendimiento** — minería de archivos de registro para
  encontrar causas raíz de errores o cuellos de botella.
- **Web mining** — comportamiento del usuario en sitios web para personalizar la
  interfaz, mejorar la navegación y predecir clics.
- **Sistemas de recomendación** — Netflix o Spotify analizando historial de
  búsquedas y visualizaciones.
- **Optimización de búsquedas** — análisis de las consultas más frecuentes y la
  relevancia de los resultados.

## Empresas que lo usan

| Empresa | Uso |
|---|---|
| **Amazon** | Recomendaciones en tiempo real y optimización de la cadena de suministro |
| **Netflix / Spotify** | Hábitos de visualización y escucha para crear contenido original y recomendar |
| **Starbucks** | Geolocalización para decidir dónde abrir nuevas tiendas |
| **BBVA** | Segmentación de clientes, prevención de fraude, evaluación de riesgos |
| **Zara (Inditex)** | Ventas en tiempo real para optimizar inventarios y ajustar producción a la demanda |
| **Walmart / minoristas** | Hábitos de compra para mejorar la colocación de productos en tienda |
| **Tesla, Google, Meta** | IA y minería para automatizar procesos y mejorar productos |

## Sectores

- **Banca y seguros** — detección de fraudes, riesgo crediticio, reducción de la
  deserción de clientes (*churn*).
- **Atención médica** — historiales para predecir necesidades de pacientes y
  gestionar recursos.
- **Telecomunicaciones** — patrones de comportamiento para evitar el abandono
  del servicio.
- **Retail y e-commerce** — personalización de ofertas y optimización de
  precios.

## Para reflexionar (Clase 6)

> ¿Hasta qué punto es ético que las empresas usen Data Mining para predecir el
> comportamiento de los clientes, **incluso antes de que ellos mismos sean
> conscientes de sus decisiones**?
>
> Si una empresa toma decisiones importantes basadas en patrones encontrados por
> Data Mining, **¿quién es responsable si esas decisiones resultan incorrectas:
> la empresa, el analista o el algoritmo?**

Relacionado: [[big-data]], [[big-data-vs-data-mining]],
[[business-intelligence]], [[inteligencia-artificial]],
[[tecnologias-disruptivas]].
