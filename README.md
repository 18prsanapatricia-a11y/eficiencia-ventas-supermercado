Eficiencia de ventas por departamento — Supermercado
Análisis del desempeño de ventas por departamento de una cadena de supermercados durante 2012, realizado íntegramente en Google Sheets. El proyecto integra limpieza de datos, unión de múltiples tablas, tablas dinámicas y un dashboard ejecutivo interactivo.
---
Contexto del problema
La empresa quería entender no solo qué departamentos venden más, sino qué tan eficiente es cada uno respecto al espacio físico que ocupa dentro de la tienda. Vender mucho en un departamento grande no es lo mismo que vender lo mismo en uno pequeño: la pregunta de negocio real era dónde está mejor aprovechado cada metro cuadrado.
El objetivo fue determinar el porcentaje de participación de ventas por departamento en 2012 y calcular su eficiencia de ventas por metro cuadrado, para identificar qué departamentos generan más valor por el espacio que ocupan.
---
Herramientas utilizadas
Herramienta	Uso en el proyecto
Google Sheets	Entorno principal de trabajo
`VLOOKUP` / `BUSCARV`	Unión de catálogos de departamento y tienda con los datos de ventas
Tablas dinámicas (Pivot tables)	Cálculo de ventas por m² y participación por departamento
`COUNTIF` / `CONTAR.SI`	Validaciones de calidad de datos (QA)
Gráficos nativos de Sheets	Dashboard ejecutivo con visualización de KPIs
---
Estructura del archivo
Hoja	Descripción	Tipo
`raw_ventas`	Datos originales de ventas semanales por tienda y departamento	Datos crudos
`raw_departamento`	Catálogo de departamentos con sus nombres	Tabla de referencia
`raw_tiendas`	Catálogo de tiendas con tipo (A/B) y tamaño en m²	Tabla de referencia
`clean_ventas`	Datos depurados, ya unidos con los catálogos de departamento y tienda	Datos limpios
`Pivot`	Tablas dinámicas: ventas por m² y participación por departamento	Análisis
`Dashboard`	KPIs y visualizaciones para presentación ejecutiva	Presentación
`Resumen`	Hallazgos principales del análisis	Conclusiones
---
Metodología
Unión de tablas. Los datos de ventas venían separados del catálogo de departamentos y del catálogo de tiendas (con su tamaño en m²). Se unificó todo en `clean_ventas` mediante búsquedas cruzadas, agregando el nombre del departamento y el tamaño de tienda a cada registro de venta.
Estandarización. Se normalizó el formato de semana y se aseguró que cada venta quedara asociada a un departamento con nombre (no solo número).
Validaciones de calidad (QA). Antes de analizar, se verificó: ausencia de tiendas sin departamento asignado, ausencia de departamentos sin nombre catalogado, presencia de ventas negativas o nulas, y tamaños en m² igual a cero. Cada chequeo se documentó con su fórmula y resultado.
Tablas dinámicas. Se construyeron pivots para calcular dos KPIs clave por departamento: ventas por metro cuadrado y porcentaje de participación sobre el total de ventas del año.
Dashboard ejecutivo. Los resultados se presentaron en una hoja dedicada con visualizaciones pensadas para una audiencia no técnica (gerencia).
---
KPIs calculados
KPI	Fórmula	Interpretación
Ventas por m²	Ventas totales ÷ tamaño de tienda	A mayor cifra, mayor eficiencia de venta por espacio ocupado
% de participación	Ventas del departamento ÷ ventas totales	A mayor cifra, mayor peso del departamento en las ventas de 2012
---
Alcance de los datos
El análisis integra 95,880 registros de ventas semanales, correspondientes a 999 tiendas de tipo A y B, distribuidas en 15 departamentos (Snacks y Bebidas, Despensa y Básicos, Electrónica de Consumo, Ropa, Comida Fresca, entre otros).
Hallazgos principales
Pregunta de negocio	Insight	Implicación
¿Qué departamentos fueron más eficientes en 2012?	"Despensa y Básicos", "Comida Fresca" y "Artículos del Hogar y Papel" concentran el 36.43% de las ventas totales del año	Expandir y priorizar espacio para estos departamentos en 2013
¿Qué departamentos tienen menor venta por m²?	"Oficina, Escuela y Manualidades" y "Jardín y Vida al Aire Libre" están 62.97% por debajo del promedio de eficiencia por metro cuadrado	Evaluar reducción de espacio físico y reforzar venta en línea
¿Qué departamentos representan menor % de ventas?	Los mismos dos departamentos representan solo el 2.53% de las ventas totales del año	Revisar canales de difusión y promoción de estas categorías
Hallazgos de calidad de datos (QA)
Durante la validación se identificaron dos observaciones relevantes que se documentaron en lugar de ocultarse:
Una categoría sin nombre de departamento representa cerca del 5.27% de las ventas totales, lo que se marcó como pendiente de investigar con el área de origen de los datos.
Se detectaron 27 registros con ventas negativas, que se decidió mantener en el análisis bajo el supuesto de que corresponden a devoluciones de clientes, en lugar de eliminarlos sin justificación.
---
Archivos del repositorio
```
├── data/
│   └── ventas_supermercado_departamentos.xlsx   # Libro completo con todas las hojas
├── docs/
│   └── capturas/                           # Dashboard exportado como imagen
└── README.md
```
---
Habilidades demostradas
Integración de múltiples fuentes de datos mediante búsquedas cruzadas (VLOOKUP)
Validación sistemática de calidad de datos antes del análisis (QA)
Construcción de tablas dinámicas para métricas de negocio
Cálculo de KPIs de eficiencia normalizados por variable física (espacio en m²)
Diseño de un dashboard ejecutivo orientado a la toma de decisiones
Documentación transparente de anomalías en los datos, en vez de omitirlas
