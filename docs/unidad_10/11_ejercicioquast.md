# Ejercicio sobre Validación del Ensamble usando QUAST

**Objetivo del ejercicio:** Aprender a usar QUAST para validar la calidad de un ensamblaje de secuencias genómicas y comprender las métricas que proporciona.

1. **Preparación de Archivos:**
   Asegúrate de tener los siguientes archivos:
   - `assembly.fasta`: El archivo de secuencias ensambladas generado por tu herramienta de ensamblaje (como SPAdes, Velvet, etc.).
   - `reference_genome.fasta`: (opcional, si tienes un genoma de referencia con el que comparar el ensamblaje). Si no tienes un genoma de referencia, puedes omitir esta parte y comparar solo las métricas internas del ensamblaje.

2. **Comando Básico de QUAST:**
   Abre una terminal y navega a la carpeta donde se encuentran los archivos. Ejecuta el siguiente comando para iniciar la validación básica del ensamblaje:

   ```bash
   quast.py assembly.fasta -o quast_output
   ```

   Este comando analizará el ensamblaje y guardará los resultados en un directorio llamado `quast_output`.

   **Explicación del comando:**
   - `assembly.fasta`: El archivo de secuencias ensambladas.
   - `-o quast_output`: Directorio donde se almacenarán los resultados del análisis.

3. **Ejecutar QUAST con un Genoma de Referencia (opcional):**
   Si tienes un genoma de referencia, puedes incluirlo en el análisis con el siguiente comando:

   ```bash
   quast.py assembly.fasta -R reference_genome.fasta -o quast_output
   ```

   **Explicación del comando:**
   - `-R reference_genome.fasta`: El archivo de genoma de referencia para comparar la calidad del ensamblaje.

4. **Revisión de los Resultados:**
   Después de ejecutar QUAST, se generarán varios archivos dentro del directorio `quast_output`. Algunos de los archivos importantes son:

   - `report.html`: Un informe visual que muestra las métricas del ensamblaje, incluidas las comparaciones con el genoma de referencia (si se proporcionó).
   - `report.txt`: Un informe de texto con las métricas detalladas.
   - `contigs_per_read.png`: Un gráfico que muestra el número de contigs por longitud de lectura.
   - `scaffold.png`: Un gráfico que muestra el número de scaffolds.
   - `stats_summary.txt`: Un resumen de estadísticas clave del ensamblaje.

5. **Interpretación de las Métricas:**
   En el informe (`report.html` o `report.txt`), QUAST proporciona varias métricas clave que te ayudarán a evaluar la calidad de tu ensamblaje. Algunas de las métricas más importantes son:

   - **N50**: La longitud del contig (o scaffold) que cubre al menos el 50% del genoma ensamblado. Un valor más alto de N50 indica un ensamblaje más completo.
   - **Total Length**: La longitud total de todas las secuencias ensambladas.
   - **Contig y Scaffold Count**: El número de contigs (fragmentos) y scaffolds (grupos de contigs ensamblados) generados.
   - **Misassemblies**: El número de errores en el ensamblaje que se detectan al comparar con el genoma de referencia.
   - **GC Content**: El contenido de guanina y citosina, que ayuda a verificar si el ensamblaje refleja correctamente la composición del genoma.

6. **Métricas adicionales (si se incluye un genoma de referencia):**
   Si proporcionaste un genoma de referencia, QUAST también calculará las siguientes métricas:

   - **Identidad con la referencia**: El porcentaje de similitud entre el ensamblaje y el genoma de referencia.
   - **Cobertura de la referencia**: El porcentaje de la referencia que está cubierto por el ensamblaje.
   - **Errores de ensamblaje**: Comparación entre las regiones del ensamblaje que coinciden con el genoma de referencia y aquellas que no.

7. **Optimización del Ensamblaje (si es necesario):**
   Si observas problemas de calidad en el ensamblaje, como un N50 bajo o muchos errores de ensamblaje, es posible que necesites ajustar los parámetros del ensamblaje o intentar con otro conjunto de herramientas de ensamblaje. Por ejemplo:
   - Asegúrate de que las lecturas de entrada sean de alta calidad (usando herramientas como **FastQC** o **Trimmomatic** para filtrarlas).
   - Si estás usando un ensamblaje de corto alcance, podrías intentar usar un ensamblaje híbrido combinando lecturas de corto y largo alcance (por ejemplo, SPAdes con lecturas de PacBio o Nanopore).

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)