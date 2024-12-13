# **Ejercicio: Navegación por el sistema de archivos en Linux**

**Objetivo:** Practicar la navegación por el sistema de archivos de Linux usando los comandos `pwd`, `cd` y `ls`.

## **Comando `pwd` (Print Working Directory)**
1. Abre una terminal en tu sistema Linux.
2. Escribe el comando `pwd` y presiona Enter.
   - **Pregunta:** ¿Qué directorio te muestra el comando `pwd`?
   - **Respuesta esperada:** Te mostrará la ruta del directorio actual en el que te encuentras (por ejemplo, `/home/usuario`).

## **Comando `ls` (List)**
1. Escribe el comando `ls` y presiona Enter.
   - **Pregunta:** ¿Qué muestra el comando `ls`?
   - **Respuesta esperada:** Te muestra una lista de archivos y carpetas en el directorio actual.
2. Ahora, escribe `ls -l` y presiona Enter.
   - **Pregunta:** ¿Qué diferencia notas entre el comando `ls` y `ls -l`?
   - **Respuesta esperada:** El comando `ls -l` muestra información adicional como permisos, propietario, tamaño y fecha de modificación de los archivos.

#### **Parte 3: Comando `cd` (Change Directory)**
1. Usa el comando `cd` para moverte al directorio `/home` (puedes escribir `cd /home` y presionar Enter).
   - **Pregunta:** ¿Cómo cambió el directorio actual? Usa `pwd` para verificarlo.
   - **Respuesta esperada:** Después de ejecutar `cd /home`, al usar `pwd`, el directorio debería mostrar algo como `/home`.
   
2. Luego, usa `cd` para navegar al subdirectorio de tu usuario (por ejemplo, `cd usuario`).
   - **Pregunta:** ¿Dónde estás ahora? ¿Qué muestra `pwd`?
   - **Respuesta esperada:** Estarás en un subdirectorio dentro de `/home`, como `/home/usuario`.

3. Ahora, vuelve al directorio anterior usando el comando `cd ..` y verifica tu ubicación con `pwd`.
   - **Pregunta:** ¿Qué hizo el comando `cd ..`?
   - **Respuesta esperada:** El comando `cd ..` te lleva al directorio padre (en este caso, de `/home/usuario` a `/home`).

4. Finalmente, usa el comando `cd ~` para ir al directorio home de tu usuario.
   - **Pregunta:** ¿Qué hace `cd ~`?
   - **Respuesta esperada:** El comando `cd ~` te lleva al directorio home de tu usuario, sin importar en qué parte del sistema estés.

## **Combinación de `ls` y `cd`**
1. Usa `cd` para entrar a un directorio de tu elección (por ejemplo, si tienes una carpeta llamada `Documentos`, escribe `cd Documentos`).
2. Una vez dentro de ese directorio, usa el comando `ls` para listar los archivos y carpetas que contiene.
   - **Pregunta:** ¿Cuántos archivos o carpetas puedes ver? ¿Puedes identificar algún archivo interesante?
   - **Respuesta esperada:** Deberías ver los archivos y carpetas dentro de `Documentos`.

3. Prueba el comando `ls -a` en ese directorio.
   - **Pregunta:** ¿Qué archivos adicionales muestra el comando `ls -a`?
   - **Respuesta esperada:** El comando `ls -a` muestra todos los archivos, incluidos los archivos ocultos (aquellos que empiezan con un punto `.`).

   #### [Menú Principal](../../index.md)
   #### [Índice](./index.md)

