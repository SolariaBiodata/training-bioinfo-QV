# **Integración de FastQC y Trimmomatic en un Pipeline de NGS**

En los estudios de **Next Generation Sequencing (NGS)**, la calidad de las lecturas de secuenciación es crucial para obtener resultados confiables. Las herramientas **FastQC** y **Trimmomatic** son fundamentales en el procesamiento de datos de NGS, y su integración en un pipeline bien estructurado garantiza que las lecturas sean de alta calidad antes de proceder con análisis más complejos, como alineamientos, ensamblajes y anotaciones. A continuación, se describe cómo integrar ambas herramientas en un pipeline de procesamiento de datos de NGS.

## **Pipeline Básico de NGS: Integración de FastQC y Trimmomatic**

El flujo de trabajo básico para procesar datos de secuenciación generalmente sigue estos pasos:
1. **Evaluación inicial de la calidad con FastQC**: Análisis de las lecturas crudas para identificar problemas en los datos.
2. **Filtrado y recorte de lecturas con Trimmomatic**: Eliminación de secuencias de baja calidad, secuencias adaptadoras y lecturas cortas.
3. **Evaluación posterior de la calidad con FastQC**: Comprobación de los resultados después del filtrado para asegurarse de que las lecturas son adecuadas para el análisis downstream.
4. **Análisis downstream**: Alineación de las lecturas a una referencia o ensamblaje de novo, dependiendo del objetivo del estudio.

## **Paso 1: Evaluación Inicial de la Calidad con FastQC**

Antes de realizar cualquier filtrado o procesamiento de los datos, se debe llevar a cabo un análisis inicial de la calidad utilizando **FastQC**. Este paso es crucial porque proporciona un panorama general de la calidad de las lecturas y permite identificar problemas antes de intentar corregirlos. Los problemas que pueden ser detectados incluyen:
- **Calidad de las bases**: ¿Las bases de la lectura tienen una buena puntuación de calidad a lo largo de la secuencia?
- **Secuencias adaptadoras**: ¿Existen secuencias de adaptadores presentes en las lecturas?
- **Duplicados**: ¿Hay una cantidad elevada de lecturas duplicadas?
- **Contaminación**: ¿Se detecta la presencia de secuencias de origen no deseado?
- **Distribución de GC**: ¿Hay un sesgo en el contenido de GC que podría indicar problemas en la secuenciación?

**Comando básico de FastQC**:
```bash
fastqc *.fastq
```
El comando anterior ejecuta FastQC en todos los archivos FASTQ presentes en el directorio actual. El resultado es un archivo HTML con gráficos y métricas sobre cada uno de los aspectos de calidad mencionados.

**Interpretación de resultados**:
- **Verde**: La calidad es aceptable, no es necesario realizar correcciones.
- **Amarillo**: Se detectaron algunos problemas, pero no deberían afectar significativamente el análisis.
- **Rojo**: Se encontraron problemas graves, como baja calidad de las bases, secuencias adaptadoras no eliminadas o contaminantes, lo que sugiere que se debe hacer un filtrado.

## **Paso 2: Filtrado y Recorte de Lecturas con Trimmomatic**

Una vez evaluada la calidad de las lecturas, el siguiente paso es usar **Trimmomatic** para recortar y filtrar las lecturas. Esta herramienta permite:
- Eliminar bases de baja calidad.
- Recortar secuencias adaptadoras.
- Eliminar lecturas que, después de recortarse, sean demasiado cortas.

El objetivo es mejorar la calidad de las lecturas antes de continuar con análisis más complejos, como el alineamiento o ensamblaje.

**Ejemplo de comando para recortar adaptadores y bases de baja calidad**:
```bash
java -jar trimmomatic-0.39.jar PE input_R1.fastq input_R2.fastq output_R1_paired.fastq output_R1_unpaired.fastq output_R2_paired.fastq output_R2_unpaired.fastq ILLUMINACLIP:adapter.fa:2:30:10 SLIDINGWINDOW:4:20 MINLEN:36
```

Explicación de los parámetros utilizados:
- `ILLUMINACLIP:adapter.fa:2:30:10`: Recorta secuencias adaptadoras usando el archivo `adapter.fa`, con parámetros que controlan el número mínimo de coincidencias y el número máximo de errores permitidos.
- `SLIDINGWINDOW:4:20`: Recorta bases en una ventana deslizante de 4 bases si la calidad promedio es menor a 20.
- `MINLEN:36`: Elimina lecturas que tengan menos de 36 bases después del recorte.

