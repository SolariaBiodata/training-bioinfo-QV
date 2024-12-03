# Ejercicio en Ensamblaje de un Genoma Bacteria Usando SPAdes

**Objetivo:** En este ejercicio, aprenderás a realizar el ensamblaje de un genoma bacteriano utilizando el software **SPAdes**. SPAdes es una herramienta de ensamblaje de genomas de secuencias de ADN, particularmente útil para ensamblar genomas de bacterias y eucariotas pequeños utilizando datos de secuenciación de corto alcance.

**Requisitos previos:**
- Tener instalados SPAdes y las herramientas de preprocesamiento de datos como **FastQC** y **Trimmomatic**.
- Tener archivos de lectura en formato FASTQ (con las lecturas de secuenciación de ADN).

**Material necesario:**
- Archivos FASTQ (datos de secuenciación).
- Terminal de comandos de Linux o un entorno de trabajo similar (como Conda o Docker).

### **Paso 1: Preparación de los datos**

Antes de comenzar el ensamblaje, asegúrate de que los datos de secuenciación estén en buenas condiciones. Esto se puede lograr mediante el control de calidad de las lecturas y la eliminación de lecturas de baja calidad.

1. **Revisar la calidad de las lecturas con FastQC:**
   - Ejecuta FastQC para obtener un informe de calidad de las lecturas FASTQ. Esto te dará una idea general sobre la calidad de los datos antes de procesarlos.
   ```bash
   fastqc sample_R1.fastq sample_R2.fastq
   ```
   - Revisa los informes generados por FastQC y determina si hay algún problema (por ejemplo, adaptadores o baja calidad en algunas lecturas).

2. **Recortar adaptadores y lecturas de baja calidad con Trimmomatic (si es necesario):**
   - Usa **Trimmomatic** para eliminar adaptadores y recortar las lecturas de baja calidad.
   ```bash
   trimmomatic PE -phred33 sample_R1.fastq sample_R2.fastq sample_R1_trimmed.fastq sample_R1_unpaired.fastq sample_R2_trimmed.fastq sample_R2_unpaired.fastq LEADING:3 TRAILING:3 SLIDINGWINDOW:4:20 MINLEN:36
   ```
   - Este comando recorta las lecturas en las posiciones donde la calidad es baja, y elimina las lecturas que son demasiado cortas después del recorte.

### **Paso 2: Ensamblaje con SPAdes**

Una vez que las lecturas de calidad han sido aseguradas, podemos proceder con el ensamblaje del genoma utilizando SPAdes.

1. **Ejecutar SPAdes en modo de ensamblaje de genoma de bacteria (con lecturas pareadas):**
   - A continuación, ejecutamos SPAdes en modo de ensamblaje para genomas bacterianos utilizando las lecturas procesadas. Asegúrate de que el archivo de entrada tenga un buen nombre (en este caso, las lecturas recortadas son `sample_R1_trimmed.fastq` y `sample_R2_trimmed.fastq`).
   
   ```bash
   spades.py --pe1-1 sample_R1_trimmed.fastq --pe1-2 sample_R2_trimmed.fastq -o spades_output --threads 8
   ```

   **Explicación del comando:**
   - `--pe1-1 sample_R1_trimmed.fastq`: archivo de las lecturas del lado 1 del par.
   - `--pe1-2 sample_R2_trimmed.fastq`: archivo de las lecturas del lado 2 del par.
   - `-o spades_output`: especifica el directorio de salida donde se almacenarán los resultados del ensamblaje.
   - `--threads 8`: número de hilos (procesadores) que SPAdes usará para acelerar el proceso.

2. **Esperar el proceso de ensamblaje**:
   - El ensamblaje tomará algún tiempo dependiendo del tamaño y la calidad de las lecturas. SPAdes generará un conjunto de archivos de salida, incluyendo los contigs ensamblados, un archivo de estadísticas y otros resultados.

### **Paso 3: Evaluar los resultados del ensamblaje**

Una vez que SPAdes haya terminado el ensamblaje, es importante evaluar la calidad del ensamblaje y la cobertura del genoma:

1. **Revisar el archivo de estadísticas**:
   - SPAdes genera un archivo llamado `spades_output/assembly/stats.html`, que proporciona información sobre la calidad del ensamblaje, como la cantidad de contigs, el tamaño total del genoma ensamblado, la longitud media de los contigs, y más.

   Abre este archivo en un navegador para ver las estadísticas detalladas.

2. **Visualización de los contigs ensamblados**:
   - Puedes visualizar los contigs ensamblados usando herramientas como **Bandage**, que permite explorar los gráficos de ensamblaje de contigs.
   ```bash
   bandage load spades_output/assembly/contigs.fasta
   ```
   Esto abrirá una interfaz gráfica para explorar los contigs y analizar las conexiones entre ellos.

### **Paso 4: Análisis posterior al ensamblaje**

Después de realizar el ensamblaje, es posible que desees realizar análisis adicionales sobre los resultados:

1. **Identificación de genes y anotación funcional:**
   - Utiliza herramientas como **Prokka** o **Prodigal** para realizar la anotación del genoma y obtener información sobre los genes presentes en el ensamblaje.
   
   ```bash
   prokka spades_output/assembly/contigs.fasta --outdir annotation --prefix sample
   ```
   
2. **Evaluación de la cobertura y calidad del ensamblaje**:
   - Puedes realizar una alineación de tus lecturas originales contra el ensamblaje usando **Bowtie2** o **BWA** para comprobar cómo se alinean las lecturas con los contigs y evaluar la cobertura.

   ```bash
   bwa mem spades_output/assembly/contigs.fasta sample_R1_trimmed.fastq sample_R2_trimmed.fastq > aligned_reads.sam
   ```

3. **Cierre de los contigs (si es necesario)**:
   - Si los contigs no se han cerrado, es posible utilizar una herramienta de ensamblaje de largo alcance (por ejemplo, **Flye** o **Canu**) para cerrar los contigs y generar un ensamblaje más completo.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./08_ejerciciovelvet.md)