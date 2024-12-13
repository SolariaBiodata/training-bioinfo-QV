# **Introducción a la Navegación en Linux**

Linux es un sistema operativo basado en el núcleo de Linux que es ampliamente utilizado por su estabilidad, seguridad y flexibilidad. La navegación por el sistema de archivos en Linux puede parecer compleja al principio debido a su estructura jerárquica, pero una vez comprendidos los conceptos clave y los comandos básicos, resulta ser muy eficiente. En este tema, abordaremos los fundamentos de la navegación en Linux, la estructura del sistema de archivos y los comandos más importantes para moverse y manipular archivos y directorios desde la línea de comandos.

## **Estructura del Sistema de Archivos en Linux**

El sistema de archivos en Linux sigue una estructura jerárquica de directorios, similar a un árbol, donde los directorios y archivos se organizan de forma jerárquica bajo un directorio raíz denominado `/`. A continuación, se presentan algunos de los directorios más comunes:

- `/`: El directorio raíz. Es el punto de partida para todas las rutas en el sistema de archivos de Linux.
- `/home`: Contiene los directorios personales de los usuarios del sistema. Cada usuario tiene un subdirectorio dentro de `/home`.
- `/etc`: Contiene archivos de configuración global del sistema.
- `/usr`: Contiene archivos de programas y bibliotecas adicionales instalados en el sistema.
- `/bin`: Contiene los programas binarios esenciales para la operación del sistema.
- `/var`: Contiene archivos que varían durante la operación del sistema, como registros del sistema y archivos temporales.

Esta estructura permite un acceso organizado y eficiente a los archivos y directorios del sistema, y la navegación por ella es una habilidad básica y esencial en la administración de sistemas Linux.

## **Rutas Absolutas y Relativas**

En Linux, hay dos formas de hacer referencia a un archivo o directorio: **rutas absolutas** y **rutas relativas**.

- **Ruta Absoluta**: Una ruta absoluta siempre comienza desde el directorio raíz `/` y especifica la ubicación completa de un archivo o directorio. Ejemplo: `/home/usuario/documentos`.
  
- **Ruta Relativa**: Una ruta relativa se especifica en relación con el directorio actual. No comienza desde el directorio raíz, sino desde el directorio en el que te encuentras. Ejemplo: si estás en `/home/usuario`, la ruta relativa a un archivo en el subdirectorio `documentos` sería simplemente `documentos`.


La navegación en Linux es un conjunto de habilidades esenciales para poder trabajar eficientemente en un sistema basado en Unix. Entender cómo moverse entre directorios, listar archivos, y localizar archivos específicos es fundamental para la administración del sistema. Los comandos `pwd`, `cd` y `ls` son los primeros pasos en la interacción con el sistema de archivos y forman la base para tareas más complejas. Con estos conocimientos, cualquier usuario puede empezar a explorar y gestionar el sistema de archivos de Linux de manera efectiva.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./02_comandosbásicos.md)