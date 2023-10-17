<p align="center">
  <img alt="Files Logo" src="https://www.mintransporte.gov.co/info/mintransporte/media/pubInt/thumbs/thpub_700x400_11343.jpg" width="450" />
  <h1 align=center style="color: #FF2403">Proyecto de análisis de accidentes aéreos por Richard Libreros</h1>
</p>

# analisis-accidentalidad-vias-invias

Análisis de accidentes viales en vías controladas por el INVIAS en Colombia usando python 3.10 y powerBI.

## INTRODUCCIÓN:

El Instituto Nacional de Vías (INVIAS) es una entidad gubernamental en Colombia encargada de la planificación, construcción, mantenimiento y administración de la infraestructura vial del país. El INVIAS trabaja en estrecha colaboración con el gobierno colombiano y otras entidades para asegurar que las carreteras y la infraestructura vial estén en buenas condiciones, lo cual es esencial para el comercio, la movilidad y el desarrollo económico en Colombia.

## 1) Fase de "Ask" (Preguntar):

Objetivos del Análisis:

Identificar Tendencias y Patrones: Analizar la evolución de la accidentalidad a lo largo del tiempo y detectar patrones estacionales, geográficos u otros en la ocurrencia de accidentes.

Determinar Causas: Investigar las causas subyacentes de los accidentes, como factores climáticos, infraestructura vial, condiciones del tráfico y comportamiento del conductor, entre otros.

Preguntas:

¿Cuál es la tendencia de accidentes en las vías controladas por el INVIAS en los últimos años?
¿Cuáles son las principales causas de accidentes en estas vías?
¿Existen áreas geográficas con una mayor incidencia de accidentes?
¿Cómo ha evolucionado la gravedad de los accidentes a lo largo del tiempo?
Fase de Preparación:

## 2) Fase de "Prepare" (Preparar):

Fuente de Datos y Accesibilidad:

El conjunto de datos que se utilizará en este análisis fue recopilado por el Instituto Nacional de Vías (INVIAS). Los datos son de acceso público y pueden descargarse desde la página gubernamental de datos abiertos: enlace a los datos.

Limitaciones:

- Los datos del conjunto están desactualizados (2017 - 2021).
- No hay registros de los tipos de vehículos involucrados en cada muestra, lo que dificulta la evaluación de la relación entre el tipo de vehículo y la gravedad de los accidentes.

Variables Relevantes:

Territorial: municipio o región en el que ocurrió el accidente.
Fecha_acc: fecha en la cual sucedió el evento.
Día_semana_acc: día de la semana en el cual sucedió el evento.
Condic_meteor: condición meteorológica en la cual sucedió el evento.
Estado_super: el estado de la superficie en el momento del evento.
Terreno: tipo de terreno en el cual sucedió el evento.
Geometría_acc: geometría de la carretera en la cual sucedió el evento.
N_heridos: número de heridos del accidente.
N_muertos: número de muertos del accidente.
N_víctimas: víctimas totales del accidente.
Clase_accidente: clase del accidente.
Causa_posible: causa posible del accidente.

Registro del Proceso de ETL:

* Se formatearon los nombres de municipios para asegurar compatibilidad con el archivo GeoJSON usado para visualizar el mapa de Colombia.
* Se removieron las fechas que se salen del rango de fecha dado por los metadatos del conjunto de datos.
* Se aseguró la consistencia de los datos en la columna "dia_semana_acc," cambiando los valores "miercoles" a "Miércoles" y "sabado" a "Sábado."

## 3) Fase de "Analyze" (Analizar):

analisis estadistico:

|          | n_heridos | n_muertos | n_victimas |
|----------|-----------|-----------|------------|
| count    | 18553.0   | 18553.0   | 11492.0    |
| mean     | 0.598609  | 0.10823   | 1.185607   |
| std      | 1.284167  | 0.37441   | 2.504110   |
| min      | 0.0       | 0.0       | 0.0        |
| 25%      | 0.0       | 0.0       | 0.0        |
| 50%      | 0.0       | 0.0       | 1.0        |
| 75%      | 1.0       | 0.0       | 1.0        |
| max      | 35.0      | 9.0       | 123.0      |


### Hallazgos

#### Heridos:

- El promedio de heridos por accidente es aproximadamente 0.60, lo que sugiere que, en promedio, la mayoría de los accidentes involucran a menos de una persona herida.
- El valor máximo de 35 heridos en un solo accidente indica que hay casos extremos con un gran número de heridos, aunque son raros.
- El 75% de los accidentes tienen 1 o menos heridos.

#### Muertos:

- El promedio de muertes por accidente es de aproximadamente 0.11, lo que sugiere que, en promedio, la mayoría de los accidentes no resultan en muertes.
- El valor máximo de 9 muertes en un solo accidente indica que hay casos extremos con un número significativo de muertes, aunque también son raros.
- El 75% de los accidentes no tienen muertes.

#### Victimas totales:

- El promedio de víctimas (heridos + muertos) por accidente es de aproximadamente 1.19, lo que sugiere que, en promedio, la mayoría de los accidentes involucran a menos de dos víctimas.
- El valor máximo de 123 víctimas en un solo accidente indica que hay casos extremos con un gran número de víctimas, pero son muy raros.
- El 75% de los accidentes involucran 1 o menos víctimas.


## 3) Fase de "Visualize" (Visualizar):






