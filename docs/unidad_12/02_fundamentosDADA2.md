# Fundamentos Teóricos

DADA2 implementa un enfoque algorítmico riguroso para diferenciar errores de secuenciación de variantes reales. Esto se logra mediante modelado estadístico y desreplicación iterativa.  

## Variantes de secuencia de amplicones (ASVs)
Las ASVs son unidades de diversidad genética definidas por secuencias exactas. Representan una mejora significativa frente a las OTUs, que dependen de umbrales arbitrarios de similitud (generalmente el 97%).  

### Principios matemáticos detrás de DADA2
El núcleo del algoritmo DADA2 se basa en los siguientes pasos:  
1. **Desreplicación inicial:**  
   Todas las secuencias idénticas son agrupadas, eliminando redundancia en el conjunto de datos. Esto reduce el ruido y facilita el procesamiento computacional.  

2. **Modelado de errores de secuenciación:**  
   - DADA2 ajusta un modelo probabilístico de errores específico para cada ejecución de secuenciación.  
   - Este modelo estima la probabilidad de que una secuencia observada sea un error derivado de una variante real.  

3. **Inferencia de variantes reales:**  
   Mediante un proceso iterativo, el algoritmo identifica variantes reales basándose en la probabilidad ajustada por el modelo de errores.  

4. **Remoción de quimeras:**  
   Las quimeras, generadas por recombinación artefactual durante la amplificación por PCR, son detectadas y eliminadas para garantizar la precisión de los resultados.  

## Ventajas del enfoque de DADA2
- **Precisión:**  
   Al operar a nivel de nucleótido, DADA2 elimina el ruido técnico y asegura que cada ASV corresponde a una variante real.  

- **Comparabilidad:**  
   Los resultados obtenidos con DADA2 pueden compararse entre estudios, ya que no dependen de umbrales arbitrarios.  

- **Eficiencia computacional:**  
   Aunque el proceso puede ser intensivo en cómputo, la desreplicación inicial y el modelado estadístico optimizan el análisis para grandes conjuntos de datos.  

## Limitaciones y consideraciones
- **Calidad de datos:**  
   DADA2 requiere datos de secuenciación de alta calidad para producir resultados confiables.  
- **Curva de aprendizaje:**  
   Su implementación puede ser compleja para usuarios sin experiencia en programación o bioinformática.  

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./03_instalaciónDADA2.md)