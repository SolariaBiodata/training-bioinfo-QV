# **Ejercicio: Revisión de Formatos Bioinformáticos FASTA, FASTQ, SAM/BAM y VCF**

#### **Objetivo:**
El objetivo de este ejercicio es familiarizarse con los formatos de archivo FASTA, FASTQ, SAM/BAM y VCF, revisando su estructura, cómo se utilizan y cómo realizar operaciones básicas sobre estos archivos.

#### **FASTA y FASTQ**
**Descripción de los formatos:**
- **FASTA**: Es uno de los formatos más simples y utilizados para almacenar secuencias biológicas (como ADN, ARN o proteínas). Consiste en una cabecera seguida de la secuencia.
  - La cabecera siempre comienza con un símbolo de mayor (">") y es seguido por una descripción o identificador de la secuencia.
  - La secuencia puede estar dividida en varias líneas.

- **FASTQ**: Similar al formato FASTA, pero además de la secuencia, también incluye información sobre la calidad de cada base (mediante un código ASCII). Es comúnmente utilizado para almacenar datos de secuenciación de próxima generación (NGS).

**Ejemplo de un archivo FASTA:**
```
>seq1
AGCTGACCTGAGC
AGCAGTGCAGTGA
>seq2
TGCAGCTAGTCAG
ATCGAGTCAGTGA
```

**Ejemplo de un archivo FASTQ:**
```
@seq1
AGCTGACCTGAGCAGCAGTGCAGTGA
+
IIIIIIIIIIIIIIIIIIIIIIIIII
@seq2
TGCAGCTAGTCAGATCGAGTCAGTGA
+
IIIIIIIIIIIIIIIIIIIIIIIIII
```

**Ejercicio:**
1. **Revisar un archivo FASTA**: Abre un archivo FASTA de tu elección (puede ser uno proporcionado o creado). Identifica las cabeceras y las secuencias. ¿Cuántas secuencias contiene el archivo? ¿Cuáles son los identificadores de las secuencias?
   
2. **Revisar un archivo FASTQ**: Abre un archivo FASTQ y observa los campos. ¿Cómo se diferencian de un archivo FASTA? Identifica las secuencias de nucleótidos y las puntuaciones de calidad. ¿Qué significado tiene cada carácter en la sección de calidad?

## **SAM/BAM**
**Descripción de los formatos:**
- **SAM** (Sequence Alignment/Map) es un formato de texto utilizado para almacenar alineamientos de secuencias a un genoma de referencia. El archivo contiene información sobre las secuencias, sus posiciones en el genoma y detalles sobre la calidad de los alineamientos.
- **BAM** es la versión binaria del formato SAM, más eficiente en términos de almacenamiento y lectura.

**Ejemplo de archivo SAM:**
```
@SQ   SN:chr1 LN:248956422
r001   0   chr1   7   60   8S4M4S   *   0   0   GATCGGAAGAGCGTCGTGTAGGGAAAGAGTGTG   *   RG:Z:group1
```

**Ejercicio:**
1. **Revisar un archivo SAM**: Examina un archivo SAM de ejemplo. ¿Qué información contiene cada campo? Identifica las columnas que indican el nombre de la secuencia, la posición de alineación, la calidad de la secuencia y la información sobre la referencia.
   
2. **Conversión de SAM a BAM**: Si tienes un archivo SAM, convierte este archivo a formato BAM utilizando la herramienta `samtools`:
   ```
   samtools view -bS archivo.sam > archivo.bam
   ```

3. **Revisar un archivo BAM**: Si has convertido el archivo SAM a BAM, utiliza herramientas como `samtools` para verificar la conversión:
   ```
   samtools view archivo.bam | head
   ```

## **VCF**
**Descripción del formato:**
- **VCF** (Variant Call Format) es utilizado para almacenar información sobre variantes genéticas como SNPs, indels, y otras mutaciones observadas en una o más muestras. El formato incluye información sobre la posición de la variante, el alelo de referencia, el alelo alternativo y la calidad de la variante.

**Ejemplo de archivo VCF:**
```
#CHROM  POS  ID    REF   ALT   QUAL  FILTER  INFO
chr1    1234 rs123 G     A     99    PASS    .
chr1    5678 rs124 T     C     100   PASS    .
```

**Ejercicio:**
1. **Revisar un archivo VCF**: Abre un archivo VCF de ejemplo. ¿Qué información contiene cada columna? Identifica el cromosoma, la posición de la variante, los alelos y la calidad de la variante.
   
2. **Filtrado de variantes en VCF**: Utiliza la herramienta `vcftools` para realizar un filtrado básico sobre un archivo VCF. Por ejemplo, para filtrar variantes con calidad superior a 30:
   ```
   vcftools --vcf archivo.vcf --minQ 30 --recode --out archivo_filtrado
   ```

#### **Contesta**
1. ¿Cómo crees que los diferentes formatos bioinformáticos se complementan entre sí en un flujo de trabajo típico de análisis genómico?
2. ¿Qué ventajas y desventajas tiene cada uno de estos formatos (FASTA, FASTQ, SAM/BAM y VCF) en términos de almacenamiento, accesibilidad y procesamiento de datos?
3. ¿Qué herramientas adicionales podrían ser útiles para trabajar con estos formatos en la bioinformática?

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
