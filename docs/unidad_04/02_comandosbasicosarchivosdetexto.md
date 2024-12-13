# Comandos Básicos para Manipular Archivos de Texto en Linux

En Linux, existe una variedad de comandos que permiten manipular archivos de texto de manera sencilla y eficiente. Estos comandos son fundamentales para cualquier tarea de administración de archivos o automatización de procesos. A continuación, se describen los comandos más utilizados para trabajar con archivos de texto en Linux.

## **`cat`**: Concatenar y Mostrar Archivos
El comando `cat` (abreviatura de "concatenate") se utiliza para mostrar el contenido de un archivo en la terminal. También se puede usar para concatenar varios archivos de texto en uno solo.

- **Mostrar el contenido de un archivo:**
  ```bash
  cat archivo.txt
  ```
- **Concatenar varios archivos en uno:**
  ```bash
  cat archivo1.txt archivo2.txt > archivo_combinado.txt
  ```
- **Agregar contenido a un archivo existente:**
  ```bash
  cat archivo2.txt >> archivo1.txt
  ```
  Aquí, el contenido de `archivo2.txt` se añade al final de `archivo1.txt`.

#### 2. **`more` y `less`**: Paginación de Archivos
Cuando se trabaja con archivos grandes, los comandos `more` y `less` permiten visualizar su contenido página por página.

- **`more`**: Muestra el archivo una página a la vez y permite avanzar hacia adelante, pero no retroceder.
  ```bash
  more archivo.txt
  ```
- **`less`**: Similar a `more`, pero ofrece más flexibilidad, permitiendo tanto avanzar como retroceder.
  ```bash
  less archivo.txt
  ```

Para salir de `more` o `less`, se presiona la tecla `q`.

## **`head`**: Mostrar las Primeras Líneas de un Archivo
El comando `head` muestra las primeras líneas de un archivo de texto, por defecto muestra las primeras 10 líneas. Esto es útil cuando solo se necesita ver una muestra del contenido de un archivo grande.

- **Mostrar las primeras 10 líneas (por defecto):**
  ```bash
  head archivo.txt
  ```
- **Mostrar un número específico de líneas:**
  ```bash
  head -n 20 archivo.txt
  ```
  Este comando muestra las primeras 20 líneas del archivo.

## **`tail`**: Mostrar las Últimas Líneas de un Archivo
De manera similar a `head`, el comando `tail` se utiliza para mostrar las últimas líneas de un archivo. Esto es útil para ver logs o archivos que se actualizan continuamente.

- **Mostrar las últimas 10 líneas (por defecto):**
  ```bash
  tail archivo.txt
  ```
- **Mostrar un número específico de líneas:**
  ```bash
  tail -n 20 archivo.txt
  ```
- **Ver en tiempo real las actualizaciones de un archivo (útil para logs):**
  ```bash
  tail -f archivo.txt
  ```
  Este comando muestra las últimas líneas del archivo y sigue mostrando nuevas líneas a medida que se agregan al archivo.

## **`nl`**: Numerar las Líneas de un Archivo
El comando `nl` imprime el contenido de un archivo, pero con la diferencia de que agrega números de línea al principio de cada línea. Esto es útil cuando se necesita hacer referencia a líneas específicas en un archivo.

- **Numerar las líneas de un archivo:**
  ```bash
  nl archivo.txt
  ```

## **`tac`**: Mostrar el Contenido de un Archivo en Orden Inverso
El comando `tac` es una versión invertida de `cat`, ya que muestra el contenido de un archivo comenzando desde la última línea hacia la primera.

- **Mostrar el contenido en orden inverso:**
  ```bash
  tac archivo.txt
  ```

## **`echo`**: Imprimir Texto en la Terminal o en Archivos
El comando `echo` se utiliza para imprimir texto en la terminal o para redirigirlo a un archivo. Es útil para escribir texto en archivos o para generar contenido dinámicamente.

- **Imprimir texto en la terminal:**
  ```bash
  echo "Hola, mundo"
  ```
- **Escribir texto en un archivo:**
  ```bash
  echo "Nuevo contenido" > archivo.txt
  ```
  Esto sobrescribe el archivo con el nuevo contenido.
- **Agregar texto al final de un archivo:**
  ```bash
  echo "Texto adicional" >> archivo.txt
  ```
  Esto agrega el texto al final del archivo sin sobrescribir su contenido.

## **`cut`**: Extraer Columnas de un Archivo de Texto
El comando `cut` permite extraer porciones de texto de un archivo, basado en columnas delimitadas por un carácter específico (como una coma o un espacio).

- **Extraer una columna de un archivo CSV (por ejemplo, la primera columna):**
  ```bash
  cut -d "," -f 1 archivo.csv
  ```
  Aquí, `-d ","` especifica que las columnas están separadas por comas y `-f 1` indica que se extrae la primera columna.

#### 9. **`sort`**: Ordenar el Contenido de un Archivo
El comando `sort` ordena las líneas de un archivo de texto. Por defecto, ordena en orden alfabético, pero se pueden usar opciones para personalizar el tipo de ordenación.

- **Ordenar un archivo alfabéticamente:**
  ```bash
  sort archivo.txt
  ```
- **Ordenar en orden inverso:**
  ```bash
  sort -r archivo.txt
  ```

## **`uniq`**: Eliminar Líneas Duplicadas
El comando `uniq` elimina las líneas duplicadas de un archivo de texto, mostrando solo las líneas únicas. Para que funcione correctamente, el archivo debe estar ordenado.

- **Eliminar las líneas duplicadas:**
  ```bash
  sort archivo.txt | uniq
  ```

## **`wc`**: Contar Líneas, Palabras y Caracteres
El comando `wc` (word count) se utiliza para contar líneas, palabras y caracteres en un archivo de texto.

- **Contar las líneas de un archivo:**
  ```bash
  wc -l archivo.txt
  ```
- **Contar palabras y caracteres:**
  ```bash
  wc -w archivo.txt
  wc -c archivo.txt
  ```

Los comandos básicos para manipular archivos de texto en Linux son herramientas poderosas que permiten gestionar y procesar archivos de manera eficiente. A través de comandos como `cat`, `head`, `tail`, `echo` y otros, es posible visualizar, editar y analizar archivos de texto en el sistema. Estos comandos forman la base de muchos procesos automatizados y actividades administrativas en el entorno Linux.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./03_ejercicioarchivosdetexto.md)