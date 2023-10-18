

<p align="center">
  <img alt="Files Logo" src="https://www.mintransporte.gov.co/info/mintransporte/media/pubInt/thumbs/thpub_700x400_11343.jpg" width="450" />
  <h1 align=center style="color: #FF2403">Análisis de accidentes viales en vías controladas por el INVIAS en Colombia usando python 3.10 y powerBI.</h1>
</p>





## INTRODUCCIÓN:

El Instituto Nacional de Vías (INVIAS) es una entidad gubernamental en Colombia encargada de la planificación, construcción, mantenimiento y administración de la infraestructura vial del país. El INVIAS trabaja en estrecha colaboración con el gobierno colombiano y otras entidades para asegurar que las carreteras y la infraestructura vial estén en buenas condiciones, lo cual es esencial para el comercio, la movilidad y el desarrollo económico en Colombia.

## 1) Fase de "Ask" (Preguntar):

Objetivos del Análisis:

Identificar Tendencias y Patrones: Analizar la evolución de la accidentalidad a lo largo del tiempo y detectar patrones estacionales, geográficos u otros en la ocurrencia de accidentes.

Determinar Causas: Investigar las causas subyacentes de los accidentes, como factores climáticos, infraestructura vial, condiciones del tráfico y comportamiento del conductor, entre otros.

Preguntas:

* ¿Cuál es la tendencia de accidentes en las vías controladas por el INVIAS en los últimos años?
* ¿Cuáles son las principales causas de accidentes en estas vías?
* ¿Existen áreas geográficas con una mayor incidencia de accidentes?
* ¿Cómo ha evolucionado la gravedad de los accidentes a lo largo del tiempo?
  
Fase de Preparación:

## 2) Fase de "Prepare" (Preparar):

Fuente de Datos y Accesibilidad:

