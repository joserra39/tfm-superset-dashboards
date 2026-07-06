# AirQuality Dashboard

Este directorio contiene el **export de un dashboard de Apache Superset** orientado a la visualización y análisis de datos de calidad del aire procedentes de sensores urbanos. El objetivo del paquete es permitir la reutilización, versionado e importación del dashboard en otros entornos Superset, manteniendo tanto la configuración del panel como la definición de los datasets y charts asociados. [1][2][3]

## Contenido del export

El export incluye, al menos, los siguientes componentes funcionales:

- **Dashboard principal** `Calidad_del_Aire_1.yaml`, que define la estructura visual del cuadro de mandos, la disposición de los charts y la configuración de filtros nativos. [1]
- **Dataset agregado de último estado** `v_airqualityobserved_lastdata_ica_5.yaml`, pensado para visualización operativa y estado actual del ICA por estación. [2]
- **Dataset histórico** `airqualityobserved_1.yaml`, utilizado para análisis temporal y comparativa de contaminantes. [3]
- **Charts individuales** exportados como YAML, reutilizables o importables de forma independiente en Superset. [4][5][6][7]

## Estructura funcional del dashboard

El dashboard se organiza en varias pestañas. En el estado actual del export se identifican las pestañas **General**, **Histórico** y una pestaña reservada para **Predicción**, aunque esta última no contiene charts configurados en el export adjunto. [1]

### Pestaña General

La pestaña **General** agrupa una vista operativa del estado actual de la calidad del aire:

- **Mapa ICA**: visualización geográfica tipo `deck_scatter` sobre coordenadas latitud/longitud, con tooltips que muestran estación, fecha observada y categoría ICA general. [4]
- **Tabla ICA**: tabla agregada con estación, nivel ICA y categoría ICA, incluyendo formato condicional por severidad. [5]

### Pestaña Histórico

La pestaña **Histórico** concentra charts orientados al análisis temporal:

- **Contaminantes**: serie temporal `echarts_timeseries_line` con las métricas SO2, NO2, PM2.5, PM10 y O3 sobre `dateobserved`. [7]
- **Mapa**: existe un chart de mapa histórico referenciado por el dashboard (`chartId: 2`), aunque su YAML específico no se ha descrito en detalle en este resumen. [1]
- **Dióxido de Nitrógeno (NO2)**: tabla agregada con media, mínimo y máximo de NO2, acompañada de formato condicional para distinguir rangos de calidad. [6]

### Filtros y navegación

El dashboard define filtros nativos de:

- **Estación** (`entityid`), disponible como selector multiselección. [1]
- **Fecha**, aplicado principalmente sobre los charts históricos. [1]
- **Cross-filters**, habilitados para interacción entre varios charts del dashboard. [1]

## Datasets utilizados

### `v_airqualityobserved_lastdata_ica`

Este dataset representa una vista de **último dato disponible por estación** y contiene atributos preparados para explotación operativa, como `nivel_ica_general`, `categoria_ica_general`, `latitude`, `longitude`, `address` y valores de contaminantes principales como PM10, PM2.5, NO2, SO2 y O3. [2]

### `airqualityobserved`

Este dataset corresponde al histórico de observaciones y contiene series temporales con `recvtime` y `dateobserved`, identificador de entidad (`entityid`), coordenadas derivadas, dirección y un conjunto más amplio de contaminantes, incluyendo NO2, SO2, CO, NOx, PM10, PM2.5, O3 y otros compuestos adicionales. [3]

## Tipos de visualización presentes

En este dashboard se identifican varios tipos de visualización nativos de Apache Superset:

- **Table** para resúmenes operativos y analíticos. [5][6]
- **Deck Scatter** para representación geográfica de estaciones. [4]
- **ECharts Time-series Line** para evolución temporal de contaminantes. [7]
- **Filtros nativos** y configuración de interacción entre visualizaciones. [1]

## Uso en repositorio

Este directorio puede tratarse como un módulo independiente del repositorio de dashboards. La estructura recomendada es conservar:

- el YAML del dashboard;
- los YAML de datasets;
- los YAML de charts;
- y este `README.md` como documentación técnica mínima del contenido exportado. [1][2][3]

Para restaurar el dashboard en otra instancia de Superset, debe importarse el conjunto completo respetando la correspondencia entre dashboard, datasets y charts. [1]

## Capturas de pantalla

No se han podido extraer **capturas reales** del dashboard únicamente a partir de los YAML, ya que los archivos describen configuración, pero no contienen renderizados visuales. [1][4][7]

Se recomienda añadir en este apartado, una vez desplegado el dashboard en Superset, al menos estas capturas:

1. Vista general de la pestaña **General** con mapa ICA y tabla resumen.
2. Vista de la pestaña **Histórico** con serie temporal de contaminantes.
3. Vista del chart de **NO2** con formato condicional.
4. Vista del filtro de estación y rango temporal aplicado.

Ejemplo de bloque a completar en el repositorio:

```md
## Capturas

### General
![Vista general](./screenshots/airquality-general.png)

### Histórico
![Vista histórica](./screenshots/airquality-historico.png)

### NO2
![Tabla NO2](./screenshots/airquality-no2.png)
```

## Observaciones

Desde el punto de vista de mantenimiento, este export es útil para versionar la configuración analítica del dashboard junto con el resto de componentes del proyecto. Además, encaja bien en un flujo de trabajo reproducible para el TFM, ya que permite documentar qué visualizaciones se han definido sobre datasets FIWARE/NGSI v2 transformados para explotación en Superset. [8][9]