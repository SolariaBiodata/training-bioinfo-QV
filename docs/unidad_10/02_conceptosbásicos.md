# Conceptos Básicos del Ensamble de Secuencias

A continuación, se detallan los conceptos clave que forman la base de este proceso:

#### **Lecturas (*Reads*)**

Las lecturas son fragmentos de secuencias de ADN o ARN generados por una tecnología de secuenciación, como Illumina, PacBio o Oxford Nanopore. Estas lecturas son la unidad básica con la que se trabaja en un proceso de ensamble y pueden ser de distintos tamaños y calidades.

- **Lecturas Cortas**: Son secuencias de longitud relativamente corta (generalmente de 100 a 300 bases) producidas por plataformas como Illumina. Estas lecturas son de alta precisión, pero son limitadas en cuanto a la cobertura de secuencias repetitivas o regiones complejas del genoma.
  
- **Lecturas Largas**: Se refieren a secuencias más largas (generalmente más de 1000 bases) generadas por plataformas como PacBio o Oxford Nanopore. Estas lecturas permiten cubrir de forma más eficaz regiones repetitivas y complejas, aunque suelen ser más propensas a errores de secuenciación.

#### **Contigs y Scaffolds**

- **Contigs**: Es una secuencia de ADN continua que ha sido ensamblada a partir de un conjunto de lecturas que se solapan. En otras palabras, un contig es una secuencia resultante de la combinación de varias lecturas que se alinean correctamente y se extienden de forma continua. La longitud de un contig depende de la cantidad y la calidad de las lecturas utilizadas en el ensamblaje.

- **Scaffolds**: Es una estructura más compleja que contiene varios contigs unidos por información adicional, como la distancia estimada entre ellos, proporcionada por lecturas largas o por mapas de ligación (métodos que proporcionan información sobre la posición relativa de los contigs). Los scaffolds permiten una representación más completa y organizada de la secuencia genómica, aunque a veces no son tan continuos como los contigs debido a la falta de información precisa en algunas regiones.

#### **Cobertura**

Se refiere al número de veces que una región del genoma es leída durante el proceso de secuenciación. Una mayor cobertura significa que hay más lecturas cubriendo una misma región, lo que mejora la precisión y la confiabilidad del ensamble. 

- **Cobertura alta**: Es ideal para mejorar la calidad del ensamble, especialmente en regiones complejas del genoma. Sin embargo, una cobertura excesiva puede ser costosa sin un beneficio significativo en el resultado final.
  
- **Cobertura baja**: Puede dar lugar a regiones del genoma que no están bien representadas o incluso a gaps (huecos) en el ensamblaje, lo que puede afectar la calidad y la precisión del genoma reconstruido.

#### **Profundidad**

La profundidad es similar y se refiere al número total de lecturas que cubren un genoma en su totalidad.

#### **Secuencias Repetitivas**

Son segmentos del ADN que aparecen múltiples veces en el genoma. Estas secuencias pueden causar problemas durante el ensamble, ya que las lecturas de diferentes ubicaciones repetitivas pueden alinearse de forma incorrecta, generando ambigüedades.

Las secuencias repetitivas son comunes en muchos genomas, y su presencia es un desafío para las plataformas de secuenciación que generan lecturas cortas, ya que las lecturas pueden no poder diferenciar entre las copias repetidas. Las lecturas largas ayudan a superar en parte este problema, ya que pueden abarcar más de una repetición a la vez.

#### **Algoritmos de Ensamble**

Los algoritmos de ensamble son las herramientas matemáticas y computacionales que guían el proceso de ensamblaje. Dependiendo del enfoque (de novo o basado en referencia), los algoritmos utilizan diferentes técnicas para organizar y combinar las lecturas. Existen dos tipos de algoritmos principales:

- **Algoritmos basados en grafos**: Estos algoritmos, como los basados en **grafos de De Bruijn**, dividen las lecturas en k-mers (fragmentos de longitud k) y las ensamblan al buscar solapamientos entre estos k-mers. Este enfoque es popular para el ensamble de novo.

- **Algoritmos overlap-layout-consensus (OLC)**: Este enfoque se utiliza principalmente para el ensamble de lecturas largas. Primero, se encuentra el solapamiento entre las lecturas, luego se organizan en un gráfico de layout, y finalmente se genera un consenso de las lecturas que están alineadas.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./03_aplicacionesdelensamblaje.md)