El conjunto de datos que se utilizará en este análisis fue recopilado por el Instituto Nacional de Vías (INVIAS). Los datos son de acceso público y pueden descargarse desde la página gubernamental de datos abiertos: [enlace a los datos](https://www.datos.gov.co/dataset/Accidentalidad-Vial-2017-2021/jj5k-4x95)

Limitaciones:

- Los datos del conjunto están desactualizados (2017 - 2021).
- No hay registros de los tipos de vehículos involucrados en cada muestra, lo que dificulta la evaluación de la relación entre el tipo de vehículo y la gravedad de los accidentes.

Variables Relevantes:

* `Territorial`: municipio o región en el que ocurrió el accidente.
* `Fecha_acc`: fecha en la cual sucedió el evento.
* `Día_semana_acc`: día de la semana en el cual sucedió el evento.
* `Condic_meteor`: condición meteorológica en la cual sucedió el evento.
* `Estado_super`: el estado de la superficie en el momento del evento.
* `Terreno`: tipo de terreno en el cual sucedió el evento.
* `Geometría_acc`: geometría de la carretera en la cual sucedió el evento.
* `N_heridos`: número de heridos del accidente.
* `N_muertos`: número de muertos del accidente.
* `N_víctimas`: víctimas totales del accidente.
* `Clase_accidente`: clase del accidente.
* `Causa_posible`: causa posible del accidente.

Registro del Proceso de ETL:

* Se formatearon los nombres de municipios para asegurar compatibilidad con el archivo GeoJSON usado para visualizar el mapa de Colombia.
* Se removieron las fechas que se salen del rango de fecha dado por los metadatos del conjunto de datos.
* Se aseguró la consistencia de los datos en la columna "dia_semana_acc," cambiando los valores "miercoles" a "Miércoles" y "sabado" a "Sábado."

## 3) Fase de "Analyze" (Analizar):

### Analisis estadístico:

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

En esta parte del análisis usaremos PowerBI para crear gráficos que nos permitan detectar posibles patrones y tendencias en los datos.

![dashboard](https://github.com/caozrich/analisis-accidentalidad-vias-invias/assets/34092193/cbd10cde-8668-4139-9933-17855936594e)

[Enlace al Dahboard](https://app.powerbi.com/view?r=eyJrIjoiNzk2MWQ2NGEtOGY3YS00ZjRhLWIxOTEtMzRiZDIwM2Y1NWRkIiwidCI6ImY1ODQzMWRmLTMyNDUtNGIyMi04NjQ1LTVmZmY5ODc0NjY3MiIsImMiOjR9)

Hallazgos:

* Los municipios de Córdoba, Antioquia y Boyacá presentan el mayor número de accidentes registrados.
* El año 2017 registró el mayor número de accidentes, alcanzando un pico de 1,574 en el segundo trimestre. Desde el cuarto trimestre de 2020, se observa una disminución gradual en la cantidad de accidentes.
* La tendencia en el número de muertes a causa de accidentes ha sido a la baja desde 2017.
* Las tres causas más comunes de accidentes son: no mantener la distancia de seguridad, exceso de velocidad e inexperiencia en el manejo.
* El tipo de accidente más frecuente es la colisión, seguido por el volcamiento.
* La causa que registra la mayor tasa de mortalidad es el atropello.
* La hora con mayor incidencia de accidentes es a las 16:00.
* El 15% de los accidentes ocurren en condiciones de lluvia.
* Un 39% de los accidentes suceden en curvas, mientras que el 57% ocurren en tramos rectos.
* La mayoría de los accidentes ocurren en terrenos montañosos.

## Conclusiones:

* Geografía de Accidentes: Los departamentos de Córdoba, Antioquia y Boyacá presentan una alta concentración de accidentes. Esto sugiere la necesidad de implementar medidas de seguridad vial específicas en estas regiones.

* Tendencia de Accidentes: A lo largo de los años, hemos observado un aumento en el número de accidentes hasta 2017, seguido de un descenso gradual. Esta tendencia podría estar relacionada con cambios en la infraestructura vial, políticas de seguridad vial o condiciones económicas.

* Disminución de Mortalidad: La tendencia a la baja en el número de muertes por accidentes es un indicador positivo de las medidas de seguridad vial implementadas en Colombia. Sin embargo, la seguridad vial sigue siendo un desafío.

* Causas de Accidentes: Las tres causas principales de accidentes (no mantener distancia de seguridad, exceso de velocidad e inexperiencia en el manejo) resaltan la importancia de la educación vial y la aplicación efectiva de las normativas de tráfico.

* Tipos de Accidentes: Las colisiones y los volcamientos son los tipos de accidentes más comunes. Esto podría indicar la necesidad de enfoques específicos para reducir estos tipos de incidentes.

* Causa Mortal: El atropello es la causa que presenta un mayor índice de mortalidad. Esto resalta la importancia de tomar medidas para proteger a los peatones y mejorar la seguridad en las vías.

##  Recomendaciones:

* Estrategias de Prevención: Implementar programas de educación vial y campañas de concienciación para abordar las causas comunes de accidentes, como el incumplimiento de la distancia de seguridad y el exceso de velocidad.

* Seguridad en Carreteras: Realizar evaluaciones y mejoras en la infraestructura vial, especialmente en áreas montañosas y curvas, para reducir la incidencia de accidentes.

* Seguridad en Condiciones Climáticas Adversas: Reforzar las medidas de seguridad en condiciones climáticas adversas, como la lluvia, para reducir los accidentes relacionados con estas condiciones.

* Vigilancia y Cumplimiento: Reforzar la vigilancia y la aplicación de las normativas de tráfico, especialmente en áreas con altas tasas de accidentes.

* Investigación de Accidentes: Continuar investigando a fondo los accidentes para identificar patrones y causas específicas, lo que permitirá desarrollar estrategias de prevención más efectivas.

Estas recomendaciones están destinadas a mejorar la seguridad vial en las carreteras controladas por el INVIAS en Colombia y reducir la incidencia de accidentes y sus consecuencias.



