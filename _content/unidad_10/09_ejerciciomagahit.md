# Ejercicio Práctico: Ensamble de Secuencias con MEGAHIT

**Objetivo:** El objetivo de este ejercicio es utilizar MEGAHIT, una herramienta eficiente para el ensamblaje de genomas a partir de datos de secuenciación de alto rendimiento, para ensamblar una muestra de secuencias y evaluar los resultados.

**Materiales Necesarios:**
- Acceso a un entorno de computación (servidor o máquina local) con MEGAHIT instalado.
- Archivos de secuenciación en formato FASTQ (lecturas de secuenciación). Puedes usar un conjunto de datos de ejemplo disponible en bases de datos públicas o generar datos simulados.
- Herramientas de evaluación de ensamblajes (por ejemplo, QUAST, BUSCO, etc.).

### **Paso 1: Preparación de Datos**
Supongamos que tienes archivos de secuenciación en formato FASTQ, que son comúnmente generados por plataformas de secuenciación como Illumina o Nanopore. Para este ejercicio, utilizarás dos archivos de lecturas, por ejemplo:

- `sample_1.fastq` (lectura de adelante)
- `sample_2.fastq` (lectura de atrás, si es un ensamblaje paired-end)

Si estás trabajando con lecturas uniparadas (single-end), solo necesitarás un archivo.

### **Paso 2: Ejecución de MEGAHIT**

#### **Ensamblaje con Lecturas Paired-End**
Si tienes un archivo de lecturas paired-end, ejecuta el siguiente comando:

```bash
megahit -1 sample_1.fastq -2 sample_2.fastq -o output_assembly
```

- `-1` especifica el archivo de lecturas en el sentido 1.
- `-2` especifica el archivo de lecturas en el sentido 2.
- `-o` especifica el directorio de salida donde se guardarán los resultados del ensamblaje.

#### **Ensamblaje con Lecturas Single-End**
Si estás trabajando con lecturas uniparadas, el comando será más simple:

```bash
megahit -r sample.fastq -o output_assembly
```

- `-r` especifica el archivo de lecturas single-end.
- `-o` especifica el directorio de salida.

### **Paso 3: Evaluación del Ensamblaje**

Después de que MEGAHIT complete el ensamblaje, generará un directorio de salida con varios archivos, incluidos los contigs ensamblados.

Para evaluar la calidad del ensamblaje, puedes usar herramientas como **QUAST** o **BUSCO**.

#### **Usando QUAST:**

QUAST es una herramienta comúnmente usada para evaluar la calidad de un ensamblaje. Para usarlo, ejecuta el siguiente comando:

```bash
quast.py output_assembly/final.contigs.fa -o quast_results
```

- `output_assembly/final.contigs.fa` es el archivo de contigs ensamblados.
- `-o quast_results` especifica el directorio donde se guardarán los resultados de la evaluación.

QUAST te proporcionará varias métricas clave del ensamblaje, como la longitud total del ensamblaje, el número de contigs, la N50 (una medida de la calidad del ensamblaje) y más.

#### **Usando BUSCO:**

BUSCO se utiliza para evaluar la completitud de un ensamblaje basado en la presencia de genes centrales específicos de un grupo taxonómico. Para usarlo:

1. Instala BUSCO siguiendo las instrucciones de su página oficial.
2. Ejecuta el siguiente comando para evaluar la completitud del ensamblaje:

```bash
busco -i output_assembly/final.contigs.fa -l bacteria_odb10 -o busco_results -m genome
```

- `-i` especifica el archivo de entrada (en este caso, los contigs ensamblados).
- `-l` especifica la base de datos de BUSCO correspondiente a tu organismo (en este ejemplo, es para bacterias).
- `-o` especifica el directorio de salida.
- `-m genome` especifica que estás evaluando un genoma completo.

### **Paso 4: Interpretación de los Resultados**

Una vez completado el ensamblaje y la evaluación, revisa los resultados generados por QUAST y BUSCO para evaluar la calidad de tu ensamblaje. Algunas métricas clave a observar son:

- **N50**: Una métrica que indica el tamaño de los contigs más largos que representan el 50% de la longitud total del ensamblaje. Un N50 alto generalmente indica un ensamblaje de buena calidad.
- **Completo vs incompleto** (en BUSCO): Esto te dirá cuántos genes core (esenciales) de tu organismo de interés están presentes en el ensamblaje. Un porcentaje alto indica que el ensamblaje es completo.

### **Paso 5: Refinamiento del Ensamblaje**

Si el ensamblaje no es lo suficientemente bueno, puedes considerar las siguientes estrategias para mejorarlo:

- **Ajustar parámetros de MEGAHIT**: Experimenta con diferentes valores de parámetros, como el tamaño de los k-mers, para mejorar el ensamblaje.
  
  Por ejemplo:
  
  ```bash
  megahit -1 sample_1.fastq -2 sample_2.fastq -o output_assembly --k-min 21 --k-max 99
  ```

- **Uso de datos adicionales**: Si es posible, añadir más datos de secuenciación o usar tecnologías complementarias (como PacBio para lecturas largas) puede mejorar la calidad del ensamblaje.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./10_ejerciciosoapdenovo.md)