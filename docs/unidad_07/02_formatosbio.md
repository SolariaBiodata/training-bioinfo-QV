# Formatos de Secuencias Biológicas en Bioinformática

Las secuencias biológicas, que incluyen ADN, ARN y proteínas, son fundamentales en los estudios de bioinformática. Representar y almacenar estas secuencias de manera eficiente es crucial para la manipulación, análisis y comparación de datos. En bioinformática, los formatos de secuencia biológica se utilizan para intercambiar y almacenar información sobre secuencias genéticas, sus características, variantes y resultados de análisis. Existen diversos formatos estándar que se han desarrollado para cumplir con diferentes necesidades, y es fundamental entender sus estructuras y aplicaciones.

## **Formato FASTA**  
**Definición:**  
FASTA es uno de los formatos más antiguos y ampliamente utilizados para almacenar secuencias biológicas de ADN, ARN y proteínas. Se utiliza tanto en bases de datos públicas como en análisis locales de datos secuenciales.

**Estructura:**  
El formato FASTA tiene una estructura simple que consta de dos componentes principales:  
- **Cabecera**: Comienza con un símbolo de mayor que (`>`) seguido de una descripción de la secuencia. Esta descripción puede incluir un identificador único, detalles sobre la secuencia o información adicional.
- **Secuencia**: En líneas subsiguientes, se presenta la secuencia de nucleótidos o aminoácidos, sin espacios ni caracteres adicionales.  

**Ejemplo:**  
```
>seq1 Homo sapiens, gen BRCA1
ATCGTACGATCGTAGCTAGCGTACG
```

**Usos comunes:**  
- Representación de secuencias completas o parciales de ADN, ARN o proteínas.
- Almacenamiento de secuencias en bases de datos como GenBank.
- Intercambio de datos entre herramientas bioinformáticas.

## **Formato FASTQ**  
**Definición:**  
El formato FASTQ se utiliza principalmente para almacenar secuencias de alta calidad obtenidas a través de secuenciación de próxima generación (NGS, por sus siglas en inglés). Es similar al formato FASTA, pero incluye información adicional sobre la calidad de las bases secuenciadas.

**Estructura:**  
- **Cabecera**: Similar al formato FASTA, comienza con un símbolo de mayor que (`@`) seguido de un identificador de secuencia.
- **Secuencia**: La secuencia de nucleótidos o aminoácidos, similar al formato FASTA.
- **Símbolo de calidad**: Una línea que contiene caracteres ASCII que representan la calidad de cada base de la secuencia. Cada carácter corresponde a un valor de calidad, basado en la puntuación Phred.

**Ejemplo:**  
```
@seq1
ATCGTACGATCGTAGCTAGCGTACG
+
IIIIIIIIIIIIIIIIIIIIIIII
```

**Usos comunes:**  
- Almacenamiento de secuencias de ADN generadas por plataformas de secuenciación masiva.
- Análisis de calidad de secuencias y eliminación de bases de baja calidad.

## **Formato GenBank**  
**Definición:**  
GenBank es una base de datos pública que almacena secuencias de ADN de organismos de todo el mundo. El formato GenBank es una estructura compleja y muy detallada, diseñada para incluir no solo la secuencia, sino también información adicional sobre la funcionalidad de los genes, características, y referencias bibliográficas.

**Estructura:**  
- **Cabecera**: Contiene información sobre el acceso a la secuencia, identificador del organismo, y fecha de la secuenciación.
- **Características**: Información sobre genes, exones, promotores, entre otros, que describen la funcionalidad de la secuencia.
- **Secuencia**: Secuencia de nucleótidos que se ha secuenciado.

**Ejemplo:**  
```
LOCUS       BRCA1           2000 bp    DNA    linear   PRI 01-JAN-2023
DEFINITION  Homo sapiens BRCA1 gene.
ACCESSION   AB123456
VERSION     AB123456.1
FEATURES             Location/Qualifiers
     gene            1..2000
     CDS             1..1500
     /product="BRCA1 protein"
     /protein_id="NP_000000"
ORIGIN      
        1 atgtcggtca ... 
//
```

**Usos comunes:**  
- Bases de datos públicas como GenBank utilizan este formato para almacenar secuencias anotadas de ADN.
- Investigadores lo utilizan para obtener secuencias genéticas completas, junto con detalles sobre las funciones de los genes.

## **Formato EMBL**  
**Definición:**  
EMBL (European Molecular Biology Laboratory) es otro formato estándar para almacenar secuencias biológicas, similar al formato GenBank. Se utiliza principalmente en Europa, aunque también es utilizado globalmente.

**Estructura:**  
El formato EMBL tiene una estructura similar a GenBank, pero con algunas diferencias en la forma en que se organizan las cabeceras y las características.

**Usos comunes:**  
- Almacenamiento de secuencias de ADN en bases de datos europeas.
- Intercambio de datos en contextos internacionales de investigación.

## **Formato GFF/GTF**  
**Definición:**  
Los formatos GFF (General Feature Format) y GTF (Gene Transfer Format) se utilizan para representar anotaciones genómicas, como la ubicación de genes, exones, y otras características relevantes en una secuencia de ADN.

**Estructura:**  
Ambos formatos tienen una estructura tabular con varias columnas que describen la ubicación y el tipo de característica, tales como:
- **Chromosome/Contig**: El nombre del cromosoma o contig.
- **Feature**: El tipo de característica (gen, exon, etc.).
- **Start/End**: La posición de inicio y final de la característica.
- **Score**: La puntuación asociada a la característica (opcional).
- **Strand**: El sentido de la cadena (positivo o negativo).

**Ejemplo (GFF):**  
```
chr1    .    gene    1000    5000    .    +    .    ID=gene1;Name=BRCA1
```

**Usos comunes:**  
- Almacenamiento de anotaciones de genes y otras características funcionales en secuencias genómicas.
- Análisis de secuencias genómicas en el contexto de las características funcionales.

## **Formato VCF**  
**Definición:**  
El formato VCF (Variant Call Format) se utiliza para almacenar variaciones genómicas, como mutaciones, polimorfismos y otras alteraciones en el ADN comparadas con una secuencia de referencia.

**Estructura:**  
- **Cabecera**: Información sobre el archivo, como los programas que lo generaron.
- **Cuerpo**: Cada línea describe una variante en la secuencia, incluyendo información sobre el cromosoma, la posición, el tipo de variante, y las probabilidades asociadas.

**Ejemplo:**  
```
#CHROM  POS  ID  REF  ALT  QUAL  FILTER  INFO
1       1234  .   G    A    99    PASS    .
```

**Usos comunes:**  
- Almacenamiento de variantes genómicas detectadas en secuencias de ADN.
- Análisis de variaciones genéticas en estudios de asociaciones genéticas.

Los formatos de secuencias biológicas son esenciales para el análisis y almacenamiento de datos genéticos. Cada formato tiene un propósito específico y es importante elegir el adecuado según el tipo de análisis y los requisitos del proyecto. El dominio de estos formatos es crucial para cualquier bioinformático, ya que facilita la interpretación de datos biológicos y la integración de información proveniente de diversas fuentes.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./03_anotacion.md)