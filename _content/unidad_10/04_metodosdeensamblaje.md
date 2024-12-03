# Métodos de Ensamble de Secuencias

El ensamble de secuencias es el proceso de unir fragmentos cortos de ADN o ARN, llamados lecturas (*reads*), para reconstruir secuencias más largas y completas. Existen varios métodos para realizar el ensamble, y la elección del método adecuado depende de factores como el tipo de secuenciación (por ejemplo, lecturas cortas o largas), la disponibilidad de un genoma de referencia y el objetivo del estudio. Los métodos de ensamble pueden clasificarse principalmente en dos enfoques: de novo y basados en referencia, y en dos tipos de algoritmos: basados en grafos y basados en superposición. A continuación, se detallan estos métodos:

## Ensamble de Novo
El ensamble de novo (de cero) es un enfoque en el que no se dispone de un genoma de referencia. En lugar de alinear las lecturas contra un genoma conocido, el objetivo es construir el genoma de nuevo, utilizando solo las lecturas obtenidas a partir de la secuenciación. Este tipo de ensamble es común cuando se trabaja con especies no modeladas, cuya secuencia genómica no ha sido previamente documentada.

##### **Características del Ensamble de Novo**
- **Desafíos**: Este enfoque es más desafiante porque no hay un genoma de referencia que guíe el proceso de ensamble, lo que puede llevar a ambigüedades y errores en la reconstrucción de secuencias, especialmente en áreas de alta repetitividad.
- **Aplicaciones**: Se utiliza cuando no hay secuencias de referencia disponibles, como en el caso de especies no estudiadas, en la metagenómica o cuando se secuencian nuevos genomas de organismos.

##### **Métodos en Ensamble de Novo**
- **Método de Grafos de De Bruijn**: Este es uno de los enfoques más utilizados para el ensamble de novo. Se basa en dividir las lecturas en fragmentos más pequeños llamados *k-mers* (subsecuencias de longitud k) y construir un grafo que representa cómo se solapan estos fragmentos. El algoritmo busca los solapamientos entre los k-mers para ensamblar secuencias más largas.
  
- **Método Overlap-Layout-Consensus (OLC)**: Este enfoque se basa en primero identificar las lecturas que se solapan, luego organizarlas en un gráfico de disposición (layout) y, finalmente, generar un consenso de las lecturas solapadas. OLC es más adecuado para lecturas largas, ya que puede manejar de manera más eficiente las regiones repetitivas y complejas.

## Ensamble Basado en Referencia

El ensamble basado en referencia utiliza un genoma conocido de una especie relacionada como guía para alinear y ensamblar las lecturas. Este método es generalmente más rápido y eficiente que el ensamble de novo, ya que aprovecha la información previa disponible, lo que mejora la precisión del ensamblaje, especialmente en especies cuya genética está bien documentada.

##### **Características del Ensamble Basado en Referencia**:
- **Ventajas**: Es menos costoso computacionalmente y más preciso en la reconstrucción de secuencias genómicas, ya que se basa en un marco de referencia.
- **Aplicaciones**: Este método se utiliza principalmente cuando se secuencian genomas de especies que ya tienen un genoma de referencia bien caracterizado. También se emplea en estudios de variantes genéticas, como mutaciones, SNPs (polimorfismos de nucleótido único), indels (inserciones y deleciones), entre otros.

##### **Métodos en Ensamble Basado en Referencia**
- **Alineamiento por Mapeo (Mapping)**: En este enfoque, las lecturas obtenidas se alinean directamente con el genoma de referencia utilizando algoritmos de alineación como BWA (Burrows-Wheeler Aligner) o Bowtie. Una vez alineadas, se pueden identificar las variaciones genéticas entre la muestra y la referencia.
  
- **Ensambles Secuenciales (Sequential Assembly)**: Este tipo de ensamblaje también utiliza un genoma de referencia, pero en lugar de alinear todas las lecturas a la vez, realiza un ensamblaje secuencial por regiones genómicas, lo que puede ser útil en el análisis de segmentos específicos de interés.

