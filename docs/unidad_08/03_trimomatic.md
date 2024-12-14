# **Trimmomatic: Filtrado y Recorte de Lecturas en Datos de Secuenciación NGS**

El filtrado y recorte de lecturas es una de las etapas más críticas en el procesamiento de datos de secuenciación de nueva generación (NGS), especialmente para mejorar la calidad de las lecturas antes de realizar análisis más profundos. **Trimmomatic** es una herramienta de software ampliamente utilizada para realizar estas tareas. Su función principal es recortar las lecturas para eliminar bases de baja calidad y secuencias adaptadoras, lo que asegura que solo las lecturas de alta calidad sean utilizadas en los análisis posteriores, como el alineamiento o ensamblaje.

## **¿Qué es Trimmomatic?**

Trimmomatic es un software diseñado para recortar y filtrar lecturas de secuenciación. Es compatible con archivos de datos en formato FASTQ y permite realizar varias operaciones de recorte en función de la calidad de las bases, la longitud de las lecturas y la presencia de secuencias adaptadoras.

Entre las funcionalidades más destacadas de Trimmomatic se incluyen:
- **Recorte de bases de baja calidad**: Elimina bases que tienen una puntuación de calidad baja.
- **Eliminación de adaptadores**: Recorta las secuencias adaptadoras presentes en las lecturas, que son añadidas durante la preparación de las bibliotecas de secuenciación.
- **Recorte de lecturas muy cortas**: Descarta lecturas que, después de ser recortadas, son demasiado cortas para ser útiles.
- **Recorte con ventana deslizante**: Recorta las bases de las lecturas según un umbral de calidad en una ventana deslizante a lo largo de la secuencia.

## **Instalación de Trimmomatic**

Trimmomatic es una herramienta que se ejecuta en la línea de comandos, y está escrita en Java, lo que la hace compatible con múltiples plataformas (Linux, Windows, macOS). 

Para instalar Trimmomatic, primero se necesita tener Java instalado en el sistema. Posteriormente, se puede descargar el archivo .jar desde su repositorio oficial y ejecutarlo directamente desde la terminal o línea de comandos. La instalación no requiere dependencias adicionales si Java está correctamente configurado.

## **Principales Funciones y Parámetros de Trimmomatic**

Trimmomatic ofrece una variedad de opciones de filtrado y recorte que se pueden combinar para mejorar la calidad de las lecturas:

### **Recorte de Adaptadores**

Las secuencias adaptadoras son secuencias cortas que se agregan a las lecturas durante la preparación de la biblioteca de secuenciación para ayudar a la amplificación y la alineación. Sin embargo, estas secuencias no pertenecen al organismo objetivo y deben eliminarse para evitar que interfieran con el análisis.

**Ejemplo de comando para recortar adaptadores**:

```bash
java -jar trimmomatic-0.39.jar PE input_R1.fastq input_R2.fastq output_R1_paired.fastq output_R1_unpaired.fastq output_R2_paired.fastq output_R2_unpaired.fastq ILLUMINACLIP:adapter.fa:2:30:10
```

- `ILLUMINACLIP`: Especifica el archivo de adaptadores (en este caso, `adapter.fa`).
- Los valores `2:30:10` son parámetros que controlan la cantidad mínima de coincidencias, el número máximo de errores permitidos y la diferencia mínima de longitud entre el adaptador y la secuencia de la lectura, respectivamente.

### **Recorte por Calidad de Bases**

Trimmomatic permite recortar las bases de baja calidad en las lecturas. La calidad de las bases se mide generalmente mediante puntuaciones Phred, donde una puntuación mayor indica mayor confiabilidad en la base secuenciada.

**Ejemplo de comando para recortar por calidad de bases**:

```bash
java -jar trimmomatic-0.39.jar SE input.fastq output_trimmed.fastq SLIDINGWINDOW:4:20
```

- `SLIDINGWINDOW:4:20`: Este parámetro utiliza una ventana deslizante de 4 bases y recorta las lecturas cuando la calidad promedio de la ventana es menor a 20. Esto asegura que las lecturas se recorten para eliminar las bases de baja calidad que podrían afectar los análisis posteriores.

### **Recorte de Lecturas Cortas**

