# **Formatos Estructurales en Bioinformática**

Los formatos estructurales en bioinformática son fundamentales para representar y analizar la estructura tridimensional de biomoléculas, principalmente proteínas y ácidos nucleicos. Estos formatos permiten almacenar, intercambiar y procesar información sobre cómo se pliegan y organizan las moléculas en el espacio, lo que es crucial para entender su función biológica, interacciones moleculares y mecanismos de acción. Existen diversos formatos estandarizados para representar estructuras biológicas, cada uno adaptado a diferentes tipos de datos y necesidades de análisis.

## **Formato PDB (Protein Data Bank)**

**Definición:**
El formato PDB (Protein Data Bank) es el estándar más utilizado para representar estructuras tridimensionales de macromoléculas como proteínas, ARN y complejos proteína-ácido nucleico. Cada entrada en un archivo PDB corresponde a una estructura tridimensional específica, que puede incluir coordenadas atómicas, información sobre las cadenas polipeptídicas, residuos, enlaces y otras características estructurales.

**Estructura:**
Un archivo PDB contiene varias secciones, pero las más relevantes incluyen:
- **Cabecera**: Información sobre la entrada, como el identificador único, el título, los autores y las fuentes experimentales (por ejemplo, cristalografía de rayos X, RMN, etc.).
- **Átomos**: Las coordenadas atómicas (X, Y, Z) de los átomos en la estructura de la proteína o el ácido nucleico. Cada átomo está representado por una línea con su nombre, tipo de átomo, número de residuo, coordenadas y otros detalles.
- **Conectividad**: Enlaces covalentes y no covalentes entre átomos, residuos y cadenas.
- **Cadenas**: Identificadores de las cadenas polipeptídicas o de ARN que conforman la estructura.

**Ejemplo de línea PDB:**
```
ATOM      1  N   ALA A   1      11.104  12.255  13.786  1.00 20.00           N
ATOM      2  CA  ALA A   1      11.341  13.701  14.324  1.00 20.00           C
```

**Usos comunes:**
- Almacenar y compartir estructuras de proteínas y ácidos nucleicos.
- Visualización de estructuras 3D en herramientas como PyMOL, Chimera, y VMD.
- Análisis de interacciones moleculares, diseño de fármacos y predicción de funciones biológicas.

## **Formato CIF (Crystallographic Information File)**

**Definición:**
El formato CIF (Crystallographic Information File) es utilizado principalmente en la cristalografía de rayos X para describir la estructura tridimensional de cristales. Es una alternativa al formato PDB y se emplea para almacenar los datos derivados de los experimentos de difracción de rayos X, incluidos los parámetros de la celda unitaria y las posiciones atómicas de los átomos en la estructura cristalina.

**Estructura:**
El formato CIF es más detallado que el PDB en términos de los parámetros cristalográficos, y contiene información sobre:
- **Celdas unitarias**: Parámetros que describen el tamaño y la orientación de la celda unitaria del cristal.
- **Atomos**: Las posiciones atómicas y sus ocupaciones en el cristal.
- **Datos experimentales**: Resultados del análisis de difracción de rayos X, como intensidades y factores de escala.

**Ejemplo de entrada CIF:**
```
data_example
_cell_length_a   10.043
_cell_length_b   12.314
_cell_length_c   15.232
_atom_site_label  N
_atom_site_occupancy  1.00
_atom_site_fract_x  0.234
_atom_site_fract_y  0.235
_atom_site_fract_z  0.123
```

**Usos comunes:**
- Almacenamiento y análisis de estructuras cristalinas.
- Intercambio de datos de difracción entre laboratorios y software especializado.
- Estudio de estructuras más complejas que pueden requerir una descripción más detallada que la proporcionada por el formato PDB.

## **Formato MMDB (Molecular Modeling Database)**

**Definición:**
El formato MMDB es un formato utilizado por el NCBI para almacenar y gestionar estructuras moleculares obtenidas por diferentes métodos experimentales, como la cristalografía de rayos X, la espectroscopía de resonancia magnética nuclear (RMN) y la modelización por homología.

**Estructura:**
Los archivos MMDB contienen representaciones estructurales de macromoléculas con información detallada sobre las posiciones atómicas, el tipo de átomo y las interacciones entre átomos. A menudo, los archivos MMDB también incluyen información adicional sobre las predicciones estructurales, como los dominios proteicos o los modelos de predicción de la estructura.

**Usos comunes:**
- Almacenamiento de modelos estructurales generados por simulaciones de dinámica molecular o modelado por homología.
- Visualización y análisis de estructuras biomoleculares en el contexto de bases de datos biológicas.

## **Formato .PSE (PyMOL Session File)**

**Definición:**
El formato .PSE es utilizado por el software PyMOL para guardar sesiones de trabajo, es decir, el estado completo de un análisis estructural. Un archivo .PSE puede contener no solo la estructura molecular y sus coordenadas, sino también la configuración de la vista 3D, los colores y otros parámetros visuales establecidos durante la sesión.

**Estructura:**
El archivo .PSE no sigue una estructura simple de texto plano, sino que es un formato binario que guarda todos los elementos visuales y estructurales que se han manipulado en PyMOL.

**Usos comunes:**
- Guardar y compartir sesiones de trabajo de análisis estructurales en PyMOL.
- Facilitar la revisión de resultados complejos en contextos colaborativos.
- Exportación de configuraciones para presentaciones o publicaciones científicas.

## **Formato DX (Distributed Computing Environment Grid)**

**Definición:**
El formato DX es utilizado principalmente para representar estructuras tridimensionales de datos en computación distribuida, especialmente en simulaciones de dinámica molecular. Se utiliza para almacenar datos de las simulaciones en formatos que pueden ser fácilmente manipulados por sistemas distribuidos o paralelizados.

**Estructura:**
El formato DX describe la estructura y la configuración de los datos 3D generados por simulaciones, incluyendo:
- **Malla**: Una estructura de malla que define las posiciones y valores asociados a cada punto.
- **Coordenadas de átomos**: Información sobre las ubicaciones de los átomos o partículas simuladas.
- **Propiedades**: Datos sobre las propiedades de la simulación, como energías, fuerzas, etc.

**Usos comunes:**
- Almacenar y analizar grandes volúmenes de datos generados en simulaciones moleculares distribuidas.
- Facilitar la visualización de grandes estructuras moleculares en aplicaciones como VMD o Chimera.

Los formatos estructurales en bioinformática permiten almacenar y compartir representaciones detalladas de estructuras tridimensionales de biomoléculas. Cada formato está diseñado para cumplir con necesidades específicas de visualización, análisis y almacenamiento, y es crucial para los estudios en áreas como la biología estructural, el diseño de fármacos y la investigación sobre proteínas y ácidos nucleicos. La selección adecuada del formato depende del tipo de análisis, el software utilizado y el tipo de información que se desea extraer de la estructura biomolecular.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./05_formatometadatos.md)