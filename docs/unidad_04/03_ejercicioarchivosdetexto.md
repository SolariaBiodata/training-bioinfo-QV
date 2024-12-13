### Ejercicio Práctico sobre Comandos `mkdir`, `touch`, `head`, `top`, `rm`, `rmdir`, `history`

Este ejercicio te guiará a través del uso de algunos de los comandos más comunes en Linux para crear, gestionar, y eliminar archivos y directorios, así como obtener información del sistema.

#### 1. **Comando `mkdir`**: Crear un Directorio
- **Objetivo**: Crear un directorio llamado `proyecto` en tu directorio actual.
  
  ```bash
  mkdir proyecto
  ```

- **Objetivo**: Crear múltiples directorios de una sola vez. Crea los directorios `proyecto/docs`, `proyecto/src` y `proyecto/tests`.

  ```bash
  mkdir -p proyecto/docs proyecto/src proyecto/tests
  ```

#### 2. **Comando `touch`**: Crear Archivos Vacíos
- **Objetivo**: Crear un archivo vacío llamado `readme.txt` dentro del directorio `proyecto/docs`.
  
  ```bash
  touch proyecto/docs/readme.txt
  ```

- **Objetivo**: Crear varios archivos vacíos de una vez dentro del directorio `proyecto/src` (por ejemplo, `main.c`, `utils.c` y `helpers.c`).

  ```bash
  touch proyecto/src/main.c proyecto/src/utils.c proyecto/src/helpers.c
  ```

#### 3. **Comando `head`**: Ver las Primeras Líneas de un Archivo
- **Objetivo**: Ver las primeras 10 líneas del archivo `readme.txt` creado en el paso anterior.

  ```bash
  head proyecto/docs/readme.txt
  ```

- **Objetivo**: Ver las primeras 5 líneas del archivo `main.c` en `proyecto/src`.

  ```bash
  head -n 5 proyecto/src/main.c
  ```

#### 4. **Comando `top`**: Monitorear el Uso de Recursos del Sistema
- **Objetivo**: Ejecutar el comando `top` para monitorear el uso de CPU y memoria en tu sistema.

  ```bash
  top
  ```

  Nota: Este comando mostrará información en tiempo real sobre los procesos en ejecución. Para salir de `top`, presiona `q`.

#### 5. **Comando `rm`**: Eliminar Archivos
- **Objetivo**: Eliminar el archivo `readme.txt` dentro de `proyecto/docs`.

  ```bash
  rm proyecto/docs/readme.txt
  ```

- **Objetivo**: Eliminar todos los archivos `.c` dentro del directorio `proyecto/src`.

  ```bash
  rm proyecto/src/*.c
  ```

#### 6. **Comando `rmdir`**: Eliminar Directorios Vacíos
- **Objetivo**: Eliminar el directorio vacío `proyecto/tests`.

  ```bash
  rmdir proyecto/tests
  ```

- **Objetivo**: Intentar eliminar el directorio `proyecto/src` que aún tiene archivos (esto fallará).

  ```bash
  rmdir proyecto/src
  ```

  Para eliminar un directorio que no está vacío, debes usar `rm -r` (eliminar recursivamente).

  ```bash
  rm -r proyecto/src
  ```

#### 7. **Comando `history`**: Ver el Historial de Comandos
- **Objetivo**: Ver el historial de comandos ejecutados en tu terminal.

  ```bash
  history
  ```

- **Objetivo**: Buscar un comando específico en el historial (por ejemplo, `mkdir`).

  ```bash
  history | grep mkdir
  ```

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)