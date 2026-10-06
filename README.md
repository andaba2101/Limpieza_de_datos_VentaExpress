# Limpieza_de_datos_VentaExpress
Sprint 1 | Proyecto 1: Limpieza y resumen de datos en hojas de cálculo

## 📊 Introducción

En este proyecto asumí el rol de analista de datos junior para **VentaExpress**, una empresa de comercio electrónico en crecimiento que comercializa productos tecnológicos en México y Colombia.

Mi objetivo fue transformar un archivo de ventas crudo en un informe ejecutivo claro, organizado y útil para la toma de decisiones. Para lograrlo, limpié y preparé los datos, calculé métricas de ventas, construí visualizaciones y documenté los hallazgos principales.

El análisis se enfocó en las ventas del cuarto trimestre de 2024.

## 🏢 Contexto del negocio

VentaExpress comercializa productos de tecnología a través de su plataforma online. Entre los productos incluidos se encuentran:

- Laptops
- Teléfonos
- Auriculares
- Tablets

El dataset contiene ventas realizadas entre octubre y diciembre de 2024 en ciudades de México y Colombia.

Durante el proyecto trabajé con el archivo:

```text
ventas_q4_2024_raw.csv
```

La información original contenía problemas comunes de datos operativos:

- Formatos inconsistentes.
- Valores duplicados.
- Valores faltantes.
- Columnas desorganizadas.
- Información de producto que requería separación.
- Falta de documentación sobre la calidad de los datos.

## 🎯 Objetivos del proyecto

Con este proyecto busqué demostrar mi capacidad para:

- Explorar la estructura de un dataset.
- Identificar problemas de calidad.
- Limpiar y documentar transformaciones.
- Preparar datos para el análisis.
- Calcular métricas comerciales relevantes.
- Crear visualizaciones claras.
- Comunicar hallazgos mediante un informe ejecutivo.
- Aplicar validaciones de calidad de datos.

## 📁 Estructura del archivo

Organicé el archivo de trabajo en varias hojas para separar los datos originales, el proceso de limpieza, el análisis y la documentación.

| Hoja | Propósito |
| --- | --- |
| `Datos_Originales` | Conservé el dataset original sin modificarlo. |
| `Datos_Limpios` | Realicé la limpieza, estandarización y preparación de los datos. |
| `Análisis` | Calculé métricas, totales y comparaciones comerciales. |
| `Visualizaciones` | Construí los gráficos que responden a las preguntas de negocio. |
| `Informe_Ejecutivo` | Documenté los hallazgos, las recomendaciones y las validaciones de calidad. |

## 🧾 Estructura de los datos

El dataset original contiene información de ventas, ciudades, productos, precios y cantidades.

| Campo | Descripción |
| --- | --- |
| `Producto` | Nombre completo del producto vendido. |
| `Ciudad` | Ciudad donde se realizó la venta. |
| `Cantidad` | Número de unidades vendidas en la transacción. |
| `Precio unitario` | Precio individual de cada producto. |
| `Monto total` | Valor total de la transacción. |
| `Fecha` | Fecha de la venta. |

## 🔄 Proceso de trabajo

Organicé el análisis en cinco etapas principales.

| Etapa | Qué hice | Resultado esperado |
| :---: | --- | --- |
| 1 | Exploré y diagnostiqué el dataset. | Comprendí columnas, formatos y problemas de calidad. |
| 2 | Limpié y preparé los datos. | Construí una tabla consistente para el análisis. |
| 3 | Calculé métricas de negocio. | Obtuve ventas totales, promedios y comparaciones. |
| 4 | Creé visualizaciones. | Representé ventas por ciudad y evolución temporal. |
| 5 | Elaboré el informe ejecutivo. | Comuniqué hallazgos, recomendaciones y limitaciones. |

# 🔍 Parte 1: Exploración y diagnóstico inicial

Antes de modificar los datos, revisé su estructura general para identificar los problemas que podían afectar el análisis.

Durante esta etapa:

- Conservé una copia de los datos originales.
- Revisé los nombres de las columnas.
- Identifiqué valores ausentes.
- Revisé formatos de fecha.
- Revisé formatos monetarios.
- Detecté posibles duplicados.
- Verifiqué si existían inconsistencias en nombres de ciudades.
- Identifiqué la necesidad de dividir la columna `Producto`.

El objetivo fue preservar el archivo original y realizar el trabajo de limpieza en una hoja independiente.

# 🧹 Parte 2: Limpieza y preparación de datos

## Formato de columnas monetarias

