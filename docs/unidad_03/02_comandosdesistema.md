# **Comandos Básicos de Linux**

Los comandos básicos de Linux son esenciales para interactuar con el sistema operativo, gestionar archivos, navegar por el sistema de archivos y realizar tareas administrativas. A continuación, se describen algunos de los comandos más comunes y utilizados en Linux para realizar estas acciones.

## **`pwd` - Imprimir el directorio de trabajo actual**
El comando `pwd` (Print Working Directory) se utiliza para mostrar la ruta completa del directorio actual en el que nos encontramos dentro del sistema de archivos de Linux.

**Uso:**
```bash
pwd
```

**Ejemplo de salida:**
```
/home/usuario
```

Este comando es útil para saber en qué directorio estamos trabajando cuando nos movemos por el sistema de archivos.

#### **`ls` - Listar archivos y directorios**
El comando `ls` se utiliza para listar los archivos y directorios en el directorio actual. Puede ser complementado con varias opciones para mostrar información adicional sobre los archivos.

**Uso básico:**
```bash
ls
```

**Opciones comunes:**
- `ls -l`: Muestra una lista detallada, que incluye permisos, propietario, tamaño y fecha de modificación.
- `ls -a`: Muestra todos los archivos, incluidos los ocultos (aquellos cuyo nombre empieza con un punto `.`).
- `ls -lh`: Muestra la lista con tamaños legibles para humanos (por ejemplo, en KB, MB, GB).

**Ejemplo de salida de `ls -l`:**
```
drwxr-xr-x 2 usuario usuario 4096 dic 12 09:30 documentos
-rw-r--r-- 1 usuario usuario   123 dic 12 09:00 archivo.txt
```

## **`cd` - Cambiar de directorio**
El comando `cd` (Change Directory) se utiliza para cambiar el directorio de trabajo actual.

**Uso:**
```bash
cd /ruta/del/directorio
```

- `cd ..`: Cambia al directorio superior (sube un nivel en la jerarquía).
- `cd ~`: Cambia al directorio home del usuario actual.
- `cd /`: Cambia al directorio raíz del sistema.

**Ejemplo:**
```bash
cd /home/usuario/documentos
```

## **`mkdir` - Crear un directorio**
El comando `mkdir` (Make Directory) se utiliza para crear un nuevo directorio dentro del directorio actual.

**Uso:**
```bash
mkdir nombre_del_directorio
```

**Ejemplo:**
```bash
mkdir proyectos
```

Este comando creará un directorio llamado "proyectos" en el directorio actual.


## *`rmdir` - Eliminar un directorio vacío**
El comando `rmdir` se utiliza para eliminar un directorio vacío. Si el directorio contiene archivos o subdirectorios, el comando no funcionará.

**Uso:**
```bash
rmdir nombre_del_directorio
```

**Ejemplo:**
```bash
rmdir proyectos
```

## **`rm` - Eliminar archivos y directorios**
El comando `rm` (Remove) se utiliza para eliminar archivos y directorios. Se debe tener cuidado con este comando, ya que los archivos eliminados con `rm` no se pueden recuperar fácilmente.

**Uso para eliminar archivos:**
```bash
rm archivo.txt
```

**Uso para eliminar directorios y su contenido:**
```bash
rm -r directorio
```

**Opciones útiles:**
- `rm -i`: Pide confirmación antes de eliminar cada archivo.
- `rm -f`: Fuerza la eliminación sin preguntar confirmación.
- `rm -rf`: Elimina recursivamente directorios y su contenido sin confirmación.

**Ejemplo:**
```bash
rm -rf /home/usuario/temporal
```
## **`cp` - Copiar archivos y directorios**
El comando `cp` se utiliza para copiar archivos o directorios de una ubicación a otra.

**Uso para copiar archivos:**
```bash
cp archivo_origen archivo_destino
```

**Uso para copiar directorios:**
```bash
cp -r directorio_origen directorio_destino
```

**Ejemplo:**
```bash
cp archivo.txt /home/usuario/documentos
```
## **`mv` - Mover o renombrar archivos y directorios**
El comando `mv` se utiliza tanto para mover archivos y directorios de un lugar a otro como para renombrarlos.

**Uso para mover archivos:**
```bash
mv archivo_origen /ruta/destino
```

**Uso para renombrar archivos:**
```bash
mv archivo_viejo archivo_nuevo
```

**Ejemplo:**
```bash
mv archivo.txt /home/usuario/documentos
mv archivo.txt archivo_nuevo.txt
```

## **`touch` - Crear archivos vacíos**
El comando `touch` se utiliza para crear archivos vacíos o para actualizar la fecha de acceso y modificación de archivos existentes.

**Uso:**
```bash
touch archivo.txt
```

**Ejemplo:**
```bash
touch nuevo_archivo.txt
```

Este comando creará un archivo vacío llamado "nuevo_archivo.txt" si no existe, o actualizará su fecha de modificación si ya existe.

#### **`cat` - Ver el contenido de un archivo**
El comando `cat` (concatenate) se utiliza para mostrar el contenido de un archivo en la terminal.

**Uso:**
```bash
cat archivo.txt
```

**Ejemplo:**
```bash
cat documento.txt
```

Este comando mostrará todo el contenido de "documento.txt" en la terminal.

## **`man` - Consultar las páginas de manual de los comandos**
El comando `man` se utiliza para mostrar la página de manual de un comando, proporcionando información detallada sobre su uso, opciones y ejemplos.

**Uso:**
```bash
man comando
```

**Ejemplo:**
```bash
man ls
```

Esto abrirá el manual del comando `ls`, donde podrás ver una descripción completa de sus opciones y cómo usarlo correctamente.

Estos son algunos de los comandos básicos que todo usuario de Linux debería conocer. Dominar estos comandos te permitirá navegar eficientemente por el sistema de archivos, gestionar archivos y directorios, y realizar tareas cotidianas en la terminal de Linux. A medida que avances en tu uso de Linux, aprenderás más comandos y herramientas que ampliarán aún más tus capacidades dentro del sistema operativo.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./03_ejerciciosistema.md)