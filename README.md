# AirQuality Dashboard

Este directorio contiene el **export de un dashboard de Apache Superset** orientado al análisis y visualización de datos de calidad del aire. El paquete incluye la definición del dashboard, los datasets asociados y los charts necesarios para su importación y reutilización en otra instancia de Superset.

## Objetivo

El dashboard permite monitorizar el estado actual de la calidad del aire y analizar su evolución histórica por estación y por contaminante. La solución está planteada como parte de una explotación analítica sobre datos urbanos reales, con foco en contaminantes como NO2, O3, PM10, PM2.5 y SO2.

## Componentes incluidos

El export incorpora los siguientes elementos principales:

- **Dashboard**: `Calidad_del_Aire_1.yaml`.
- **Dataset operativo**: `v_airqualityobserved_lastdata_ica_5.yaml`, orientado a estado actual e ICA.
- **Dataset histórico**: `airqualityobserved_1.yaml`, orientado a análisis temporal.
- **Charts exportados**: mapas, tablas, gauges, series temporales y visualizaciones comparativas por estación.

## Estructura del dashboard

La estructura actual del dashboard se organiza en pestañas **General**, **Histórico** y **Predicción**. En el export disponible, la pestaña **Predicción** figura en la estructura del dashboard, pero no contiene charts configurados.

### General

La pestaña General resume el estado actual del ICA y facilita una visión rápida del comportamiento de las estaciones:

- Indicador de **media ICA actual**.
- Indicador de **máximo ICA actual**.
- Visualización de **top estaciones por ICA**. 
- Mapa operativo con estaciones y su distribución espacial.

### Histórico

La pestaña Histórico concentra el análisis temporal y la exploración por contaminante:

- Serie temporal de **evolución de la concentración de contaminantes**.
- Mapa de estaciones para análisis espacial histórico. 
- Mapa de calor estación/hora para NO2.
- Indicadores gauge de **mínimo**, **media** y **máximo** de NO2.
- Comparativa de **máximo, media y mínimo por estación (NO2)**.
- Navegación por pestañas para contaminantes como NO2, O3, PM10, PM2.5 y SO2.

## Tipos de visualización utilizados

En este dashboard se emplean varios charts nativos de Apache Superset:

- **Big Number / KPI** para indicadores agregados del ICA.
- **Bar Chart** para ranking de estaciones.
- **Deck/Map chart** para representación espacial de estaciones.
- **Time-series line chart** para evolución temporal de contaminantes.
- **Heatmap** para patrones estación/hora.
- **Gauge chart** para indicadores sintéticos por contaminante.
- **Gráfico comparativo por estación** para máximo, media y mínimo.

## Capturas de pantalla

### Vista general

#### Media ICA actual

![Media ICA actual](airquality/screenshots/Datos%20generales%20-%20media%20ICA%20actual.png)

#### Máximo ICA actual

![Máximo ICA actual](airquality/screenshots/Datos%20generales%20-%20máximo%20ICA%20actual.png)

#### Top estaciones por ICA

![Top estaciones por ICA](airquality/screenshots/Datos%20generales%20-%20Top%20estaciones%20por%20ICA.png)

### Vista histórica

#### Evolución de la concentración de contaminantes

![Evolución de la concentración de contaminantes](airquality/screenshots/Datos%20históricos%20-%20evolución%20de%20la%20concentración%20de%20contaminantes.png)

#### Mapa de estaciones

![Mapa de estaciones](airquality/screenshots/Datos%20históricos%20-%20mapa%20estaciones.png)

#### Mapa de calor por estación/hora (NO2)

![Mapa de calor por estación/hora (NO2)](airquality/screenshots/Datos%20históricos%20-%20Mapa%20de%20calor%20por%20estación.png)

#### Navegación por contaminantes

![Tabs de contaminantes](airquality/screenshots/Datos%20históricos%20-%20tabs.png)

### Indicadores NO2

#### Mínimo NO2

![Mínimo NO2](airquality/screenshots/Datos%20históricos%20-%20mínimo%20NO2.png)

#### Media NO2

![Media NO2](airquality/screenshots/Datos%20históricos%20-%20media%20NO2.png)

#### Máximo NO2

![Máximo NO2](airquality/screenshots/Datos%20históricos%20-%20máximo%20NO2.png)

#### Máximo, media y mínimo por estación (NO2)

![Máximo, media y mínimo por estación (NO2)](airquality/screenshots/Datos%20históricos%20-%20Máximo%20media%20minimo%20por%20estación.png)


## Filtros e interacción

El dashboard define filtros nativos de estación y fecha, además de interacción entre gráficos mediante **cross-filtering**. Esto permite analizar tanto el estado actual como el histórico desde una misma estructura de navegación.

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

Para restaurar este dashboard en otra instancia de Apache Superset, es necesario importar de forma coherente el dashboard, sus datasets y los charts asociados, manteniendo la correspondencia entre identificadores y fuentes de datos.

## Observaciones técnicas

Desde el punto de vista de mantenibilidad, este enfoque facilita el versionado del trabajo analítico y la trazabilidad de cambios sobre dashboards, datasets y visualizaciones. Además, resulta especialmente adecuado para un TFM, ya que documenta de forma reproducible la explotación de datos urbanos reales mediante Superset sobre un backend analítico derivado de NGSI v2 y FIWARE. [19][20]
