# Resultados y Análisis en DADA2

El análisis de datos procesados con DADA2 culmina con la generación de resultados que describen la diversidad genética y taxonómica de las muestras. Este tema aborda la interpretación de los resultados obtenidos, los métodos para validar su calidad, y las técnicas para visualizarlos de manera clara y efectiva.

## Generación de la Tabla de Variantes de Secuencia (ASVs)

La tabla de ASVs es el producto principal del pipeline de DADA2. Contiene la abundancia de cada variante de secuencia en cada muestra.  

### Pasos principales:
1. Crear la tabla de ASVs:  
   ```R
   seqtab <- makeSequenceTable(mergers)
   dim(seqtab) # Muestra el número de muestras y ASVs detectadas.
   ```

2. Remover quimeras para garantizar la calidad:  
   ```R
   seqtab.nochim <- removeBimeraDenovo(seqtab, method = "consensus", multithread = TRUE)
   ```
   El porcentaje de lecturas no quiméricas es un indicador clave de la calidad del proceso:  
   ```R
   sum(seqtab.nochim) / sum(seqtab) * 100
   ```

3. Inspeccionar las ASVs más frecuentes:  
   ```R
   colnames(seqtab.nochim)[1:5]
   ```

### Asignación Taxonómica

DADA2 utiliza bases de datos como SILVA o GreenGenes para asignar una clasificación taxonómica a las ASVs.  

1. Asignar taxonomía hasta el nivel de género:  
   ```R
   taxa <- assignTaxonomy(seqtab.nochim, "path/to/silva_nr_v138_train_set.fa.gz", multithread = TRUE)
   ```

2. Opcional: Asignar taxonomía a nivel de especie cuando sea posible:  
   ```R
   taxa <- addSpecies(taxa, "path/to/silva_species_assignment_v138.fa.gz")
   ```

3. Ver los resultados de la taxonomía:  
   ```R
   taxa[1:5, ]
   ```

### Validación de Resultados

Para asegurar la fiabilidad de los datos, se realizan verificaciones como:  

1. **Distribución de la riqueza de ASVs:**  
   Muestra la diversidad en cada muestra:  
   ```R
   rowSums(seqtab.nochim)
   ```

2. **Proporción de ASVs asignadas a taxonomía:**  
   Analiza cuántas variantes tienen una clasificación taxonómica:  
   ```R
   prop.table(table(is.na(taxa[, "Genus"])))
   ```

3. **Evaluación de lecturas filtradas y retenidas:**  
   Revisa el flujo de datos desde la entrada hasta la salida:  
   ```R
   track <- cbind(out, rowSums(seqtab), rowSums(seqtab.nochim))
   colnames(track) <- c("Filtrado", "No quimérico")
   track
   ```

### Visualización de Resultados

La visualización facilita la interpretación de los datos y la comunicación de los hallazgos.  

1. **Riqueza de ASVs en muestras:**  
   Muestra cuántas variantes están presentes en cada muestra:  
   ```R
   hist(rowSums(seqtab.nochim), breaks = 20, main = "Distribución de Riqueza de ASVs", xlab = "Número de ASVs")
   ```

2. **Clasificación taxonómica:**  
   Gráficos de barras para visualizar la abundancia de cada nivel taxonómico (género, familia, etc.):  
   ```R
   barplot(sort(table(taxa[, "Genus"]), decreasing = TRUE)[1:10], 
           main = "Top 10 Géneros", las = 2, col = rainbow(10))
   ```

3. **Diversidad alfa y beta:**  
   Usando herramientas como *Phyloseq* o *Vegan*, se pueden calcular métricas de diversidad:  

   - **Diversidad alfa:**  
     ```R
     library(phyloseq)
     ps <- phyloseq(otu_table(seqtab.nochim, taxa_are_rows = FALSE), tax_table(taxa))
     plot_richness(ps, measures = c("Shannon", "Simpson"))
     ```

   - **Diversidad beta (Análisis de PCoA):**  
     ```R
     ord <- ordinate(ps, method = "PCoA", distance = "bray")
     plot_ordination(ps, ord, color = "SampleType", title = "PCoA")
     ```

### Exportación de Resultados

Los datos procesados se pueden exportar para integrarlos con otros análisis o herramientas.  

1. Exportar la tabla de ASVs:  
   ```R
   write.table(seqtab.nochim, "ASV_table.txt", sep = "\t", quote = FALSE)
   ```

2. Exportar la taxonomía asignada:  
   ```R
   write.table(taxa, "Taxonomy_table.txt", sep = "\t", quote = FALSE)
   ```

3. Exportar datos para herramientas externas como QIIME2:  
   ```R
   library(Biostrings)
   sequences <- getSequences(seqtab.nochim)
   writeXStringSet(DNAStringSet(sequences), "ASVs.fasta")
   ```

### Interpretación de Resultados

1. **Identificación de patrones:**  
   Analiza cómo se distribuyen las ASVs entre las muestras y los niveles taxonómicos para buscar patrones relevantes.  

2. **Comparación entre muestras:**  
   Examina la diversidad microbiana entre diferentes grupos (p. ej., muestras de pacientes vs. controles) para identificar posibles asociaciones.  

3. **Correlación con metadatos:**  
   Vincula los resultados con factores experimentales o ambientales para interpretar su impacto en la composición microbiana.  

El análisis y visualización de los resultados generados por DADA2 permiten obtener insights valiosos sobre la composición y diversidad microbiana, facilitando su interpretación en el contexto del estudio. Con estas herramientas, los investigadores pueden relacionar los datos con preguntas ecológicas, médicas o evolutivas específicas.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./05_resultadosyanálisis.md)