Apliqué formato de moneda a las variables financieras principales.

| Columna | Formato aplicado |
| --- | --- |
| `Precio unitario` | Moneda con dos decimales. |
| `Monto total` | Moneda con dos decimales. |

El formato utilizado permite presentar los valores de manera consistente:

```text
$ 1.005,05
```

## Estandarización de ciudades

Para corregir diferencias de escritura en la columna `Ciudad`, creé una nueva variable llamada:

```text
Ciudad corregida
```

Apliqué una fórmula de normalización para conservar la primera letra en mayúscula y el resto en minúscula.

### Fórmula en inglés

```excel
=PROPER(Celda)
```

### Fórmula en español

```excel
=NOMPROPIO(Celda)
```

Este proceso permitió evitar que una misma ciudad se analizara como categorías diferentes por errores de mayúsculas o minúsculas.

## División de la información del producto

Conservé la columna original `Producto` y generé tres columnas adicionales:

| Producto original | Categoría | Tipo | Especificaciones |
| --- | --- | --- | --- |
| `Laptop-Gaming-16GB` | Laptop | Gaming | 16GB |

La separación de la información permitió analizar los productos con un mayor nivel de detalle.

Las nuevas columnas fueron:

- `Categoría`
- `Tipo`
- `Especificaciones`

## Manejo de valores ausentes

Revisé los valores faltantes en las columnas:

- `Precio unitario`
- `Monto total`

Cuando faltaba el precio unitario, utilicé la información disponible de cantidad y monto total para calcularlo:

```text
Precio unitario = Monto total / Cantidad
```

Cuando faltaba el monto total, lo calculé a partir de las variables disponibles:

```text
Monto total = Cantidad × Precio unitario
```

Documenté la cantidad de valores ausentes y el tratamiento aplicado dentro de `Informe_Ejecutivo`.

## Eliminación de duplicados

Revisé y eliminé duplicados completos mediante la herramienta de limpieza de datos.

El objetivo fue asegurar que una misma venta no afectara varias veces las métricas de ventas, cantidad o precio promedio.

## Validación posterior a la limpieza

Después de preparar la tabla, comprobé los siguientes criterios:

| Validación | Objetivo |
| --- | --- |
| Duplicados | Confirmar que no quedaran registros repetidos. |
| Tipos de datos | Verificar que fechas y montos fueran interpretados correctamente. |
| Ciudades | Confirmar una escritura consistente. |
| Valores ausentes | Validar que fueran calculados o documentados correctamente. |
| Productos | Confirmar que la separación de categoría, tipo y especificaciones fuera correcta. |

# 📈 Parte 3: Análisis y cálculo de métricas

En la hoja `Análisis`, calculé las métricas principales del trimestre.

## Métricas generales

| Métrica | Fórmula conceptual | Propósito |
| --- | --- | --- |
| Ventas totales | Suma de `Monto total`. | Medir el valor comercial del trimestre. |
| Venta promedio por transacción | Promedio de `Monto total`. | Conocer el valor medio de cada operación. |
| Número de transacciones | Conteo de ventas. | Medir el volumen de actividad comercial. |

### Fórmulas utilizadas

```excel
=SUM(rango_montos_totales)
```

```excel
=AVERAGE(rango_montos_totales)
```

```excel
=COUNT(rango_transacciones)
```

## Métricas segmentadas

También analicé el desempeño por categoría, ciudad y mes.

| Métrica | Pregunta que responde |
| --- | --- |
| Categoría más vendida por cantidad | ¿Qué tipo de producto tiene mayor volumen? |
| Ciudad con mayores ventas | ¿En qué mercado se concentra la facturación? |
| Mes con mayores ventas | ¿Cuál fue el mejor periodo comercial del trimestre? |
| Precio promedio por categoría | ¿Qué categorías presentan mayor valor unitario? |

Estas métricas permitieron pasar de una lectura global a una comparación por segmentos.

# 📊 Parte 4: Visualización de datos

En la hoja `Visualizaciones`, construí gráficos para comunicar los resultados de forma clara.

## Ventas por ciudad

Construí un gráfico de barras para comparar las ventas totales por ciudad.

| Elemento | Configuración |
| --- | --- |
| Eje X | Ciudad |
| Eje Y | Ventas totales |
| Objetivo | Comparar el desempeño comercial entre mercados. |

Este gráfico permitió responder:

- ¿En qué ciudad VentaExpress tiene mayor desempeño?
- ¿Existen diferencias importantes entre los mercados?
- ¿Dónde conviene investigar oportunidades comerciales?

