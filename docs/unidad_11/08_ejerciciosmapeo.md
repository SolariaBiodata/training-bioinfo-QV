# Ejercicio 1: Mapeo con BWA (Burrows-Wheeler Aligner)

**BWA** es una de las herramientas más utilizadas para el mapeo de lecturas de secuenciación de ADN contra una referencia. A continuación, te guiaré en cómo realizar un mapeo básico con BWA.

#### 1. Preparación de la referencia

Antes de mapear las lecturas, necesitas indexar el genoma de referencia. Esto permite que BWA realice el mapeo de manera más eficiente.

```bash
bwa index referencia_genoma.fasta
```

Este comando indexará la secuencia de referencia **referencia_genoma.fasta**.

#### 2. Mapeo de las lecturas

Una vez que el índice esté listo, puedes proceder a mapear tus lecturas de secuenciación contra la referencia. Supón que tienes un archivo de lecturas en formato **FASTQ** (por ejemplo, **lecturas.fastq**).

```bash
bwa mem referencia_genoma.fasta lecturas.fastq > mapeo.sam
```

En este comando, **bwa mem** es la función de mapeo para lecturas largas, y el archivo de salida será en formato **SAM**, que contiene los resultados del mapeo.

#### 3. Convertir a BAM

El archivo SAM debe ser convertido a formato **BAM** (binario) para ser procesado más eficientemente.

```bash
samtools view -S -b mapeo.sam > mapeo.bam
```

#### 4. Ordenar y crear un archivo BAM indexado

Una vez que tengas el archivo BAM, puedes ordenarlo y crear un índice para facilitar el acceso rápido a las ubicaciones del mapeo.

```bash
samtools sort mapeo.bam -o mapeo_ordenado.bam
samtools index mapeo_ordenado.bam
```

Obtendrás un archivo **BAM** ordenado y un índice **BAI**.

---

# Ejercicio 2: Mapeo con HISAT2

**HISAT2** es una herramienta diseñada para el mapeo de lecturas de secuenciación de RNA, aunque también se puede usar para ADN. HISAT2 es especialmente eficiente en mapeo de lecturas en genomas grandes y con muchas repeticiones.

#### 1. Preparación de la referencia

Primero, debes construir un índice para el genoma de referencia. Supón que tienes el archivo **referencia_genoma.fasta**.

```bash
hisat2-build referencia_genoma.fasta referencia_genoma_index
```

Este comando generará los archivos de índice necesarios para el mapeo.

#### 2. Mapeo de las lecturas

Una vez que el índice está listo, puedes mapear las lecturas con el siguiente comando. Supón que tienes un archivo de lecturas en formato FASTQ llamado **lecturas.fastq**.

```bash
hisat2 -x referencia_genoma_index -U lecturas.fastq -S mapeo.sam
```

El parámetro **-x** indica el archivo de índice, **-U** se usa para las lecturas simples (en formato **FASTQ**), y **-S** especifica el archivo de salida en formato **SAM**.

#### 3. Convertir y ordenar el archivo BAM

Al igual que con BWA, puedes convertir el archivo SAM a BAM y luego ordenarlo.

```bash
samtools view -bS mapeo.sam > mapeo.bam
samtools sort mapeo.bam -o mapeo_ordenado.bam
samtools index mapeo_ordenado.bam
```

---

# Ejercicio 3: Mapeo con STAR

**STAR** (Spliced Transcripts Alignment to a Reference) es un alineador rápido y preciso de secuencias de RNA-Seq. Está diseñado para mapear lecturas de RNA a una referencia, manejando intrones y empalmes de manera eficiente.

#### 1. Preparación de la referencia

Antes de mapear, debes construir un índice para el genoma de referencia con **STAR**. Supón que tienes un archivo **referencia_genoma.fasta** y un archivo de anotación GTF (**referencia_anotacion.gtf**).

```bash
STAR --runThreadN 4 --runMode genomeGenerate --genomeDir referencia_genoma_index --genomeFastaFiles referencia_genoma.fasta --sjdbGTFfile referencia_anotacion.gtf --sjdbOverhang 100
```

El parámetro **--runThreadN** especifica el número de hilos a usar, **--genomeDir** es el directorio donde se almacenará el índice, **--genomeFastaFiles** es el archivo de secuencia de referencia, y **--sjdbGTFfile** es el archivo de anotación GTF. **--sjdbOverhang** es el tamaño de las lecturas empalmadas (generalmente igual a la longitud de la lectura menos 1).

#### 2. Mapeo de las lecturas

Una vez que el índice está listo, puedes realizar el mapeo de las lecturas. Supón que tus lecturas están en un archivo **lecturas.fastq**.

```bash
STAR --runThreadN 4 --genomeDir referencia_genoma_index --readFilesIn lecturas.fastq --outFileNamePrefix mapeo_
```

Este comando genera archivos de salida con el prefijo **mapeo_**, como **mapeo_Aligned.out.sam**.

#### 3. Convertir y ordenar el archivo BAM

Puedes convertir el archivo **SAM** a **BAM** y luego ordenarlo como sigue:

```bash
samtools view -bS mapeo_Aligned.out.sam > mapeo.bam
samtools sort mapeo.bam -o mapeo_ordenado.bam
samtools index mapeo_ordenado.bam
```

Cada uno de estos alineadores tiene características y configuraciones específicas que pueden hacerlos más adecuados para diferentes tipos de datos o tipos de experimentos. **BWA** es ideal para ADN de corta longitud, **HISAT2** es útil para RNA-Seq y genomas grandes, mientras que **STAR** es uno de los mejores alineadores para RNA-Seq debido a su capacidad para manejar intrones y empalmes. Las estrategias y herramientas que elijas dependerán de tus datos y de los objetivos específicos del análisis.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)