# **Ejercicio: Análisis de calidad y preprocesamiento de lecturas con FastQC y Trimmomatic**

### **Objetivo**
1. Evaluar la calidad de datos de secuenciación usando FastQC.
2. Filtrar y recortar las secuencias con Trimmomatic para eliminar datos de baja calidad y adaptadores.

### **Datos necesarios**
- **Archivos FASTQ de prueba**: Descargar secuencias ejemplo desde bases como [SRA](https://www.ncbi.nlm.nih.gov/sra) o usar archivos FASTQ proporcionados.
  - Ejemplo: `sample_R1.fastq` (lecturas forward) y `sample_R2.fastq` (lecturas reverse).
- Archivo de adaptadores: Proporcionado en Trimmomatic (`adapters/TruSeq3-PE.fa`).

### **Requisitos**
- **Software instalado**:
  - FastQC
  - Trimmomatic
- Conocimientos básicos de terminal o línea de comandos.

## **Parte 1: Evaluación inicial de calidad con FastQC**

1. **Ejecuta FastQC** en tus archivos FASTQ:
   ```bash
   fastqc sample_R1.fastq sample_R2.fastq
   ```
2. **Explora los resultados**:
   - Revisa los archivos generados (`.html` y `.zip`) en el directorio actual.
   - Analiza:
     - **Gráfico de calidad**: ¿Dónde baja la calidad de las bases?
     - **Contenido GC**: ¿Hay algún sesgo?
     - **Adaptadores presentes**: ¿Aparecen adaptadores en el análisis?

3. **Pregunta:**
   - ¿Los datos necesitan recorte o filtrado antes de continuar con el análisis?

## **Parte 2: Recorte y filtrado con Trimmomatic**

1. **Ejecuta Trimmomatic** en modo de pares:
   ```bash
   trimmomatic PE \
   sample_R1.fastq sample_R2.fastq \
   trimmed_R1_paired.fastq trimmed_R1_unpaired.fastq \
   trimmed_R2_paired.fastq trimmed_R2_unpaired.fastq \
   ILLUMINACLIP:adapters/TruSeq3-PE.fa:2:30:10 \
   LEADING:3 TRAILING:3 SLIDINGWINDOW:4:20 MINLEN:36
   ```
   - **Parámetros**:
     - `ILLUMINACLIP`: Recorta adaptadores.
     - `LEADING` y `TRAILING`: Elimina bases de baja calidad en los extremos.
     - `SLIDINGWINDOW`: Filtra lecturas con una calidad promedio por ventana inferior al umbral.
     - `MINLEN`: Descarta lecturas más cortas que el valor especificado.

2. **Verifica los archivos generados**:
   - `trimmed_R1_paired.fastq` y `trimmed_R2_paired.fastq`: Lecturas limpias.
   - `trimmed_R1_unpaired.fastq` y `trimmed_R2_unpaired.fastq`: Lecturas descartadas.

## **Parte 3: Revisión post-procesamiento con FastQC**

1. Ejecuta FastQC nuevamente en los archivos filtrados:
   ```bash
   fastqc trimmed_R1_paired.fastq trimmed_R2_paired.fastq
   ```
2. Compara los resultados con el análisis inicial:
   - ¿Mejoró la calidad de las lecturas?
   - ¿Se eliminaron los adaptadores?

## **Contesta**
1. ¿Qué patrones de baja calidad identificaste en los datos originales?
2. ¿Cuánto mejoraron los datos tras el procesamiento?
3. ¿Crees que el recorte afectó negativamente la cantidad de datos?

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)