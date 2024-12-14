# **Análisis de Calidad Inicial en Datos de Secuenciación: Uso de FastQC**

El análisis de calidad inicial de los datos de secuenciación es una etapa fundamental en cualquier proyecto de NGS (Next Generation Sequencing), ya que permite identificar rápidamente posibles problemas en las lecturas obtenidas antes de realizar análisis más profundos. La calidad de los datos afecta directamente a la precisión de los resultados finales, por lo que es crucial evaluar si las lecturas generadas son lo suficientemente buenas para ser utilizadas en los pasos posteriores del análisis.

Una de las herramientas más utilizadas para realizar este análisis inicial es **FastQC**. FastQC proporciona una evaluación detallada de los datos de secuenciación, permitiendo identificar posibles errores o artefactos antes de que se proceda con el procesamiento de las lecturas.

## **¿Qué es FastQC?**
FastQC es una herramienta de software ampliamente utilizada para la evaluación de la calidad de las lecturas generadas por las plataformas de secuenciación. Permite examinar diversos aspectos de la calidad de los datos, desde la calidad de las bases individuales hasta la presencia de contaminantes o secuencias adaptadoras.

## **Instalación y Ejecución de FastQC**
- **Instalación**: FastQC puede instalarse en diferentes sistemas operativos (Linux, Windows, macOS) y está disponible de forma gratuita. En sistemas basados en Unix, puede instalarse fácilmente a través de gestores de paquetes como `apt` o `brew`.
  
- **Ejecución**: FastQC se ejecuta desde la línea de comandos. Para analizar un archivo de secuenciación (generalmente en formato FASTQ), se utiliza el siguiente comando básico:
  
  ```
  fastqc archivo.fastq
  ```

  Si se tienen múltiples archivos, se pueden analizar en lote utilizando el comodín `*` o especificando una lista de archivos.
  
  ```
  fastqc *.fastq
  ```

- **Salida**: El resultado es un archivo HTML y un archivo de texto que contienen los informes de calidad. Estos informes contienen gráficos visuales y métricas que facilitan la interpretación de la calidad de las lecturas.

## **Evaluación de los Informes de FastQC**

El informe generado por FastQC incluye varios análisis clave que proporcionan información sobre la calidad de las lecturas:

#### **Calidad de las Bases**
FastQC evalúa la calidad de las bases a lo largo de las lecturas. Cada base es evaluada con una puntuación de calidad, generalmente representada por un valor Phred (Puntuación de Calidad). Las lecturas de alta calidad deben tener una puntuación de calidad consistente y alta (generalmente superior a 30), mientras que una puntuación baja indica problemas en la secuenciación. 

- **Gráfico de Calidad de las Bases**: El gráfico muestra cómo varía la calidad de las bases a medida que avanza la secuencia. Una buena secuenciación debería tener puntuaciones altas al principio y al final de la lectura. Sin embargo, las puntuaciones pueden bajar al final debido a la degradación de las señales de secuenciación, lo cual es esperado.

#### **Conteo de Secuencias y Tamaño de Lectura**
FastQC proporciona información sobre el número total de secuencias en el archivo, lo cual es útil para confirmar que no hay una pérdida inesperada de datos. Además, el análisis del tamaño de las lecturas puede indicar si las lecturas tienen una longitud uniforme o si existen fragmentos demasiado cortos o largos que podrían necesitar filtrado.

- **Gráfico de Tamaño de las Lecturas**: Este gráfico muestra la distribución de las longitudes de las lecturas. Es importante que las lecturas tengan una longitud consistente para garantizar la calidad del análisis downstream. Lecturas extremadamente cortas pueden ser descartadas si se considera que no aportan suficiente información.

#### **Contaminación y Secuencias Adaptadoras**
En las secuencias de NGS, es común que se utilicen adaptadores durante la preparación de la muestra, los cuales ayudan a la secuenciación de los fragmentos de ADN. FastQC puede identificar la presencia de estos adaptadores en las lecturas.

- **Gráfico de Secuencias Adaptadoras**: Este gráfico muestra la cantidad de lecturas que contienen secuencias adaptadoras. La presencia de adaptadores no eliminados es una señal de que se deben realizar pasos adicionales de filtrado para limpiar las lecturas antes de su uso en el análisis.

#### **Distribución de las Secuencias por Posición**
FastQC también analiza cómo se distribuyen las secuencias a lo largo de la secuenciación. En algunas plataformas de secuenciación, se pueden generar sesgos en ciertas posiciones de las lecturas, lo que puede indicar problemas con la instrumentación o el proceso de preparación de la muestra.

- **Gráfico de Distribución de las Secuencias**: Este gráfico muestra cómo se distribuyen las lecturas a lo largo del proceso de secuenciación. Un sesgo en la distribución puede reflejar problemas técnicos o con la preparación de la biblioteca.

#### **Duplicados y Contaminantes**
FastQC también evalúa la presencia de lecturas duplicadas, que pueden ocurrir si algunas lecturas son generadas más de una vez durante el proceso de secuenciación. Además, puede detectar secuencias de origen no deseado, como contaminantes de otras especies.

- **Gráfico de Duplicados**: Este gráfico muestra la proporción de lecturas duplicadas. Un número elevado de duplicados puede indicar problemas en la preparación de la muestra o en la secuenciación.

- **Gráfico de Contaminación**: Este gráfico muestra la cantidad de secuencias que no pertenecen al organismo de interés. Las lecturas contaminantes pueden distorsionar el análisis y deben ser eliminadas antes de continuar.

##### **3.6. GC Content**
La distribución de contenido de GC en las lecturas es otra métrica importante. Un sesgo en el contenido de GC puede ser indicativo de problemas en la preparación de la muestra o en el proceso de secuenciación.

- **Gráfico de Contenido de GC**: Este gráfico muestra cómo se distribuye el contenido de GC a lo largo de las lecturas. Un sesgo en este gráfico puede indicar problemas con la calidad de la secuenciación o con la preparación de la biblioteca.

## **Cómo Interpretar los Resultados de FastQC**

FastQC clasifica los resultados en diferentes niveles de calidad:
- **Verde**: Los resultados son aceptables, lo que significa que no se detectaron problemas importantes.
- **Amarillo**: Se han detectado algunos problemas, pero no deberían afectar significativamente el análisis.
- **Rojo**: Se han encontrado problemas serios que deben ser corregidos antes de proceder con el análisis. Esto puede incluir baja calidad de las bases, adaptadores no eliminados, secuencias contaminantes, etc.

## **Acciones Posteriores al Análisis de Calidad Inicial**

Dependiendo de los resultados obtenidos con FastQC, se pueden realizar varias acciones para mejorar la calidad de las lecturas antes de continuar con el análisis:

- **Filtrado de Lecturas**: Usar herramientas como **Trimmomatic** para eliminar lecturas de baja calidad y secuencias adaptadoras.
- **Ajuste en los Parámetros de Secuenciación**: Si los problemas son sistemáticos (por ejemplo, baja calidad en ciertas posiciones), puede ser necesario ajustar los parámetros de secuenciación en futuros experimentos.
- **Remoción de Contaminantes**: Utilizar herramientas específicas para eliminar lecturas contaminantes que puedan distorsionar el análisis.


El análisis de calidad inicial con FastQC es esencial para garantizar que las lecturas de secuenciación sean adecuadas para su uso en análisis posteriores. Proporciona una visión clara de los problemas que pueden afectar la calidad de los datos y permite tomar medidas correctivas antes de proceder a la fase de análisis, lo que mejora la fiabilidad y precisión de los resultados obtenidos.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./03_trimomatic.md)