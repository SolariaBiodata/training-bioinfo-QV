# **Formatos de Anotación y Alineamiento en Bioinformática**

En bioinformática, los formatos de anotación y alineamiento juegan un papel esencial en la interpretación y el análisis de datos biológicos. La anotación permite identificar las funciones y características de las secuencias genéticas, mientras que los alineamientos permiten comparar estas secuencias con otras referencias o entre sí. Ambos formatos proporcionan la estructura necesaria para representar no solo las secuencias, sino también las relaciones funcionales y estructurales entre ellas.

## **Formato GFF/GTF (General Feature Format / Gene Transfer Format)**

**Definición:**
Los formatos GFF (General Feature Format) y GTF (Gene Transfer Format) son utilizados para describir las anotaciones de características genómicas, tales como genes, exones, y otras regiones funcionales dentro de una secuencia de ADN. Estos formatos permiten asociar coordenadas genómicas con características funcionales y son ampliamente utilizados en la anotación de genomas.

**Estructura:**
Ambos formatos tienen una estructura tabular, con campos específicos que describen diferentes atributos de las características anotadas. La diferencia principal entre GFF y GTF radica en el formato de las características y la cantidad de información que se almacena.

- **Campos comunes en GFF/GTF:**
  1. **Chromosome/Contig**: Nombre del cromosoma o contig donde se encuentra la característica.
  2. **Source**: Herramienta o base de datos utilizada para generar la anotación.
  3. **Feature**: Tipo de característica (ej. gen, exon, CDS, etc.).
  4. **Start/End**: Posiciones de inicio y fin de la característica en el cromosoma.
  5. **Score**: Puntuación asignada a la característica (opcional).
  6. **Strand**: Cadena en la que se encuentra la característica (positivo o negativo).
  7. **Frame**: Información sobre el marco de lectura (para CDS).
  8. **Attributes**: Información adicional sobre la característica, como identificadores y nombres.

**Ejemplo de línea GFF:**
```
chr1    .    gene    1000    5000    .    +    .    ID=gene1;Name=BRCA1
```

**Usos comunes:**
- Representar la anotación funcional de genomas en proyectos de secuenciación de genomas completos.
- Almacenar información sobre las características de los genes, tales como exones, intrones, y elementos regulatorios.
- Integración de datos de anotación de diferentes fuentes y herramientas.

## **Formato SAM/BAM (Sequence Alignment/Map / Binary Alignment/Map)**

**Definición:**
El formato SAM (Sequence Alignment/Map) es utilizado para almacenar alineamientos de secuencias de ADN contra una secuencia de referencia. El formato BAM es la versión binaria del formato SAM y se utiliza para almacenar los mismos datos en un formato más compacto, lo que facilita su almacenamiento y manipulación.

**Estructura:**
Un archivo SAM/BAM consta de dos secciones principales:
1. **Cabecera**: Contiene información sobre el archivo, la referencia, las herramientas utilizadas, etc.
2. **Alineamientos**: Cada línea describe un alineamiento de una secuencia contra una referencia, con múltiples campos que incluyen:
   - **QNAME**: Identificador de la secuencia.
   - **FLAG**: Un conjunto de indicadores que describen el estado del alineamiento (por ejemplo, si es un alineamiento correcto o si se ha invertido).
   - **RNAME**: Nombre del cromosoma o contig de referencia.
   - **POS**: Posición de inicio del alineamiento en la referencia.
   - **MAPQ**: Puntuación de calidad del alineamiento.
   - **CIGAR**: Descripción del alineamiento (por ejemplo, coincidencias, inserciones, eliminaciones).
   - **SEQ**: La secuencia de nucleótidos alineada.
   - **QUAL**: Puntuación de calidad de las bases alineadas.

**Ejemplo de línea SAM:**
```
@SQ SN:chr1 LN:248956422
r001    0    chr1    1000    60    100M    *    0    0    AGCTTAGCTAGCTAGC    IIIIIIIIIIIIIII
```

**Usos comunes:**
- Almacenamiento de alineamientos de secuencias de ADN obtenidas mediante técnicas de secuenciación de próxima generación (NGS).
- Representación de los resultados de los alineamientos de secuencias contra un genoma de referencia.
- Análisis de variantes genómicas, como SNPs y indels, a partir de los alineamientos.

## **Formato VCF (Variant Call Format)**

**Definición:**
El formato VCF (Variant Call Format) es utilizado para almacenar información sobre variantes genéticas, tales como mutaciones, polimorfismos de un solo nucleótido (SNP), inserciones y deleciones (indels). VCF proporciona una forma eficiente de almacenar las diferencias entre una secuencia de muestra y una referencia.

**Estructura:**
Un archivo VCF consta de dos partes principales:
1. **Cabecera**: Información sobre el archivo, como el formato, los programas utilizados y las referencias genéticas.
2. **Cuerpo**: Cada línea describe una variante específica y contiene varios campos, entre ellos:
   - **CHROM**: El cromosoma o contig donde se encuentra la variante.
   - **POS**: La posición de la variante en la secuencia de referencia.
   - **ID**: Identificador de la variante (opcional).
   - **REF**: Base(s) de referencia en la posición indicada.
   - **ALT**: Base(s) alternativa(s) observadas en la variante.
   - **QUAL**: Puntuación de calidad de la variante.
   - **FILTER**: Indicador de si la variante pasó un filtro de calidad.
   - **INFO**: Información adicional sobre la variante (por ejemplo, anotación funcional).

**Ejemplo de línea VCF:**
```
#CHROM  POS  ID  REF  ALT  QUAL  FILTER  INFO
1       1234  .   G    A    99    PASS    .
```

**Usos comunes:**
- Almacenamiento de variantes genéticas detectadas en estudios de secuenciación.
- Análisis de polimorfismos y mutaciones en estudios de genética poblacional y asociaciones genéticas.
- Integración de información sobre variantes de diferentes plataformas y estudios.

## **Formato BED (Browser Extensible Data)**

**Definición:**
El formato BED (Browser Extensible Data) es utilizado para describir regiones del genoma, como genes o sitios de interés. Es utilizado principalmente en visualización de datos genómicos en navegadores como UCSC Genome Browser.

**Estructura:**
Un archivo BED tiene una estructura tabular con tres columnas obligatorias:
1. **Chrom**: Nombre del cromosoma o contig.
2. **Start**: Posición de inicio de la región.
3. **End**: Posición final de la región.
También pueden incluirse columnas adicionales para información como el nombre de la característica o su puntuación.

**Ejemplo de línea BED:**
```
chr1    1000    5000    gene1    0    +
```

**Usos comunes:**
- Almacenamiento de regiones de interés para visualización en navegadores genómicos.
- Representación de características como genes, exones y otras regiones funcionales.
- Análisis de enriquecimiento de características en regiones del genoma.

Los formatos de anotación y alineamiento son fundamentales para el análisis de datos genómicos en bioinformática. Los formatos GFF/GTF permiten describir las características funcionales de los genomas, mientras que los formatos SAM/BAM y VCF son esenciales para almacenar los resultados de los alineamientos y las variantes genéticas. Cada uno de estos formatos cumple un rol específico y se utiliza en diferentes contextos dentro de los flujos de trabajo bioinformáticos. Un manejo adecuado de estos formatos facilita la interpretación precisa de los datos genómicos y la realización de análisis más complejos.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./04_formatoestructural.md)