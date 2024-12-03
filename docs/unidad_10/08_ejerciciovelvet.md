# Ejercicio de Ensamblaje de Secuencias Genómicas con Velvet

En este ejercicio, utilizaremos **Velvet**, una herramienta popular para el ensamblaje de genomas de novo a partir de datos de secuenciación de corto alcance. Velvet es especialmente útil para ensamblar genomas de tamaño pequeño a mediano. Este ejercicio te guiará a través de la preparación de los datos y la ejecución del ensamblaje.

### **Paso 1: Preparación de los Datos de Secuenciación**

En este ejercicio, utilizaremos datos de secuenciación de ADN en formato **FASTQ** (lecturas de corto alcance). Puedes obtener un conjunto de datos de ejemplo desde plataformas públicas como el [NCBI SRA](https://www.ncbi.nlm.nih.gov/sra), o utilizar un conjunto de datos de lectura corta ya disponible.

**2.1 Preprocesamiento de Datos:**

1. Asegúrate de que tus archivos **FASTQ** están listos para el ensamblaje. Si es necesario, utiliza **FastQC** para evaluar la calidad de las lecturas:

   ```bash
   fastqc data.fastq
   ```

2. Si las lecturas tienen adaptadores o baja calidad, puedes usar herramientas como **Trimmomatic** o **BBMap** para recortarlas:

   ```bash
   bbmap.sh in1=data.fastq out=clean_data.fastq
   ```

### **Paso 2: Ejecutar Velvet para Ensamblaje de Secuencias**

Una vez que los datos están listos, puedes proceder al ensamblaje con Velvet. Para ello, primero crea un directorio de trabajo y mueve tus archivos de secuenciación allí.

**3.1 Creación de un directorio de trabajo:**

```bash
mkdir velvet_assembly
cd velvet_assembly
```

**3.2 Ejecutar Velvet:**

Supón que tienes lecturas de secuenciación almacenadas en un archivo llamado `clean_data.fastq`. Velvet requiere que se especifique el **k-mer length** (el tamaño de las secuencias que se usarán para ensamblar). Un valor común para el k-mer es **31**, pero puedes experimentar con otros tamaños.

Ejecuta Velvet con el siguiente comando (cambia `kmer_length` a 31 o el valor que prefieras):

```bash
velveth velvet_output_dir 31 -fastq -short -fastq -sequences clean_data.fastq
```

Explicación:
- **velveth**: Inicia el ensamblaje de Velvet.
- **velvet_output_dir**: El directorio de salida donde se almacenará el ensamblaje.
- **31**: El tamaño de k-mer (puedes experimentar con otros valores de k).
- **-fastq**: Indica que los datos de entrada están en formato FASTQ.
- **-short**: Especifica que las lecturas son de corto alcance.

**3.3 Ejecutar el ensamblaje:**

Una vez que Velvet haya procesado las lecturas, puedes ejecutar el ensamblaje real con el siguiente comando:

```bash
velvetg velvet_output_dir -exp_cov auto -cov_cutoff 10
```

Explicación:
- **velvetg**: Ejecuta el ensamblaje de Velvet.
- **velvet_output_dir**: El directorio donde se encuentran los resultados del primer paso.
- **-exp_cov auto**: Velvet ajustará automáticamente la cobertura esperada.
- **-cov_cutoff 10**: Configura un umbral de cobertura mínima para las lecturas que se ensamblarán.

### **Paso 3: Evaluación del Ensamblaje**

Una vez completado el ensamblaje, Velvet generará varios archivos en el directorio de salida (`velvet_output_dir`). Los archivos clave son:

- **contigs.fa**: Contiene las secuencias ensambladas (contigs).
- **log**: Un archivo de registro que proporciona información sobre el proceso de ensamblaje.

Puedes usar herramientas como **QUAST** o **BUSCO** para evaluar la calidad del ensamblaje generado:

**4.1 Evaluar con QUAST:**

```bash
quast velvet_output_dir/contigs.fa
```

**4.2 Evaluar con BUSCO:**

```bash
busco -i velvet_output_dir/contigs.fa -l bacteria_odb10 -o busco_results
```

Esto te dará una evaluación sobre la completitud y la calidad del ensamblaje.

### **Paso 4: Interpretación de los Resultados**

Una vez que hayas completado el ensamblaje y la evaluación, examina los resultados:

1. **Contigs**: Las secuencias ensambladas se encontrarán en el archivo `contigs.fa`. Analiza la longitud total del ensamblaje y el número de contigs.
   
2. **Completeness**: Los resultados de **BUSCO** o **QUAST** te proporcionarán métricas sobre la calidad del ensamblaje, como el número de genes completos, fragmentados o ausentes.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./09_ejerciciomagahit.md)