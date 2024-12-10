### **Ejercicio Práctico: Visualización de Variantes Genómicas con IGV y Tablet**

Este ejercicio tiene como objetivo guiar al usuario a través del proceso de análisis y visualización de variantes genómicas utilizando dos herramientas bioinformáticas: **IGV (Integrative Genomics Viewer)** y **Tablet**. Ambas herramientas son populares en la comunidad científica para explorar datos genómicos, aunque tienen enfoques ligeramente diferentes. Mientras que IGV es ampliamente utilizado para la visualización de datos genómicos en humanos y modelos, Tablet está más orientado al análisis de datos de ensamblaje y mapeo en organismos diversos, incluyendo genomas pequeños como los de bacterias o virus.

### **Objetivos del Ejercicio**

1. Aprender a cargar y explorar datos de secuenciación genómica en IGV y Tablet.
2. Visualizar variantes genómicas (SNPs, indels y variantes estructurales).
3. Interpretar la relación entre las variantes y sus contextos genómicos.
4. Comparar las capacidades de IGV y Tablet para visualizar y analizar variantes.

### **Requisitos Previos**

- Software instalado:
  - **IGV**: Descargable desde [Broad Institute IGV](https://software.broadinstitute.org/software/igv/).
  - **Tablet**: Descargable desde [Tablet Bioinformatics](https://ics.hutton.ac.uk/tablet/).
- Archivos de datos genómicos (pueden obtenerse de bases públicas como *1000 Genomes* o *GATK Resource Bundle*):
  - Archivo de alineación: `.bam` con su índice `.bai`.
  - Archivo de variantes: `.vcf`.
  - Archivo de referencia genómica: `.fasta` con su índice `.fai`.
- Conocimientos básicos sobre genómica y variantes genéticas.

## **Visualización en IGV**

1. **Configuración inicial**:
   - Inicia IGV.
   - Selecciona el genoma de referencia adecuado (*e.g.*, Homo sapiens hg19 o hg38) desde la opción **Genomes** > **Load Genome from Server**.
   - Carga los archivos `.bam` y `.vcf` desde **File** > **Load from File**.

2. **Exploración del BAM**:
   - Navega a una región de interés introduciendo el nombre del cromosoma y las coordenadas específicas (*e.g.*, `chr17:41,196,312-41,277,500` para visualizar el gen *BRCA1*).
   - Observa la cobertura de las lecturas en la región seleccionada. Nota áreas con mayor densidad y regiones con huecos que podrían indicar deleciones.

3. **Exploración del VCF**:
   - Activa la capa de variantes para ver las anotaciones correspondientes.
   - Busca variantes específicas: SNPs, indels o variantes estructurales.
   - Haz clic sobre las variantes para obtener detalles (posición, efecto funcional, frecuencia alélica, etc.).

4. **Análisis de variantes**:
   - Identifica una variante no sinónima en un gen codificante.
   - Compara la cobertura y el consenso entre las lecturas alineadas para confirmar la calidad de la variante.


## **Visualización en Tablet**

1. **Configuración inicial**:
   - Inicia Tablet.
   - Carga los archivos `.bam` y `.fasta` desde **File** > **Open Assembly**.
   - Asegúrate de que la referencia genómica coincida con los datos de alineación.

2. **Exploración de datos**:
   - Navega por el ensamblaje utilizando el índice de cromosomas o contigs.
   - Observa las lecturas alineadas en una región específica y verifica si Tablet detecta discrepancias.

3. **Identificación de variantes**:
   - Utiliza las herramientas de anotación para resaltar discrepancias entre las lecturas y la referencia. Estas discrepancias suelen corresponder a variantes.
   - Analiza cómo Tablet presenta las variantes en comparación con IGV (coloración de lecturas, información contextual, etc.).

4. **Exportación de datos**:
   - Genera un informe de variantes utilizando la opción **Export Variants** para un análisis posterior.

## **Comparación entre IGV y Tablet**

1. **Análisis de Cobertura**:
   - ¿Cómo presentan IGV y Tablet las regiones de alta y baja cobertura? ¿Cuál de las herramientas te parece más intuitiva?

2. **Visualización de Variantes**:
   - Examina cómo cada herramienta resalta variantes. ¿Es más claro el esquema de colores y anotaciones de IGV o de Tablet?

3. **Compatibilidad y Fluidez**:
   - Considera el tiempo de carga, la capacidad de manejar grandes conjuntos de datos y la calidad gráfica.

---

### **Contesta**

1. ¿Qué diferencias encontraste entre las variantes visualizadas en IGV y Tablet?
2. ¿Qué herramienta consideras más adecuada para un análisis de variantes en organismos complejos y por qué?
3. ¿Cómo podría la visualización de variantes ayudarte a interpretar resultados biológicos o clínicos?

Este ejercicio práctico ilustra cómo usar IGV y Tablet para visualizar variantes genómicas. Ambas herramientas tienen sus fortalezas y debilidades según el tipo de análisis que se realice y el organismo de estudio. Comprender sus capacidades y limitaciones permite a los investigadores seleccionar la herramienta más adecuada para sus necesidades y mejorar su análisis genómico.