## Evolución mensual de ventas

Construí un gráfico de líneas para analizar la evolución de las ventas mensuales.

| Elemento | Configuración |
| --- | --- |
| Eje X | Mes |
| Eje Y | Ventas totales |
| Objetivo | Identificar tendencias y variaciones temporales. |

Este gráfico permitió responder:

- ¿Cómo evolucionaron las ventas durante el trimestre?
- ¿Qué mes presentó el mejor desempeño?
- ¿Existen patrones estacionales visibles?

## Criterios de diseño

Para mantener una presentación profesional, apliqué los siguientes criterios:

- Títulos claros y descriptivos.
- Ejes correctamente etiquetados.
- Colores consistentes.
- Datos ordenados de manera lógica.
- Formato monetario en variables financieras.
- Visualizaciones enfocadas en preguntas de negocio.

# 📝 Parte 5: Informe ejecutivo

En la hoja `Informe_Ejecutivo`, organicé los resultados para responder preguntas de negocio de forma clara y accionable.

## Preguntas respondidas

| Pregunta | Métrica utilizada |
| --- | --- |
| ¿Cuál fue el producto más vendido por cantidad? | Suma de unidades por producto. |
| ¿Qué ciudad generó el mayor volumen de ventas? | Suma de ventas por ciudad. |
| ¿Cuál fue el precio promedio por categoría? | Promedio de precio unitario por categoría. |
| ¿Qué acción comercial se recomienda? | Interpretación derivada de los resultados anteriores. |

## Estructura de comunicación

Organicé las conclusiones mediante el enfoque:

> Contexto → Hallazgo → Implicación

| Componente | Contenido |
| --- | --- |
| Contexto | Expliqué el periodo, los datos y el segmento analizado. |
| Hallazgo | Presenté el resultado respaldado por una métrica o visualización. |
| Implicación | Propuse una acción comercial alineada con el hallazgo. |

### Ejemplo de comunicación

```text
Contexto:
Analicé las ventas del cuarto trimestre de 2024 por ciudad.

Hallazgo:
La ciudad con mayor volumen de ventas concentró una proporción relevante de la facturación total.

Implicación:
La Dirección Comercial puede priorizar inventario y campañas en ese mercado, después de contrastar el resultado con margen, disponibilidad y demanda.
```

# ✅ Parte 6: Quality Assurance — QA

Documenté validaciones de calidad para asegurar que las métricas, visualizaciones y conclusiones fueran trazables.

| Validación | Pregunta de control |
| --- | --- |
| Datos originales | ¿La hoja original se preservó sin modificaciones? |
| Formatos | ¿Fechas, precios y montos tienen el formato correcto? |
| Duplicados | ¿Existen registros repetidos? |
| Valores ausentes | ¿Los valores faltantes se trataron y documentaron correctamente? |
| Ciudades | ¿Las ciudades están estandarizadas? |
| Producto | ¿La información fue dividida correctamente en categoría, tipo y especificaciones? |
| Métricas | ¿Las fórmulas corresponden a la definición de cada KPI? |
| Gráficos | ¿Los títulos, ejes y formatos son claros? |
| Informe | ¿Las recomendaciones se derivan de los hallazgos? |

# 📦 Entregables

| Entregable | Contenido |
| --- | --- |
| Datos originales | Archivo de ventas sin modificaciones. |
| Datos limpios | Tabla preparada, estandarizada y enriquecida. |
| Análisis | Métricas generales y segmentadas. |
| Visualizaciones | Gráficos de ventas por ciudad y evolución mensual. |
| Informe ejecutivo | Hallazgos, recomendaciones y limitaciones. |
| Documentación QA | Validaciones y trazabilidad del proceso. |

# 💭 Reflexión final

Este proyecto representó mi primer flujo integral de análisis de datos en hojas de cálculo.

Durante el desarrollo:

- Exploré la estructura de los datos.
- Identifiqué problemas de calidad.
- Estandaricé formatos y categorías.
- Calculé métricas de negocio.
- Construí visualizaciones básicas.
- Organicé un informe ejecutivo.
- Documenté el proceso y las validaciones realizadas.

La principal enseñanza fue que una buena recomendación no depende únicamente de identificar la ciudad con más ventas o el producto más vendido. También requiere revisar la calidad de los datos, comprender el contexto y comunicar con claridad qué significan los resultados para el negocio.

Este proyecto fortaleció mi capacidad para transformar datos crudos en información útil para apoyar decisiones de inventario, presupuesto y estrategia comercial.
