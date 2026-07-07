# AirQuality Dashboard

Este directorio contiene el **export de un dashboard de Apache Superset** orientado al análisis y visualización de datos de calidad del aire. El paquete incluye la definición del dashboard, los datasets asociados y los charts necesarios para su importación y reutilización en otra instancia de Superset. [1][2][3]

## Objetivo

El dashboard permite monitorizar el estado actual de la calidad del aire y analizar su evolución histórica por estación y por contaminante. La solución está planteada como parte de una explotación analítica sobre datos urbanos reales, con foco en contaminantes como NO2, O3, PM10, PM2.5 y SO2. [2][3][4]

## Componentes incluidos

El export incorpora los siguientes elementos principales:

- **Dashboard**: `Calidad_del_Aire_1.yaml`. [1]
- **Dataset operativo**: `v_airqualityobserved_lastdata_ica_5.yaml`, orientado a estado actual e ICA. [2]
- **Dataset histórico**: `airqualityobserved_1.yaml`, orientado a análisis temporal. [3]
- **Charts exportados**: mapas, tablas, gauges, series temporales y visualizaciones comparativas por estación. [5][6][7][4]

## Estructura del dashboard

La estructura actual del dashboard se organiza en pestañas **General**, **Histórico** y **Predicción**. En el export disponible, la pestaña **Predicción** figura en la estructura del dashboard, pero no contiene charts configurados. [1]

### General

La pestaña General resume el estado actual del ICA y facilita una visión rápida del comportamiento de las estaciones:

- Indicador de **media ICA actual**. [8]
- Indicador de **máximo ICA actual**. [9]
- Visualización de **top estaciones por ICA**. [10]
- Mapa operativo con estaciones y su distribución espacial. [5][11]

### Histórico

La pestaña Histórico concentra el análisis temporal y la exploración por contaminante:

- Serie temporal de **evolución de la concentración de contaminantes**. [4][12]
- Mapa de estaciones para análisis espacial histórico. [11]
- Mapa de calor estación/hora para NO2. [13]
- Indicadores gauge de **mínimo**, **media** y **máximo** de NO2. [14][15][16]
- Comparativa de **máximo, media y mínimo por estación (NO2)**. [17]
- Navegación por pestañas para contaminantes como NO2, O3, PM10, PM2.5 y SO2. [18]

## Tipos de visualización utilizados

En este dashboard se emplean varios charts nativos de Apache Superset:

- **Big Number / KPI** para indicadores agregados del ICA. [8][9]
- **Bar Chart** para ranking de estaciones. [10]
- **Deck/Map chart** para representación espacial de estaciones. [5][11]
- **Time-series line chart** para evolución temporal de contaminantes. [4][12]
- **Heatmap** para patrones estación/hora. [13]
- **Gauge chart** para indicadores sintéticos por contaminante. [14][15][16]
- **Gráfico comparativo por estación** para máximo, media y mínimo. [17]

## Capturas de pantalla

Las siguientes capturas deben ubicarse en la ruta `./airquality/screenShots` dentro del repositorio.

### Vista general

#### Media ICA actual



#### Máximo ICA actual



#### Top estaciones por ICA



### Vista histórica

#### Evolución de la concentración de contaminantes



#### Mapa de estaciones



#### Mapa de calor por estación/hora



#### Navegación por contaminantes



### Indicadores NO2

#### Mínimo NO2



#### Media NO2



#### Máximo NO2



#### Máximo, media y mínimo por estación (NO2)



## Filtros e interacción

El dashboard define filtros nativos de estación y fecha, además de interacción entre gráficos mediante **cross-filtering**. Esto permite analizar tanto el estado actual como el histórico desde una misma estructura de navegación. [1]

## Uso del repositorio

La estructura recomendada para este módulo del repositorio es:

```text
README.md
airquality/
├── charts/
├── dashboards
├── databases
├── datasets
├── screenShots/
└── metadata.yaml 
```

## Importación

Para restaurar este dashboard en otra instancia de Apache Superset, es necesario importar de forma coherente el dashboard, sus datasets y los charts asociados, manteniendo la correspondencia entre identificadores y fuentes de datos. [1][2][3]

## Observaciones técnicas

Desde el punto de vista de mantenibilidad, este enfoque facilita el versionado del trabajo analítico y la trazabilidad de cambios sobre dashboards, datasets y visualizaciones. Además, resulta especialmente adecuado para un TFM, ya que documenta de forma reproducible la explotación de datos urbanos reales mediante Superset sobre un backend analítico derivado de NGSI v2 y FIWARE. [19][20]