**Tipo de recorte realizado**:
- Recorte de adaptadores y contaminantes.
- Recorte de bases de baja calidad utilizando la técnica de ventana deslizante.
- Filtrado de lecturas demasiado cortas después del recorte.

## **aso 3: Evaluación Posterior de la Calidad con FastQC**

Después de aplicar Trimmomatic, es importante realizar otra ronda de evaluación de calidad con FastQC para asegurarse de que el filtrado haya sido efectivo y que las lecturas que quedan sean de alta calidad. Este paso también ayuda a identificar si algún problema persiste, como la presencia de contaminantes o secuencias adaptadoras.

**Comando para ejecutar FastQC después del filtrado**:
```bash
fastqc output_R1_paired.fastq output_R2_paired.fastq
```

Con esta segunda evaluación, se busca verificar que:
- La calidad de las bases ha mejorado y las lecturas recortadas son ahora de mayor calidad.
- Las secuencias adaptadoras han sido eliminadas correctamente.
- No hay lecturas contaminadas o problemas evidentes que puedan afectar el análisis downstream.

## **Paso 4: Análisis Downstream**

Una vez que las lecturas han sido evaluadas y filtradas, se pueden utilizar para diversos análisis downstream, como:
- **Alineación**: Usar herramientas como **BWA**, **Bowtie2** o **STAR** para alinear las lecturas filtradas a una referencia genómica.
- **Ensamblaje de novo**: Si no se tiene una referencia, se pueden ensamblar las lecturas utilizando herramientas como **SPAdes** o **Velvet**.
- **Anotación**: Una vez que se tienen los contigs o alineamientos, se pueden anotar utilizando bases de datos de genes o proteínas.

**Comando para alinear las lecturas con BWA** (por ejemplo):
```bash
bwa mem reference_genome.fasta output_R1_paired.fastq output_R2_paired.fastq > aligned_reads.sam
```

## **Ventajas de Integrar FastQC y Trimmomatic en un Pipeline**

La integración de **FastQC** y **Trimmomatic** en un pipeline de NGS aporta varios beneficios significativos:
1. **Mejora de la calidad de los datos**: El filtrado y recorte de las lecturas eliminan las bases de baja calidad y las secuencias contaminantes, lo que mejora la precisión de los análisis posteriores.
2. **Reducción de errores y sesgos**: Eliminar adaptadores y secuencias no deseadas previene errores y sesgos en los análisis de alineamiento o ensamblaje.
3. **Optimización de recursos**: Al eliminar lecturas de baja calidad y cortas, se asegura que el análisis downstream utilice solo las lecturas más informativas, optimizando el uso de recursos computacionales.
4. **Mayor fiabilidad de los resultados**: Un pipeline bien diseñado con FastQC y Trimmomatic reduce el riesgo de obtener resultados incorrectos o sesgados, lo que aumenta la fiabilidad de los hallazgos biológicos.

## **Consideraciones Adicionales**

- **Tamaño de la muestra**: Es importante tener en cuenta que el filtrado excesivo puede reducir demasiado la cantidad de lecturas disponibles. Por lo tanto, es esencial ajustar los parámetros de filtrado de manera que se mantenga un equilibrio entre calidad y cantidad de datos.
- **Repetibilidad**: Si se van a procesar muchos conjuntos de datos, es recomendable automatizar el pipeline para asegurar que el análisis sea repetible y eficiente.

La integración de **FastQC** y **Trimmomatic** en un pipeline de NGS es esencial para garantizar la calidad de los datos de secuenciación antes de realizar análisis más complejos. Al evaluar inicialmente la calidad de las lecturas con FastQC, filtrar y recortar con Trimmomatic, y luego evaluar nuevamente con FastQC, se asegura que solo las lecturas de alta calidad sean utilizadas, lo que mejora la precisión y confiabilidad de los análisis posteriores, como alineamientos y ensamblajes. Esta estrategia reduce la probabilidad de errores en el análisis y asegura resultados más confiables en estudios de NGS.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./05_ejercicio.md)