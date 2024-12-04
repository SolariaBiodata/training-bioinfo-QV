# Desreplicación de Secuencias con DADA2 

La desreplicación de secuencias es un paso esencial en el análisis de datos de secuenciación de alto rendimiento (NGS, por sus siglas en inglés). DADA2 (Divisive Amplicon Denoising Algorithm 2) es una herramienta bioinformática diseñada para identificar variantes de secuencia de amplicones (ASVs, *Amplicon Sequence Variants*) con precisión a nivel de nucleótido único.  

## ¿Qué es la desreplicación de secuencias?
La desreplicación implica agrupar y contar secuencias idénticas en un conjunto de datos para reducir redundancia y facilitar el análisis. Este paso es crucial en estudios de microbioma para distinguir variantes reales de errores introducidos por el proceso de secuenciación.  

#### Principales aplicaciones de DADA2
- **Análisis de microbiomas:**  
   DADA2 es ampliamente utilizado en estudios de ecología microbiana para analizar comunidades bacterianas, arqueas y fúngicas. Permite identificar ASVs sin depender de límites arbitrarios como los usados en los enfoques basados en OTUs (*Operational Taxonomic Units*).  
   
- **Salud humana:**  
   Ayuda en investigaciones sobre la microbiota intestinal, vinculando comunidades microbianas con enfermedades como obesidad, diabetes y trastornos gastrointestinales.  

- **Ecosistemas y medio ambiente:**  
   Se emplea para caracterizar comunidades microbianas en suelos, océanos y otros ambientes, revelando interacciones ecológicas y ciclos biogeoquímicos.  

- **Estudios evolutivos y taxonómicos:**  
   DADA2 proporciona una base precisa para explorar la diversidad genética, lo que es clave para reconstruir relaciones filogenéticas y clasificar microorganismos.  

## Comparación con enfoques tradicionales
A diferencia de métodos que agrupan secuencias similares en OTUs basadas en un porcentaje de similitud, DADA2 opera a nivel de nucleótido, eliminando el ruido técnico y generando resultados más reproducibles y comparables entre estudios.  

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./02_fundamentosDADA2.md)