## Algoritmos de Ensamble

Los algoritmos de ensamble son esenciales para procesar y combinar las lecturas de secuenciación. A continuación se describen los dos tipos más comunes:

##### **Algoritmos Basados en Grafos**
Los algoritmos basados en grafos son los más populares en el ensamble de secuencias, especialmente en el enfoque de **De Novo**. Estos algoritmos representan las lecturas como vértices en un grafo y los solapamientos entre ellas como aristas. 

- **Grafo de De Bruijn**: Este enfoque es ampliamente utilizado en la secuenciación de alto rendimiento. En lugar de alinear las lecturas completas, el algoritmo divide las lecturas en fragmentos de longitud fija (k-mers), lo que reduce la complejidad y el tamaño del grafo. El algoritmo intenta encontrar el camino más largo en el grafo, ensamblando las lecturas en secuencias más largas.

- **Grafo de Solapamiento**: Este tipo de grafo conecta directamente las lecturas que se solapan. Es útil cuando las lecturas son largas y cuando las secuencias tienen más solapamientos directos.

##### **Algoritmos Overlap-Layout-Consensus (OLC)**
El enfoque OLC es más adecuado para el ensamble de lecturas largas. Este método requiere que las lecturas se alineen inicialmente por solapamiento, luego se organizan en un diseño (layout) de contig y finalmente se genera un consenso de las lecturas solapadas. Aunque el método OLC puede ser más complejo y computacionalmente intensivo que los algoritmos basados en grafos, es efectivo cuando se tienen lecturas largas que abarcan regiones más complejas del genoma.

## **Métodos para Mejorar la Calidad del Ensamble**

Existen diversas estrategias para mejorar la calidad del ensamblaje, especialmente en el caso de secuenciación de alto rendimiento, donde las lecturas pueden tener errores. Algunas de estas estrategias incluyen:

- **Corrección de Errores**: Las lecturas generadas por secuenciación de alto rendimiento pueden contener errores. Los algoritmos de corrección de errores (por ejemplo, **Quake** o **Lighter**) se utilizan antes de iniciar el proceso de ensamblaje para mejorar la calidad de las lecturas y minimizar los errores durante el ensamblaje.
  
- **Uso de Lecturas Largas y Cortas**: El uso combinado de lecturas largas y cortas en el proceso de ensamble puede mejorar la calidad y la completitud del ensamblaje. Las lecturas largas permiten superar problemas de secuencias repetitivas, mientras que las lecturas cortas ofrecen una mayor precisión en la alineación.

- **Incorporación de Información Adicional**: En el caso del ensamble basado en referencia, la incorporación de mapas de ligación o datos de secuenciación de longitudes intermedias (por ejemplo, utilizando **PacBio** o **Oxford Nanopore**) puede proporcionar información adicional para superar ambigüedades en la reconstrucción de la secuencia.

## Aplicaciones de los Métodos de Ensamble

Cada método de ensamble tiene aplicaciones específicas dependiendo del tipo de proyecto:

- **Ensambles de Novo**: Son cruciales para el estudio de especies no modeladas o en proyectos de metagenómica donde no se dispone de un genoma de referencia.
- **Ensambles Basados en Referencia**: Se utilizan para estudiar genomas de especies modeladas o para la identificación de variaciones genéticas en estudios de genómica humana, animal o de plantas.
- **Ensambles Híbridos (Lecturas Cortas y Largas)**: Combinan lo mejor de ambos mundos, mejorando la precisión del ensamblaje y la cobertura de regiones complejas.

Los métodos de ensamble de secuencias continúan evolucionando, con nuevos algoritmos y tecnologías emergentes que permiten un ensamblaje más preciso y eficiente. La elección del método adecuado depende de la calidad y tipo de las lecturas disponibles, el objetivo del estudio y los recursos computacionales disponibles.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./05_herramientasdeensamblaje.md)