### **Comandos Básicos para Navegar por el Sistema de Archivos en Linux**

El sistema de archivos en Linux es una jerarquía de directorios en la que los archivos y carpetas están organizados en una estructura de árbol, comenzando desde un directorio raíz `/`. La navegación por este sistema de archivos se realiza principalmente desde la línea de comandos, utilizando una serie de comandos que permiten desplazarse entre directorios, listar archivos, y verificar la ubicación actual. Los tres comandos básicos para la navegación en el sistema de archivos de Linux son `pwd`, `cd` y `ls`.

---

#### **1. Comando `pwd` (Print Working Directory)**

El comando `pwd` es utilizado para mostrar la ruta del directorio en el que te encuentras actualmente en el sistema de archivos. Este comando es útil cuando no estás seguro de tu ubicación o si deseas confirmar en qué directorio estás trabajando.

**Sintaxis:**
```bash
pwd
```

**Ejemplo:**
```bash
$ pwd
/home/usuario
```
- **Explicación:** En este ejemplo, el comando `pwd` muestra que el usuario se encuentra en el directorio `/home/usuario`.

El comando `pwd` siempre devuelve la ruta completa (absoluta) desde la raíz del sistema de archivos, lo que significa que se incluye todo el camino desde el directorio raíz `/`.

---

#### **2. Comando `cd` (Change Directory)**

El comando `cd` se utiliza para cambiar de directorio dentro del sistema de archivos. Puedes utilizar rutas absolutas o relativas para indicar el directorio al que deseas navegar. 

- **Ruta Absoluta:** Comienza desde el directorio raíz `/` y especifica la ruta completa hacia el directorio deseado.
- **Ruta Relativa:** Se refiere al directorio en relación con el directorio actual. No se incluye la ruta completa desde la raíz.

**Sintaxis:**
```bash
cd [ruta_del_directorio]
```

**Ejemplos:**

- **Navegar a un directorio absoluto:**
  ```bash
  $ cd /home/usuario/documentos
  ```

  Esto te lleva al directorio `/home/usuario/documentos`, sin importar dónde te encuentres actualmente.

- **Navegar a un directorio relativo:**
  Si estás en el directorio `/home/usuario` y deseas acceder a `documentos` (que está dentro de tu directorio actual), puedes usar:
  ```bash
  $ cd documentos
  ```

- **Volver al directorio anterior:**
  Para regresar al directorio anterior en el que estabas, usa:
  ```bash
  $ cd -
  ```

- **Subir un nivel en la jerarquía:**
  El comando `cd ..` te permite subir al directorio padre (el directorio que está por encima del directorio actual).
  ```bash
  $ cd ..
  ```

- **Ir al directorio home del usuario:**
  El comando `cd ~` te lleva directamente al directorio home del usuario, sin importar dónde estés.
  ```bash
  $ cd ~
  ```

---

#### **3. Comando `ls` (List)**

El comando `ls` se utiliza para listar los archivos y directorios contenidos en el directorio actual. Es uno de los comandos más comunes y permite ver el contenido del directorio de una manera ordenada.

**Sintaxis:**
```bash
ls [opciones]
```

**Ejemplos de uso:**

- **Listar archivos y directorios:**
  ```bash
  $ ls
  ```
  Esto muestra una lista simple de los archivos y carpetas dentro del directorio actual.

- **Listar archivos con más detalles:**
  Si deseas ver más información sobre los archivos, como permisos, propietario, tamaño y fecha de modificación, puedes usar la opción `-l` (long format):
  ```bash
  $ ls -l
  ```

  **Salida esperada:**
  ```
  drwxr-xr-x 2 usuario usuario 4096 dic  1 10:22 documentos
  -rw-r--r-- 1 usuario usuario   52 dic  1 10:15 archivo.txt
  ```

  En esta salida, puedes ver el tipo de archivo (directorio `d` o archivo regular `-`), los permisos, el propietario, el tamaño y la fecha de modificación.

- **Listar todos los archivos, incluidos los ocultos:**
  En Linux, los archivos y directorios ocultos comienzan con un punto `.` (por ejemplo, `.bashrc`). Para listarlos, usa la opción `-a`:
  ```bash
  $ ls -a
  ```

  **Salida esperada:**
  ```
  .  ..  .bashrc  documentos  archivo.txt
  ```

- **Listar archivos de manera más legible:**
  Para ver tamaños de archivo en una forma más fácil de leer (por ejemplo, KB, MB), puedes usar la opción `-h` junto con `-l`:
  ```bash
  $ ls -lh
  ```

  **Salida esperada:**
  ```
  drwxr-xr-x 2 usuario usuario 4.0K dic  1 10:22 documentos
  -rw-r--r-- 1 usuario usuario  52K dic  1 10:15 archivo.txt
  ```

---

#### **Combinación de Comandos**

Puedes combinar estos comandos para hacer más eficiente la navegación:

- **Ver tu ubicación actual y listar el contenido del directorio:**
  Puedes usar `pwd` para ver tu ubicación y luego `ls` para listar el contenido del directorio:
  ```bash
  $ pwd
  /home/usuario
  $ ls
  documentos  archivo.txt
  ```

- **Navegar y listar contenido al mismo tiempo:**
  Si deseas cambiar de directorio y ver los archivos en ese directorio en un solo paso, puedes hacer lo siguiente:
  ```bash
  $ cd /home/usuario/documentos && ls
  ```

---

#### **Consejos Adicionales de Navegación**

- **Autocompletado con la tecla Tab**: La tecla `Tab` es útil para completar automáticamente nombres de archivos o directorios. Si comienzas a escribir una ruta o un nombre de archivo, presionar `Tab` completará el nombre si es único.
  
- **Historial de comandos**: Para ver el historial de los comandos que has ejecutado, puedes usar las teclas de flecha arriba (`↑`) y abajo (`↓`) para navegar por ellos. Esto es útil para repetir comandos sin tener que escribirlos de nuevo.

- **Comandos abreviados**: Puedes usar atajos para moverte más rápido:
  - `cd ~`: Va al directorio home.
  - `cd ..`: Sube un nivel en la jerarquía de directorios.
  - `ls -a`: Muestra todos los archivos, incluidos los ocultos.

---

### **Conclusión**

Los comandos `pwd`, `cd` y `ls` son los fundamentos para navegar por el sistema de archivos en Linux. Estos comandos permiten a los usuarios explorar y gestionar los archivos y directorios en su sistema, ofreciendo herramientas poderosas para interactuar con el entorno de la línea de comandos. Al dominar estos comandos, puedes realizar tareas básicas de administración de archivos y navegación de manera eficiente, lo que constituye la base para realizar tareas más avanzadas en Linux.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./03_ejerciciolinux.md)