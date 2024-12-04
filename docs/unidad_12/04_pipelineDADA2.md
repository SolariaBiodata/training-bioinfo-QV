# Pipeline de DADA2

El pipeline de DADA2 es un flujo de trabajo bioinformático diseñado para procesar datos de secuenciación masiva, eliminando errores técnicos y obteniendo variantes de secuencia de amplicones (ASVs) con precisión. A continuación, se describe cada uno de los pasos del pipeline, desde el control de calidad inicial hasta la obtención de resultados finales.

## Control de Calidad de Lecturas

**Objetivo:** Identificar y eliminar lecturas de baja calidad que puedan introducir ruido en el análisis.  

1. **Evaluación de la calidad:**  
   Usando la función `plotQualityProfile`, se generan gráficos que muestran la calidad de las lecturas en cada ciclo de secuenciación.  

   ```R
   plotQualityProfile(fnFs[1:2]) # Lecturas forward.
   plotQualityProfile(fnRs[1:2]) # Lecturas reverse.
   ```

2. **Filtrado y truncamiento:**  
   Se eliminan bases con baja calidad y lecturas que no cumplen con ciertos criterios.  

   ```R
   filtFs <- file.path("filtered", "sample1_R1_filtered.fastq.gz")
   filtRs <- file.path("filtered", "sample1_R2_filtered.fastq.gz")

   out <- filterAndTrim(fnFs, filtFs, fnRs, filtRs, 
                        truncLen = c(240, 200), 
                        maxN = 0, maxEE = c(2, 2), 
                        truncQ = 2, rm.phix = TRUE, 
                        compress = TRUE, multithread = TRUE)
   ```

## Desreplicación de Secuencias

**Objetivo:** Agrupar lecturas idénticas para reducir redundancia y mejorar la eficiencia computacional.  

La desreplicación genera una lista de secuencias únicas y el número de veces que aparecen en el conjunto de datos:  

```R
derepFs <- derepFastq(filtFs)
derepRs <- derepFastq(filtRs)

names(derepFs) <- sample.names
names(derepRs) <- sample.names
```


## Modelado de Errores 

**Objetivo:** Construir un modelo probabilístico de los errores introducidos por la secuenciación.  

El modelo de errores se ajusta específicamente a los datos de cada corrida de secuenciación.  

```R
errF <- learnErrors(filtFs, multithread = TRUE)
errR <- learnErrors(filtRs, multithread = TRUE)

plotErrors(errF, nominalQ = TRUE)
```

Este paso evalúa la calidad del modelo y ajusta los parámetros de corrección de errores.


## Inferencia de Variantes de Secuencia

**Objetivo:** Identificar variantes reales eliminando errores técnicos.  

Se utiliza el modelo de errores para inferir variantes de secuencia (ASVs) de las lecturas desreplicadas:  

```R
dadaFs <- dada(derepFs, err = errF, multithread = TRUE)
dadaRs <- dada(derepRs, err = errR, multithread = TRUE)
```

## Unión de Lecturas Forward y Reverse  

**Objetivo:** Combinar las lecturas forward y reverse para obtener secuencias completas del amplicón.  

La función `mergePairs` une lecturas complementarias, validando que las regiones de solapamiento coincidan:  

```R
mergers <- mergePairs(dadaFs, derepFs, dadaRs, derepRs, verbose = TRUE)
```

El resultado es un conjunto de secuencias unidas y la frecuencia de aparición de cada una.

## Remoción de Quimeras

**Objetivo:** Identificar y eliminar secuencias quiméricas que resultan de la amplificación artefactual.  

```R
seqtab <- makeSequenceTable(mergers)
seqtab.nochim <- removeBimeraDenovo(seqtab, method = "consensus", multithread = TRUE, verbose = TRUE)
```

La proporción de secuencias no quiméricas se utiliza como indicador de la calidad de los datos procesados.  

## Asignación Taxonómica

**Objetivo:** Clasificar las ASVs utilizando bases de datos taxonómicas.  

DADA2 admite bases de datos como SILVA, GreenGenes y RDP para la asignación taxonómica:  

```R
taxa <- assignTaxonomy(seqtab.nochim, "path/to/silva_nr_v138_train_set.fa.gz", multithread = TRUE)
taxa <- addSpecies(taxa, "path/to/silva_species_assignment_v138.fa.gz")
```

Esto genera una tabla que asigna taxonomía a nivel de género y especie (cuando es posible).  

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./05_resultadosyanálisis.md)