Después de recortar adaptadores o bases de baja calidad, algunas lecturas pueden volverse demasiado cortas para ser útiles. Trimmomatic permite filtrar estas lecturas para asegurar que solo se utilicen lecturas que cumplan con un mínimo de longitud.

**Ejemplo de comando para filtrar lecturas cortas**:

```bash
java -jar trimmomatic-0.39.jar SE input.fastq output_trimmed.fastq MINLEN:36
```

- `MINLEN:36`: Este parámetro elimina todas las lecturas que son más cortas que 36 bases, lo que asegura que solo las lecturas suficientemente largas se utilicen en los análisis posteriores.

### **Recorte de Lecturas con Ventana Deslizante**

Una de las características más poderosas de Trimmomatic es el recorte de lecturas utilizando un método de ventana deslizante. Esto implica evaluar un segmento de la secuencia y recortar las bases de baja calidad dentro de una ventana definida. Si el valor promedio de calidad dentro de la ventana es inferior a un umbral determinado, las bases son eliminadas.

**Ejemplo de comando para el recorte con ventana deslizante**:

```bash
java -jar trimmomatic-0.39.jar SE input.fastq output_trimmed.fastq SLIDINGWINDOW:4:15
```

- `SLIDINGWINDOW:4:15`: Recorta la secuencia de 4 bases en 4 bases cuando la calidad promedio dentro de la ventana de 4 bases es inferior a 15.

### **3Recorte de Secuencias de Baja Calidad (Leading y Trailing)**

Trimmomatic también permite recortar bases de baja calidad al principio (leading) o al final (trailing) de la lectura. Esta operación es útil cuando se sabe que las primeras o últimas bases de la lectura son de baja calidad.

**Ejemplo de comando para el recorte de bases al principio y final**:

```bash
java -jar trimmomatic-0.39.jar SE input.fastq output_trimmed.fastq LEADING:3 TRAILING:3
```

- `LEADING:3`: Recorta bases de calidad inferior a 3 al principio de la lectura.
- `TRAILING:3`: Recorta bases de calidad inferior a 3 al final de la lectura.

## **Uso de Trimmomatic en un Pipeline de Análisis de NGS**

Trimmomatic es frecuentemente utilizado en combinación con otras herramientas dentro de un pipeline de análisis de NGS. Un flujo de trabajo típico para procesar datos de secuenciación podría incluir:

1. **Evaluación inicial de la calidad**: Utilizar herramientas como FastQC para examinar la calidad de las lecturas antes del procesamiento.
2. **Filtrado y recorte con Trimmomatic**: Eliminar bases de baja calidad, secuencias adaptadoras y lecturas cortas.
3. **Evaluación posterior de la calidad**: Volver a evaluar la calidad de las lecturas filtradas con FastQC para asegurarse de que el filtrado haya sido efectivo.
4. **Análisis downstream**: Realizar análisis de alineación, ensamblaje o anotación utilizando herramientas como BWA, STAR o Bowtie2.

## **Consideraciones Importantes al Usar Trimmomatic**

- **Parámetros ajustables**: Trimmomatic ofrece una gran cantidad de parámetros que pueden ajustarse para cumplir con las necesidades específicas del proyecto. Es importante experimentar con diferentes configuraciones y valores de calidad para encontrar la mejor configuración para los datos en cuestión.
  
- **Impacto en el análisis downstream**: Un filtrado demasiado agresivo puede eliminar demasiadas lecturas, lo que podría afectar el poder estadístico de los análisis posteriores. Por lo tanto, es fundamental equilibrar el recorte con la cantidad de datos que se utilizan.

- **Alineamiento posterior**: Si se van a realizar alineamientos de las lecturas recortadas, es importante tener en cuenta que los recortes pueden alterar el tamaño de las lecturas, lo que podría afectar la precisión del alineamiento, especialmente si las lecturas se recortan de manera desigual.

Trimmomatic es una herramienta poderosa y flexible para el procesamiento de datos de secuenciación, que ayuda a mejorar la calidad de las lecturas al eliminar bases de baja calidad, secuencias adaptadoras y lecturas cortas. Al integrarlo en un flujo de trabajo adecuado, los investigadores pueden asegurar que solo las lecturas más confiables se utilicen en los análisis posteriores, lo que aumenta la precisión y fiabilidad de los resultados obtenidos en los estudios de NGS.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./04_integracion.md)