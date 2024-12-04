# Instalación y Configuración de DADA2

La correcta instalación y configuración de DADA2 es un paso esencial para garantizar un análisis eficiente y reproducible de datos de secuenciación. Este tema describe los requisitos previos, el proceso de instalación y los pasos iniciales para configurar el entorno de trabajo.  


### Requisitos previos

Antes de instalar DADA2, es importante asegurarse de que se cumplan ciertos requisitos básicos:  

1. **Sistema operativo compatible:**  
   - Windows, macOS o Linux.  
   - Aunque DADA2 funciona en diferentes plataformas, su instalación en sistemas basados en Linux suele ser más eficiente.  

2. **R y RStudio:**  
   - **R:** Versión 4.0 o superior (DADA2 depende de funciones avanzadas introducidas en versiones recientes).  
   - **RStudio:** Interfaz gráfica recomendada para trabajar con R.  

3. **Dependencias necesarias:**  
   - Paquetes de R como `BiocManager`, que permite instalar paquetes relacionados con bioinformática desde Bioconductor.  

4. **Datos iniciales:**  
   - Archivos de secuencias en formato FASTQ generados por plataformas como Illumina.  
   - Metadatos de las muestras, generalmente en formato CSV o TSV.  


##  Instalación de DADA2

### Instalar R y RStudio
1. Descarga R desde el [sitio oficial del CRAN](https://cran.r-project.org/).  
2. Instala RStudio desde su [sitio oficial](https://posit.co/download/rstudio-desktop/).  

### Instalar DADA2 usando BiocManager  
1. Abre RStudio.  
2. Ejecuta los siguientes comandos en la consola para instalar `DADA2`:  

```R
if (!requireNamespace("BiocManager", quietly = TRUE)) {
    install.packages("BiocManager")
}
BiocManager::install("dada2")
```

3. Verifica que la instalación fue exitosa cargando el paquete:  

```R
library(dada2)
```

Si no aparece ningún mensaje de error, el paquete está listo para usarse.  

### Instalar otras dependencias recomendadas
DADA2 puede requerir otros paquetes para tareas complementarias. Algunos paquetes útiles incluyen:  

```R
install.packages(c("ggplot2", "phyloseq", "vegan"))
```

---

## Configuración del Entorno de Trabajo 

### Organización de directorios**  
Para garantizar un flujo de trabajo organizado, estructura los archivos en carpetas específicas:  
- `/raw_data/` para los archivos FASTQ originales.  
- `/filtered_data/` para los archivos filtrados.  
- `/output/` para los resultados del análisis.  

### Carga de datos iniciales
Asegúrate de que los nombres de los archivos FASTQ sigan un patrón claro para facilitar su procesamiento. Por ejemplo:  
- `sample1_R1.fastq.gz` (lecturas forward).  
- `sample1_R2.fastq.gz` (lecturas reverse).  

Usa el siguiente código para listar los archivos en R:  

```R
path <- "ruta/a/raw_data"
list.files(path)
```

### Comprobación de calidad de datos
Es buena práctica generar gráficos de calidad antes de iniciar el procesamiento:  

```R
fnFs <- sort(list.files(path, pattern="_R1.fastq.gz", full.names = TRUE))
fnRs <- sort(list.files(path, pattern="_R2.fastq.gz", full.names = TRUE))

plotQualityProfile(fnFs[1:2]) # Para las primeras dos muestras (lecturas forward).
plotQualityProfile(fnRs[1:2]) # Para las primeras dos muestras (lecturas reverse).
```

### Configuración de parámetros
Define los parámetros para el filtrado y truncamiento basándote en los gráficos de calidad. Por ejemplo:  

```R
filtered_path <- "ruta/a/filtered_data"
filtFs <- file.path(filtered_path, paste0(basename(fnFs), "_filtered"))
filtRs <- file.path(filtered_path, paste0(basename(fnRs), "_filtered"))

filterAndTrim(fnFs, filtFs, fnRs, filtRs,
              truncLen = c(240, 200), # Truncar después de 240 y 200 bases.
              maxN = 0,              # No se permiten Ns.
              maxEE = c(2, 2),       # Máximo de 2 errores esperados.
              truncQ = 2,            # Truncar donde Q < 2.
              rm.phix = TRUE,        # Remover secuencias PhiX.
              compress = TRUE,       # Comprimir los archivos filtrados.
              multithread = TRUE)    # Paralelización.
```

---

## Verificación Final
Antes de proceder al análisis completo, verifica que todos los pasos iniciales se ejecutaron correctamente:  
- ¿Se cargaron todos los archivos?  
- ¿Los gráficos de calidad son aceptables?  
- ¿Se generaron archivos filtrados?  

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./04_pipelineDADA2.md)