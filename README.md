# Urban Context Dashboards

Este repositorio agrupa varios módulos de visualización basados en Apache Superset
para el análisis de datos urbanos del Ayuntamiento de Madrid. Cada módulo corresponde
a un ámbito específico del contexto urbano y se distribuye en un directorio propio,
manteniendo una estructura homogénea orientada a facilitar la importación, versión
y despliegue de los dashboards.

## Módulos incluidos

Actualmente se contemplan los siguientes módulos de análisis:

- `airquality/`: calidad del aire (contaminantes, ICA, series temporales, mapas).
- `noise/`: niveles de ruido ambiental y su evolución temporal.
- `occupancy/`: aforo y ocupación de espacios públicos o equipamientos.
- `wastewater/`: indicadores de aguas residuales asociados a actividad urbana.
- `energy/`: consumo de energía en edificios residenciales.

Cada módulo contiene el export de uno o varios dashboards de Apache Superset,
junto con los datasets, charts y conexiones a bases de datos necesarias para
su correcta importación en otra instancia de Superset.

## Estructura de cada módulo

Todos los módulos comparten la misma estructura de directorios, derivada del
formato de export de Superset (`charts`, `dashboards`, `databases`, `datasets`
y `metadata.yaml`).

El patrón general es:

```text
<modulo>/
├── README.md
├── charts/
├── dashboards/
├── databases/
├── datasets/
├── screenShots/
└── metadata.yaml
```

Por ejemplo, para el dashboard de calidad del aire:

```text
airquality/
├── README.md
├── charts/
├── dashboards/
├── databases/
├── datasets/
├── screenShots/
└── metadata.yaml
```

Y análogamente para ruido, aforo, aguas residuales y energía:

```text
noise/
occupancy/
wastewater/
energy/
```

Cada directorio incluye un `metadata.yaml` que describe el export y permite
importar el conjunto en Superset (dashboards, charts, datasets y bases de datos)
como un bloque coherente.


Se recomienda que cada módulo (`airquality`, `noise`, `occupancy`, `wastewater`,
`energy`) disponga de su propio `README.md` explicando:

- objetivo del dashboard,
- fuentes de datos utilizadas,
- principales visualizaciones,
- y pasos de importación en Superset.

## Capturas de pantalla

Las capturas de pantalla de los dashboards se almacenan en el subdirectorio
`screenShots/` de cada módulo, y se referencian desde los respectivos `README.md`
para facilitar su visualización directa en GitHub.

Por ejemplo, para el módulo de calidad del aire:

```text
airquality/
├── README.md
└── screenShots/
    ├── Datos%20generales%20-%20media%20ICA%20actual.png
    ├── Datos%20generales%20-%20máximo%20ICA%20actual.png
    └── ...
```

## Importación en Apache Superset

Los directorios de cada módulo pueden utilizarse como origen (`source_dir`) para
procesos de importación automatizados (CLI, Terraform, pipelines de CI/CD),
importando conjuntamente dashboards, charts, datasets y bases de datos.

A alto nivel, el flujo de uso típico es:

1. Clonar este repositorio en el entorno donde se ejecuta Superset.
2. Seleccionar el módulo que se desea importar (`airquality/`, `noise/`, etc.).
3. Ejecutar el comando o pipeline de importación apuntando al directorio del módulo.
4. Verificar que los dashboards aparecen correctamente en Superset y enlazan con
   las fuentes de datos urbanas configuradas (FIWARE, NGSI v2, bases de datos
   analíticas, etc.).

Este enfoque facilita el versionado de los dashboards urbanos y su despliegue
reproducible en entornos de desarrollo, preproducción y producción.