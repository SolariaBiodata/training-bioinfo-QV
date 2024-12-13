# **Ejercicio de Comandos Básicos de Linux**

#### **Objetivo:**
Crear y manipular archivos y directorios, visualizar información del sistema y limpiar los registros.

### **Paso 1: Crear directorios y archivos**

1. **Crear un directorio llamado "trabajo":**
   ```bash
   mkdir trabajo
   ```

2. **Crear un archivo dentro de ese directorio llamado "documento.txt":**
   ```bash
   touch trabajo/documento.txt
   ```

3. **Verificar que el archivo fue creado:**
   ```bash
   ls trabajo
   ```

   Deberías ver que "documento.txt" aparece en la lista.

### **Paso 2: Ver el contenido de un archivo**

1. **Escribir algo dentro del archivo para poder verlo después.**
   Puedes usar un editor de texto o hacerlo directamente con `echo`:
   ```bash
   echo "Este es un archivo de ejemplo" > trabajo/documento.txt
   ```

2. **Ver las primeras 10 líneas del archivo usando `head`:**
   ```bash
   head trabajo/documento.txt
   ```

   Como solo has escrito una línea, `head` mostrará la línea que has escrito.

### **Paso 3: Ver procesos en ejecución**

1. **Ver los procesos en ejecución con el comando `top`:**
   ```bash
   top
   ```

   - El comando `top` mostrará los procesos en ejecución en tiempo real, junto con información como el uso de CPU, memoria y más. Para salir de `top`, presiona `q`.

### **Paso 4: Eliminar archivos y directorios**

1. **Eliminar el archivo "documento.txt" utilizando `rm`:**
   ```bash
   rm trabajo/documento.txt
   ```

2. **Verificar que el archivo ha sido eliminado:**
   ```bash
   ls trabajo
   ```

   Deberías ver que el archivo ya no está presente.

3. **Eliminar el directorio "trabajo" usando `rmdir`:**
   ```bash
   rmdir trabajo
   ```

4. **Verificar que el directorio ha sido eliminado:**
   ```bash
   ls
   ```

   El directorio "trabajo" ya no debería aparecer.

### **Paso 5: Ver el historial de comandos ejecutados**

1. **Mostrar el historial de los comandos ejecutados en la terminal:**
   ```bash
   history
   ```

   Esto te mostrará una lista de los comandos que has ejecutado en el pasado.


### **Resumen del ejercicio:**
- **`mkdir trabajo`**: Crea un directorio llamado "trabajo".
- **`touch trabajo/documento.txt`**: Crea un archivo vacío dentro del directorio "trabajo".
- **`head trabajo/documento.txt`**: Muestra las primeras líneas del archivo "documento.txt".
- **`top`**: Muestra los procesos en ejecución en tiempo real.
- **`rm trabajo/documento.txt`**: Elimina el archivo "documento.txt".
- **`rmdir trabajo`**: Elimina el directorio "trabajo".
- **`history`**: Muestra el historial de comandos ejecutados en la terminal.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)