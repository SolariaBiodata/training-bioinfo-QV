# **Ejercicio de Interpretación de Variantes Genéticas con R**

Este ejercicio está diseñado para familiarizarte con la interpretación de variantes genéticas utilizando **R**, un lenguaje de programación comúnmente utilizado en bioinformática. A continuación, te guiaré a través de un ejercicio que incluye scripts precargados en **R** para filtrar variantes genéticas y analizar su impacto potencial.

#### **Objetivo del Ejercicio:**
Aprender a filtrar variantes genéticas y obtener información clínica relevante a partir de un archivo de variantes VCF (Variant Call Format) utilizando **R**.

## **Pasos del Ejercicio:**

1. **Preparación del Entorno:**
   Necesitarás tener **R** y algunos paquetes instalados para trabajar con datos genómicos. Los paquetes que usaremos son:
   - `vcfR`: Para leer y manipular archivos VCF.
   - `dplyr`: Para manipular datos de manera eficiente.
   - `biomaRt`: Para obtener anotaciones genómicas.

   Si no tienes estos paquetes, instálalos con el siguiente comando en R:

   ```R
   install.packages("dplyr")
   install.packages("vcfR")
   install.packages("biomaRt")
   ```

2. **Cargar y Visualizar el Archivo VCF:**
   Asumimos que ya tienes un archivo **VCF** que contiene variantes genéticas. Este archivo puede haber sido generado por una secuenciación de próxima generación (NGS).

   ```R
   # Cargar las bibliotecas necesarias
   library(vcfR)
   library(dplyr)
   library(biomaRt)

   # Cargar el archivo VCF
   vcf_file <- "ruta/a/tu/archivo.vcf"
   vcf_data <- read.vcfR(vcf_file)

   # Ver las primeras filas del VCF
   head(vcf_data@fix)
   ```

   El objeto `vcf_data@fix` contiene la información de los encabezados del archivo VCF (como información sobre las variantes). Al visualizarlo con `head()`, puedes obtener una vista preliminar de las primeras filas.

3. **Filtrado de Variantes Comunes:**
   En este paso, filtramos las variantes con frecuencia alta en la población general (por ejemplo, variantes con frecuencia mayor al 1% en la base de datos gnomAD). Para esto, supongamos que ya tenemos una columna llamada `AF` (frecuencia alélica) en los datos que indica la frecuencia de la variante en la población.

   ```R
   # Filtrar variantes con frecuencia mayor al 1% (AF > 0.01)
   filtered_variants <- vcf_data@fix %>%
     filter(AF <= 0.01)

   # Mostrar las primeras filas de las variantes filtradas
   head(filtered_variants)
   ```

4. **Anotación de Variantes:**
   Utilizaremos **biomaRt** para obtener anotaciones sobre las variantes, como su ubicación en genes, efecto funcional y otras características. Esto se puede hacer al asociar el conjunto de datos con un martillo (base de datos) de Ensembl.

   ```R
   # Conectar con la base de datos Ensembl
   ensembl <- useMart("ENSEMBL_MART_ENSEMBL", dataset = "hsapiens_gene_ensembl")

   # Obtener información sobre las variantes en los genes correspondientes
   annotations <- getBM(
     attributes = c("chromosome_name", "start_position", "end_position", "gene_biotype"),
     filters = "chromosome_name",
     values = filtered_variants$CHROM,
     mart = ensembl
   )

   # Unir las anotaciones con las variantes filtradas
   annotated_variants <- left_join(filtered_variants, annotations, by = c("CHROM" = "chromosome_name"))

   # Mostrar las primeras filas de variantes anotadas
   head(annotated_variants)
   ```

5. **Clasificación de Variantes según su Patogenicidad:**
   En este paso, filtramos las variantes según su impacto potencial en la salud. Para simplificar, clasificamos las variantes según su tipo: `snp`, `indel`, etc.

   ```R
   # Clasificar variantes por tipo (por ejemplo, SNPs e Indels)
   annotated_variants$variant_type <- ifelse(grepl("INDEL", annotated_variants$INFO), "Indel", "SNP")

   # Filtrar variantes que son SNPs
   snp_variants <- annotated_variants %>%
     filter(variant_type == "SNP")

   # Mostrar variantes SNPs
   head(snp_variants)
   ```

6. **Visualización de las Variantes Filtradas:**
   Finalmente, se puede visualizar la distribución de las variantes filtradas utilizando gráficos.

   ```R
   # Instalar el paquete ggplot2 para visualización
   install.packages("ggplot2")
   library(ggplot2)

   # Graficar la distribución de las posiciones de las variantes
   ggplot(snp_variants, aes(x = start_position)) +
     geom_histogram(binwidth = 1000, fill = "blue", color = "black") +
     theme_minimal() +
     labs(title = "Distribución de SNPs en el Genoma", x = "Posición en el Genoma", y = "Número de Variantes")
   ```

## **Explicación de los Resultados Esperados:**

- **Filtrado de Variantes Comunes:** El script elimina variantes que tienen una frecuencia superior al 1% en la población general, ya que se considera que estas variantes son más comunes y tienen menos probabilidad de estar asociadas con enfermedades raras.
  
- **Anotación de Variantes:** El paso de anotación proporciona información adicional sobre las variantes, como su localización en genes y su tipo, lo que es crucial para determinar su relevancia clínica. En este caso, se obtiene información desde Ensembl.

- **Clasificación por Tipo de Variante:** Se clasifican las variantes en dos tipos principales (SNP e Indels), lo que ayuda a enfocar el análisis en las variantes con impacto potencial sobre la proteína o función génica.

- **Visualización:** El gráfico generado muestra la distribución de las variantes en el genoma, lo que puede ayudar a identificar si las variantes se encuentran en ciertas regiones genómicas específicas, como exones o áreas reguladoras.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)