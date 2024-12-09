# **Herramientas y Métodos para la Detección de Variantes Genéticas**

La detección de variantes genéticas implica el uso de herramientas bioinformáticas y métodos computacionales para identificar diferencias entre el ADN de un organismo y un genoma de referencia. Este análisis es crucial para aplicaciones en genética médica, estudios evolutivos, y proyectos de diversidad genómica.

## **Flujo de Trabajo General**
El proceso de detección de variantes sigue un flujo estructurado que incluye las siguientes etapas:
1. **Secuenciación**:
   - Obtención de datos de secuenciación de nueva generación (NGS) en formato FASTQ.
2. **Preprocesamiento**:
   - Filtrado y limpieza de las lecturas de ADN.
   - Alineación de las lecturas al genoma de referencia.
3. **Llamado de variantes** (*Variant Calling*):
   - Identificación de diferencias genéticas (SNPs, Indels, variantes estructurales).
4. **Filtrado y Anotación**:
   - Eliminación de variantes falsas positivas y asignación de significado biológico.

## **Herramientas Principales para la Detección de Variantes**
Existen diversas herramientas bioinformáticas que ayudan en cada etapa del análisis. Algunas de las más utilizadas son:

### **Alineación**
La alineación mapea las lecturas de ADN contra un genoma de referencia.
   - **BWA (Burrows-Wheeler Aligner)**:
     - Rápido y eficiente para lecturas cortas.
   - **Bowtie2**:
     - Excelente para lecturas de longitud variable.
   - **Minimap2**:
     - Diseñado para lecturas largas (p. ej., PacBio, Oxford Nanopore).
   
### **Llamado de Variantes**
Herramientas para identificar variantes genéticas en las lecturas alineadas:
   - **GATK (Genome Analysis Toolkit)**:
     - Plataforma robusta para SNPs y pequeños Indels.
   - **FreeBayes**:
     - Adecuado para poblaciones y genomas poliploides.
   - **SAMtools/BCFtools**:
     - Ligero y eficiente para tareas de llamado y manipulación de variantes.

### **Detección de Variantes Estructurales**
   - **Manta**:
     - Identificación de inserciones, deleciones, y translocaciones.
   - **Lumpy**:
     - Especializado en variantes complejas.
   - **Sniffles**:
     - Diseñado para lecturas largas.

### **Anotación de Variantes**
Asigna información funcional y clínica a las variantes detectadas:
   - **ANNOVAR**:
     - Anotación basada en bases de datos funcionales y clínicas.
   - **SnpEff**:
     - Predicción de impacto funcional.
   - **Ensembl VEP (Variant Effect Predictor)**:
     - Análisis detallado con bases de datos actualizadas.

## **Métodos Específicos**
### **SNPs y Indels**
   - **Pipeline de GATK**:
     1. Preprocesamiento: Alineación con BWA y recalibración de calidad.
     2. Llamado de variantes con *HaplotypeCaller*.
     3. Filtrado con criterios estadísticos.

### **Variantes Estructurales**
   - Herramientas como Lumpy o Manta detectan grandes reorganizaciones genómicas utilizando estrategias como:
     - **Lecturas divididas** (*Split Reads*): Identificación de lecturas que abarcan puntos de ruptura.
     - **Pares discordantes**: Alineaciones anómalas de lecturas emparejadas.

### **Variantes en Genomas Poliploides o Complejos**
   - **FreeBayes** y **Platypus**:
     - Utilizan modelos que consideran múltiples alelos por locus.

## **Filtrado y Validación**
Después de la detección, las variantes deben ser filtradas para evitar errores:
   - **Criterios de calidad**:
     - Profundidad de cobertura adecuada.
     - Baja tasa de errores en la base.
   - **Validación experimental**:
     - PCR y secuenciación Sanger para verificar variantes detectadas computacionalmente.

Las herramientas y métodos para la detección de variantes han evolucionado rápidamente gracias al avance de la bioinformática y la tecnología de secuenciación. Estas metodologías permiten identificar, interpretar y aplicar el conocimiento de las variantes genéticas en una amplia gama de campos, aunque siguen existiendo desafíos técnicos y analíticos por superar.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./03_análisisvariantes.md)
