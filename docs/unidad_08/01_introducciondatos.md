# **Introducción a la Calidad de Datos en Secuenciación NGS**

La secuenciación de nueva generación (NGS, por sus siglas en inglés) ha revolucionado la biología molecular, permitiendo la obtención de grandes cantidades de datos genómicos a un costo mucho más bajo que las tecnologías anteriores. Sin embargo, debido a la alta cantidad de datos generados y las complejidades inherentes al proceso de secuenciación, la calidad de los datos se convierte en un aspecto crucial para garantizar la precisión de los análisis posteriores. A continuación, se exploran los conceptos fundamentales relacionados con la calidad de los datos en NGS.

## **Importancia de los Controles de Calidad en NGS**

En NGS, la calidad de los datos es crítica, ya que influye directamente en la fiabilidad de los resultados del análisis. Los datos de baja calidad pueden generar falsos positivos, falsos negativos o interpretaciones incorrectas, lo que afectaría la validez de las conclusiones obtenidas de un experimento. Sin una evaluación rigurosa de la calidad de las lecturas, se podrían pasar por alto problemas que impidan una correcta interpretación de la información genética.

Los controles de calidad aseguran que las lecturas que se utilizarán en el análisis sean lo suficientemente buenas para ser confiables y precisas. Por ello, el monitoreo continuo de la calidad durante todo el proceso de secuenciación y análisis es necesario para optimizar los resultados.

## **Problemas Comunes en los Datos de NGS**

Los datos obtenidos por NGS pueden verse afectados por varios problemas técnicos, biológicos o de procesamiento. Algunos de los problemas más comunes son:

- **Lecturas de baja calidad**: En algunas secuencias, las bases pueden tener una calidad baja debido a errores de secuenciación o problemas con la química utilizada. Esto puede reflejarse en puntuaciones de calidad bajas en algunas posiciones de la secuencia.
  
- **Contaminación de secuencias**: Pueden aparecer secuencias no deseadas, como aquellas originadas de contaminantes (por ejemplo, secuencias bacterianas en muestras humanas o de otras especies presentes en la muestra), que alteran los resultados.

- **Adaptadores no eliminados**: Los adaptadores que se utilizan durante la preparación de las bibliotecas de secuenciación pueden no eliminarse completamente, lo que provoca que las lecturas contengan secuencias adicionales al final de las lecturas.

- **Sesgo en la secuenciación**: Algunos métodos de secuenciación pueden introducir sesgos sistemáticos, como un mayor número de lecturas en ciertas regiones del genoma o un menor número en otras.

- **Errores de alineación**: En el proceso de alineación de las lecturas con un genoma de referencia, los errores pueden ocurrir debido a lecturas de baja calidad o adaptadores no eliminados, lo que genera alineaciones incorrectas.

## **Estrategias para Asegurar la Calidad de los Datos**

Existen diversas técnicas y herramientas utilizadas para monitorear y mejorar la calidad de los datos en NGS. Estas incluyen:

- **Evaluación de calidad de las lecturas**: Herramientas como **FastQC** permiten evaluar la calidad de las lecturas antes de realizar cualquier procesamiento. FastQC genera informes detallados que incluyen métricas sobre la calidad de las bases, la presencia de adaptadores, la distribución de las secuencias, y la presencia de contaminantes o duplicados.

- **Filtrado de lecturas**: Herramientas como **Trimmomatic** o **Cutadapt** son utilizadas para eliminar secuencias de baja calidad y adaptadores. El filtrado asegura que solo las lecturas con una calidad suficiente sean utilizadas en el análisis posterior.

- **Alineación y ensamblaje**: Tras el filtrado de las lecturas, las secuencias se alinean con un genoma de referencia o se ensamblan en nuevos contigs. Durante este proceso, es importante asegurarse de que los errores de calidad no interfieran con la correcta alineación o ensamblaje.

- **Control de calidad durante todo el proceso**: El monitoreo de la calidad debe ser continuo durante todas las fases del análisis, desde la secuenciación hasta el análisis final de los resultados. Es fundamental verificar la calidad de las lecturas después de cada paso del procesamiento para garantizar que los datos sean fiables.

## **Herramientas Comunes para la Evaluación de la Calidad**

- **FastQC**: Es una de las herramientas más utilizadas para evaluar la calidad de los datos de secuenciación. FastQC genera una serie de gráficos y métricas que permiten detectar problemas en las lecturas, como baja calidad de bases, adaptadores no eliminados, sesgos en las lecturas, entre otros.

- **Trimmomatic**: Es una herramienta de procesamiento que se usa principalmente para recortar adaptadores y bases de baja calidad de las lecturas. Trimmomatic permite realizar ajustes finos en el filtrado según las necesidades del proyecto.

- **Cutadapt**: Similar a Trimmomatic, esta herramienta se especializa en el recorte de adaptadores. Es ampliamente utilizada en análisis de secuenciación de RNA-Seq y otros proyectos donde los adaptadores pueden interferir en el análisis.

#### **5. Impacto de la Calidad de los Datos en el Análisis Posterior**

La calidad de las lecturas tiene un impacto directo en los resultados obtenidos en los análisis downstream, tales como:

- **Alineación del genoma**: Las lecturas de alta calidad se alinean mejor con el genoma de referencia, lo que mejora la precisión del mapeo y la identificación de variantes.
  
- **Análisis de expresión génica**: En RNA-Seq, una baja calidad de las lecturas puede afectar la detección de genes expresados o variantes de splicing, distorsionando los resultados de la expresión génica.

- **Identificación de variantes**: La calidad de los datos es crucial para la correcta identificación de variantes genéticas (como SNPs o indels). Lecturas con baja calidad o contaminadas pueden generar errores en la llamada de variantes.

El control de calidad es un paso fundamental en los proyectos de secuenciación NGS, ya que los datos sin una adecuada evaluación y filtrado pueden generar resultados incorrectos o irreproducibles. Implementar un flujo de trabajo adecuado que incluya herramientas como FastQC y Trimmomatic garantiza que solo los datos de alta calidad se utilicen en los análisis posteriores, mejorando la fiabilidad y precisión de las conclusiones científicas.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./02_calidadinicial.md)