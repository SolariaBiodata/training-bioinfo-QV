# Proceso de Mapeo con Referencia en Secuenciación Genómica

El mapeo con referencia es un proceso fundamental en los estudios de secuenciación genómica, especialmente cuando se utilizan tecnologías de secuenciación de nueva generación (NGS). Este proceso permite alinear las lecturas obtenidas de la secuenciación contra un genoma de referencia conocido para identificar posiciones específicas, variaciones genéticas (como SNPs, indels), y comprender la estructura genómica de los organismos estudiados. A continuación se presenta un desglose detallado del proceso de mapeo con referencia.

## Pasos en el Proceso de Mapeo con Referencia

El proceso de mapeo con referencia generalmente involucra varias etapas fundamentales que incluyen la preparación de los datos, el alineamiento de las lecturas a la referencia y la evaluación de la calidad del mapeo. A continuación, se describe cada uno de estos pasos en detalle:

#### 1. **Preparación de los Datos de Secuenciación**
Antes de realizar el mapeo con referencia, es necesario preparar y procesar los datos de secuenciación crudos para garantizar que se encuentren en una forma adecuada para el análisis:

   - **Control de calidad de las lecturas**: Utilizar herramientas como **FastQC** para evaluar la calidad de las lecturas generadas por la secuenciación. Esto incluye verificar la distribución de la calidad de las bases, la presencia de adaptadores, y la longitud de las lecturas.
   - **Filtrado y recorte**: Las lecturas con baja calidad o con secuencias de adaptadores deben ser eliminadas o recortadas utilizando herramientas como **Trimmomatic** o **Cutadapt**.

#### 2. **Selección de la Secuencia de Referencia**
Para el mapeo con referencia, se necesita una secuencia de referencia para alinear las lecturas. Esta referencia puede ser:

   - **Genoma completo de una especie**: Para estudios de genómica, donde el objetivo es alinear lecturas que provienen de todo el genoma.
   - **Subconjuntos de genoma o regiones específicas**: En casos donde solo se quiere estudiar ciertas regiones del genoma, como exomas o genes específicos.

La calidad y la precisión de la referencia son críticas, ya que cualquier error o defecto en la secuencia de referencia puede afectar el proceso de alineación y la interpretación de los resultados.

#### 3. **Alineamiento de las Lecturas**
El siguiente paso es alinear las lecturas obtenidas de la secuenciación contra la secuencia de referencia. Esto se hace utilizando programas de alineación que utilizan diversos algoritmos para encontrar la mejor coincidencia entre las lecturas y la referencia. Los principales métodos de alineación incluyen:

   - **Algoritmos de emparejamiento exacto**: Estos algoritmos buscan encontrar coincidencias exactas entre las lecturas y la secuencia de referencia. Se usan cuando las lecturas son de alta calidad y no contienen muchos errores.
   - **Algoritmos de alineación aproximada**: Estos permiten alineamientos más flexibles, permitiendo pequeñas diferencias entre las lecturas y la referencia (como pequeñas mutaciones o indels). Son esenciales cuando las lecturas contienen errores o variaciones.

Herramientas comunes para realizar este mapeo son:
   - **BWA (Burrows-Wheeler Aligner)**: Utiliza la transformada de Burrows-Wheeler para indexar el genoma de referencia, lo que permite un alineamiento rápido y eficiente.
   - **Bowtie**: Un alineador rápido y eficiente basado en el algoritmo de Burrows-Wheeler.
   - **STAR**: Utilizado principalmente para RNA-Seq, realiza alineamientos de transcritos con alta precisión.

#### 4. **Evaluación de la Calidad del Mapeo**
Una vez que las lecturas se han alineado con la referencia, es crucial evaluar la calidad del mapeo. Se pueden utilizar varias métricas para evaluar el éxito del mapeo:

   - **Porcentaje de lecturas mapeadas**: Un alto porcentaje de lecturas mapeadas indica que las lecturas fueron correctamente alineadas con la referencia.
   - **Cobertura del genoma**: Es importante verificar qué porción del genoma está cubierta por las lecturas, ya que las áreas con baja cobertura pueden generar sesgos en el análisis.
   - **Posicionamiento y distribuciones de las lecturas**: Analizar cómo están distribuidas las lecturas a lo largo del genoma para asegurar que no haya áreas sin cubrir o mal alineadas.

Las herramientas como **Samtools** o **Picard** permiten evaluar la calidad del alineamiento, así como la presencia de duplicados, cobertura, y otros aspectos clave.

#### 5. **Identificación de Variantes**
Una de las principales aplicaciones del mapeo con referencia es la identificación de variantes genéticas entre el genoma de referencia y las lecturas mapeadas. Estas variantes pueden incluir:

   - **SNPs (Polimorfismos de Nucleótido Único)**: Cambios en un solo nucleótido entre la referencia y las lecturas.
   - **Indels (Inserciones y Deleciones)**: Variaciones en la secuencia que involucran la inserción o eliminación de nucleótidos.
   - **Reordenamientos y variaciones estructurales**: Cambios más grandes en la estructura del genoma que pueden incluir inversiones o translocaciones.

Herramientas como **GATK** (Genome Analysis Toolkit) y **Samtools** se utilizan para llamar variantes después del mapeo. Estas herramientas comparan las lecturas mapeadas con la referencia y detectan las variantes de interés.

## Consideraciones Importantes en el Mapeo con Referencia

   - **Exactitud de la referencia**: Si la referencia contiene errores o no está completamente representada (como en el caso de organismos con genomas no completamente secuenciados), puede haber problemas durante el mapeo.
   - **Complejidad de las lecturas**: Las lecturas largas o con muchas secuencias repetitivas pueden ser difíciles de alinear correctamente, lo que puede generar problemas de mapeo, especialmente en regiones altamente repetitivas del genoma.
   - **Errores en las lecturas**: Las tecnologías de secuenciación a veces generan lecturas con errores, lo que puede dificultar el mapeo exacto. Las herramientas modernas de mapeo a menudo permiten tolerar estos errores mediante un mapeo aproximado.

El mapeo con referencia es una herramienta poderosa en la genómica moderna, permitiendo la alineación precisa de lecturas de secuenciación con una secuencia conocida para identificar variantes y estudiar la estructura genética de los organismos. Aunque es una técnica eficiente, depende de la calidad de la referencia y puede enfrentar desafíos en regiones complejas del genoma. A medida que la tecnología de secuenciación y las herramientas bioinformáticas continúan avanzando, el proceso de mapeo con referencia seguirá siendo esencial en la interpretación de datos genómicos y la investigación biológica.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./06_aplicacionesdelmapeo.md)