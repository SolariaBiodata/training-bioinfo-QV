# Ejercicios en prokka, SAMtools y HTseq

## **Anotación de Variantes con Prokka**
Prokka se utiliza principalmente para la anotación de genomas completos, pero también puede anotarse un archivo de variantes si el genoma ya ha sido secuenciado. A continuación, se explican los pasos para la anotación de un genoma bacteriano completo y su variante:

**Comando para anotar el genoma completo usando Prokka**:
```bash
prokka --kingdom Viruses --outdir Directorio_de_resultados genoma_de_novo.fasta
```
**Explicación de los parámetros**:
- `--outdir`: Directorio donde se guardará la salida de Prokka.

## Llamado de variantes 
### 1.- Indexar el genoma de referencia
```bash
samtools faidx genoma_de_novo.fasta
```
### 2.-Indexar el archivo del ensamble .bam sorted
```bash
bamtools index -in ensamble.sorted.bam
```
### 3.- Crear un directorio con el nombre variantes
### 4.- Utilizando el programa freebayes, correr el siguiente comando 
```bash
freebayes -f genoma_de_novo.fasta ensamble.sorted.bam > variantes/VIH_genome.freebayes.vcf
```
### 5.- Revisar en la terminal el archivo generado con los siguientes comandos (cada uno por separado)
```bash
cat variantes/VIH_genome.freebayes.vcf | head
cat variantes/VIH_genome.freebayes.vcf | grep -v '##' | head -4
bgzip variantes/VIH_genome.freebayes.vcf
tabix -p vcf variantes/VIH_genome.freebayes.vcf.gz
rtg vcfstats variantes/VIH_genome.freebayes.vcf.gz
```

### Con bcftools generar un archivo con los estadísticos.
```bash
bcftools stats -F genoma_de_novo.fasta -s - variantes/VIH.freebayes.vcf.gz > variantes/VIH.freebayes.vcf.gz.stats
tabix -p vcf variantes/VIH_genome.freebayes.vcf.gz
rtg vcfstats variantes/VIH_genome.freebayes.vcf.gz
```

### GATK para generar un archivo de índices y tabla de recalibración
```bash
gatk BaseRecalibrator \ 
-I sample_marked.bam \ 
-R reference.fasta \ 
--known-sites dbsnp.vcf \ 
-O recal_data.table gatk ApplyBQSR \
-R reference.fasta \ 
-I sample_marked.bam \
--bqsr-recal-file recal_data.table \ 
-O sample_recalibrated.bam
```
### Llamado de Variantes en GATK
```bash
gatk HaplotypeCaller \ 
-R reference.fasta \ 
-I sample_recalibrated.bam \ 
-O raw_variants.vcf
```
### Filtrado de Variantes en GATK
```bash

gatk VariantFiltration \
-R reference.fasta \
-V raw_variants.vcf \
--filter-expression "QD < 2.0 || FS > 60.0 || MQ < 40.0" \
--filter-name "LowQuality" \
-O filtered_variants.vcf
```
### Anotación de Variantes 
```bash
snpEff annotate -v genome_version filtered_variants.vcf > annotated_variants.vcf
```

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)








