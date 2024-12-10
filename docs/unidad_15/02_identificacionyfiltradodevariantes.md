# **Identificación y Filtrado de Variantes**  

La identificación y el filtrado de variantes son pasos esenciales en el análisis de datos genómicos, especialmente en el contexto de la investigación clínica y genómica. Este proceso ayuda a reducir el número de variantes posibles a aquellas que tienen mayor probabilidad de ser funcionales, patogénicas o relevantes para la condición o enfermedad en estudio. A continuación, se desarrollan en detalle los aspectos clave de la identificación y el filtrado de variantes.

## **Métodos de Secuenciación y Detección de Variantes**  

**1.1 Secuenciación de Próxima Generación (NGS):**  
La secuenciación de próxima generación (NGS) ha revolucionado el análisis genético, permitiendo la identificación de variantes genéticas con una alta resolución. Existen diferentes plataformas y técnicas que se utilizan dependiendo del tipo de análisis que se desee realizar:

- **Secuenciación de Exomas (WES):** Secuencia únicamente las regiones codificantes del genoma (~1-2% del genoma), lo cual es eficiente para encontrar variantes relevantes en genes causantes de enfermedades.
- **Secuenciación de Genoma Completo (WGS):** Permite analizar todo el genoma, tanto las regiones codificantes como no codificantes, y detectar variantes raras o complejas, incluidas las variaciones estructurales.
- **Paneles Dirigidos:** Focalizados en un conjunto específico de genes asociados con enfermedades hereditarias o cáncer, son más rápidos y menos costosos que las técnicas de secuenciación completa.

## **Control de Calidad en el Análisis de Variantes**  

**Evaluación de Calidad de Datos:**  
Una vez obtenidos los datos de secuenciación, es esencial realizar un control de calidad antes de proceder con la identificación de variantes:

- **Phred Score:** Indica la probabilidad de que una base esté equivocada. Un Phred score superior a 20 o 30 es considerado aceptable para la mayoría de los análisis.
- **Cobertura:** Es el número de lecturas que cubren una región específica del genoma. Cuanto mayor sea la cobertura (por ejemplo, ≥30x), mayor es la precisión de la variante identificada.
- **Duplicados:** Las lecturas duplicadas pueden introducir sesgos, por lo que se deben eliminar durante el procesamiento de datos.
- **Herramientas:**  
  - **FastQC:** Para verificar la calidad general de las lecturas de secuenciación.
  - **MultiQC:** Herramienta que agrupa los informes de calidad de varias muestras para una comparación visual rápida.

**Filtrado Inicial de Datos:**  
Se eliminan las lecturas de baja calidad, las que tienen errores en su secuenciación o aquellas que no tienen suficiente cobertura. Además, se eliminan las regiones genómicas con secuencias repetitivas o problemáticas que dificultan el alineamiento.

## **Identificación de Variantes**  

**Llamado de Variantes (Variant Calling):**  
El proceso de llamado de variantes es la identificación de las diferencias entre el ADN secuenciado de una muestra y el genoma de referencia. Existen herramientas especializadas que realizan esta tarea, algunas de las más utilizadas incluyen:

- **GATK HaplotypeCaller:** Utilizado para variantes germinales, identifica SNPs e indels con alta precisión.
- **FreeBayes:** Otra herramienta útil para llamar variantes, especialmente en muestras con baja cobertura o genomas complejos.
- **Mutect2:** Diseñada específicamente para variantes somáticas, especialmente en el contexto de cáncer.
  
**Tipos de Variantes Identificadas:**  
Las variantes que se identifican pueden clasificarse en varios tipos, según la naturaleza del cambio en la secuencia de ADN:
- **SNPs (Polimorfismos de un solo nucleótido):** Cambios en una sola base del ADN.
- **Indels:** Inserciones o deleciones de una o más bases.
- **CNVs (Variantes en el número de copias):** Variaciones en la cantidad de copias de una región del genoma.
- **Variantes Estructurales:** Alteraciones más grandes, como duplicaciones, translocaciones e inversiones.

## **Filtrado de Variantes Relevantes**  

