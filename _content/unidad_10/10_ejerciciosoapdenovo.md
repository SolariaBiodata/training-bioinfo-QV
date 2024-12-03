# Ejercicio Práctico: Ensamblaje de Secuencias con SOAPdenovo

#### **Objetivo:**
Ensamblar un conjunto de lecturas de secuenciación usando SOAPdenovo para generar un contig o genoma ensamblado.

### **Paso 1: Preparación de los Datos**

Antes de comenzar con el ensamblaje, debes preparar tus datos de secuenciación. En este ejemplo, supongamos que tienes lecturas de secuenciación en formato FASTQ.

1. Si tus lecturas están en pares (paired-end), asegúrate de tener dos archivos de lectura: uno para las lecturas "forward" (`reads_1.fq`) y otro para las lecturas "reverse" (`reads_2.fq`).

2. Si tienes un solo archivo de lecturas (single-end), solo necesitarás un archivo (`reads.fq`).

3. Realiza una evaluación preliminar de la calidad de tus lecturas con herramientas como **FastQC** para verificar que no haya problemas evidentes en las lecturas.

---

### **Paso 2: Creación del Archivo de Configuración**

SOAPdenovo requiere un archivo de configuración para ejecutar el ensamblaje. Este archivo incluye detalles sobre las lecturas y los parámetros de ensamblaje. Para crear este archivo, sigue los pasos:

1. Crea un archivo de configuración llamado `soapdenovo.config`:
   ```bash
   nano soapdenovo.config
   ```

2. Agrega la siguiente estructura básica al archivo de configuración (ajusta según tu situación):

   ```text
   [LIB]
   # Tipo de secuenciación (si es paired-end o single-end)
   name = my_read_data
   shortPaired = reads_1.fq reads_2.fq
   # Si es single-end, usa:
   # shortSingle = reads.fq

   [ASSEMBLY]
   # Parámetros de ensamblaje
   k = 31
   # El valor de k debe ser un número impar
   ```

   - **`k`**: Este es el tamaño del *k-mer* que se usará durante el ensamblaje. Un valor típico es `31`, pero puedes experimentar con otros valores dependiendo de la longitud de tus lecturas.

---

### **Paso 3: Ejecutar SOAPdenovo para Ensamblaje**

Una vez que el archivo de configuración esté listo, puedes ejecutar el ensamblaje. Si tus lecturas están en formato *paired-end*, el comando sería:

```bash
./SOAPdenovo-127mer all -s soapdenovo.config -o my_assembly_output -K 31
```

- **`-s`**: Especifica el archivo de configuración.
- **`-o`**: Especifica el nombre del directorio de salida donde se guardarán los archivos del ensamblaje.
- **`-K`**: Especifica el valor de `k` para el ensamblaje (el tamaño del *k-mer*).

Si tus lecturas son *single-end*, el comando sería similar pero con el archivo de entrada único.

---

### **Paso 4: Evaluación del Ensamblaje**

Después de ejecutar el ensamblaje, SOAPdenovo generará varios archivos en el directorio de salida que contienen los resultados del ensamblaje.

1. **Archivos principales generados:**
   - `my_assembly_output.contig`: Contiene los contigs ensamblados.
   - `my_assembly_output.scaf`: Contiene los scaffolds ensamblados.
   - Otros archivos de log y estadísticos.

2. Para evaluar la calidad del ensamblaje, puedes utilizar herramientas como **QUAST** para obtener métricas como la longitud total del ensamblaje, el número de contigs, el N50, etc.

   Ejemplo de ejecución de QUAST:
   ```bash
   quast.py my_assembly_output.contig -o quast_output
   ```
### **Paso 5: Análisis y Visualización**

Una vez que hayas ensamblado las lecturas y evaluado la calidad del ensamblaje, puedes proceder a realizar análisis adicionales, como:

- **Análisis de variantes** (por ejemplo, SNPs y indels).
- **Análisis funcional** (asociación con bases de datos de genes y funciones biológicas).
- **Visualización**: Puedes usar herramientas como **IGV** para visualizar los contigs y scaffolds en el genoma de referencia.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./11_ejercicioquast.md)