Dado que el proceso de secuenciación puede generar millones de variantes, es crucial aplicar filtros para reducir el número de variantes a aquellas con mayor probabilidad de ser funcionales o patogénicas. Este proceso se hace en varios pasos:

**Filtrado Inicial:**  
Este filtrado elimina variantes que son comúnmente observadas en la población sana y que, por tanto, no tienen una probabilidad significativa de estar asociadas con una enfermedad:
- **Frecuencia en la población:** Variantes con una frecuencia mayor al 1% en bases de datos como **gnomAD** o **1000 Genomes** generalmente se consideran benignas y se eliminan del análisis.
- **Calidad mínima (QUAL):** Las variantes con un puntaje de calidad bajo se filtran para asegurar que solo se consideren las variantes de alta confiabilidad.

**Filtros Específicos para Contextos Clínicos:**  
Dependiendo de la enfermedad o el fenotipo de interés, se pueden aplicar filtros adicionales:
- **Genes específicos:** Filtrar por variantes en genes que están relacionados con la enfermedad en cuestión (por ejemplo, variantes en **BRCA1** para cáncer de mama).
- **Impacto funcional:** Variantes que impactan funciones críticas como la codificación de proteínas, elementos reguladores o sitios de splicing son priorizadas.

**Herramientas de Filtrado:**
- **VCFtools:** Utilizado para manejar y filtrar archivos VCF (Variant Call Format), el formato comúnmente utilizado para almacenar variantes genéticas.
- **bcftools:** Permite aplicar filtros complejos a archivos VCF basados en varios parámetros, como calidad, profundidad de cobertura y frecuencia alélica.

## **Herramientas y Recursos para Filtrado y Priorización**  

**Anotación de Variantes:**  
Después de identificar y filtrar variantes, se deben anotar para obtener información adicional sobre su posible relevancia clínica. Existen herramientas que ayudan a este proceso:
- **ANNOVAR:** Realiza anotación funcional de variantes, identificando si se encuentran en regiones codificantes o si afectan a proteínas.
- **VEP (Variant Effect Predictor):** De Ensembl, proporciona anotaciones detalladas sobre variantes, prediciendo su impacto en la proteína.
- **SnpEff:** Similar a VEP, pero también incluye predicciones sobre el impacto en los elementos regulatorios.

**Base de Datos para la Priorización de Variantes:**  
Las bases de datos clínicas y de población son recursos fundamentales para la interpretación de variantes:
- **ClinVar:** Base de datos pública que clasifica variantes en categorías como patogénicas, benignas o de significado incierto (VUS).
- **HGMD (Human Gene Mutation Database):** Contiene variantes genéticas asociadas con enfermedades hereditarias.
- **gnomAD (Genome Aggregation Database):** Proporciona frecuencias de variantes en la población, permitiendo distinguir entre variantes comunes y raras.

## **Desafíos en el Filtrado y la Identificación de Variantes**  

- **Falsos positivos y negativos:**  
  El proceso de llamado de variantes puede generar falsos positivos (variantes que no son reales) o falsos negativos (variantes que no se detectan). Es importante validar las variantes con técnicas adicionales como PCR o secuenciación Sanger.
  
- **Variantes estructurales:**  
  Las variantes estructurales (duplicaciones, translocaciones) son más difíciles de detectar con NGS debido a su tamaño y complejidad. Herramientas como **Lumpy** o **Manta** pueden ayudar, pero la cobertura de estas variantes sigue siendo un desafío.

- **Impacto funcional en regiones no codificantes:**  
  La interpretación de variantes en regiones no codificantes sigue siendo un desafío, aunque está mejorando con el desarrollo de nuevas herramientas de análisis y anotación.

La identificación y filtrado de variantes genéticas son procesos fundamentales en el análisis genómico, especialmente en contextos clínicos. Utilizando herramientas avanzadas y bases de datos, los investigadores y médicos pueden reducir el número de variantes potencialmente patogénicas y centrarse en aquellas que tienen un mayor impacto en la salud del paciente. Este enfoque sistemático ayuda a mejorar la precisión del diagnóstico y facilita el avance hacia la medicina personalizada.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./03_interpretacion.md)