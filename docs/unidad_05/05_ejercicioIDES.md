# **Ejercicio de Uso de Editores de Texto en Línea de Comandos: Nano y Vi**

En este ejercicio, vamos a explorar los editores de texto en línea de comandos más utilizados: **Nano** y **Vi** (o **Vim**, su versión mejorada). Ambos son herramientas poderosas para editar archivos directamente desde la terminal, pero tienen características y formas de interactuar muy diferentes. A lo largo de este ejercicio, practicarás las operaciones básicas y algunas características avanzadas de ambos editores.

### **Objetivos del ejercicio:**
1. Crear y editar archivos de texto con **Nano** y **Vi**.
2. Aprender las operaciones básicas de edición, guardado y salida.
3. Explorar algunas funciones avanzadas como búsqueda, navegación y personalización de estos editores.

## **Usando Nano**

**Nano** es un editor de texto simple y fácil de usar en la terminal. Se destaca por su interfaz intuitiva y la visualización de los atajos de teclado en la parte inferior de la pantalla.

### **Abrir un archivo con Nano**
1. Abre tu terminal.
2. Escribe el siguiente comando para crear o editar un archivo de texto:
   ```bash
   nano archivo_de_prueba.txt
   ```
   Si el archivo no existe, Nano lo creará automáticamente.

### **Operaciones básicas en Nano**
- **Escribir texto**: Comienza a escribir el texto directamente en la pantalla.
- **Guardar el archivo**: Para guardar el archivo, presiona `Ctrl + O`. Nano te pedirá confirmar el nombre del archivo. Presiona `Enter` para confirmarlo.
- **Salir de Nano**: Para salir del editor, presiona `Ctrl + X`. Si no has guardado tus cambios, Nano te preguntará si deseas hacerlo.

### **Navegación en el archivo**
- **Moverte por el archivo**: Usa las teclas de las flechas del teclado para moverte por el archivo.
- **Buscar texto**: Para buscar un texto dentro del archivo, presiona `Ctrl + W` e ingresa la palabra que deseas buscar.
- **Cortar y pegar texto**: Para cortar texto, presiona `Ctrl + K` y para pegarlo, presiona `Ctrl + U`.

### **Ejercicio práctico en Nano**
1. Abre Nano y escribe el siguiente texto:
   ```text
   Esto es un archivo de prueba en Nano.
   Vamos a aprender a editar con Nano.
   ```
2. Guarda el archivo y sal del editor.

## **Usando Vi (o Vim)**

**Vi** es un editor mucho más poderoso pero también más complejo que Nano. Vi tiene varios modos de operación, como el modo de comando y el modo de inserción.

### **Abrir un archivo con Vi**
1. Abre tu terminal.
2. Escribe el siguiente comando para abrir o crear un archivo en Vi:
   ```bash
   vi archivo_de_prueba_vi.txt
   ```

### **Modos de Vi**
- **Modo de comando**: Este es el modo predeterminado. En este modo, puedes moverte por el archivo, borrar líneas, copiar y pegar, pero no puedes escribir directamente.
- **Modo de inserción**: Para escribir, primero debes estar en el modo de inserción. Para entrar en el modo de inserción, presiona `i`.

### **Operaciones básicas en Vi**
1. **Escribir texto**: Presiona `i` para entrar en el modo de inserción y empieza a escribir.
2. **Guardar y salir**: Cuando termines de escribir, presiona `Esc` para salir del modo de inserción y volver al modo de comando.
   - Para guardar el archivo, escribe `:w` y presiona `Enter`.
   - Para salir de Vi, escribe `:q` y presiona `Enter`.
   - Si deseas guardar y salir al mismo tiempo, escribe `:wq` y presiona `Enter`.
   - Si deseas salir sin guardar cambios, escribe `:q!` y presiona `Enter`.

### **Navegación y búsqueda en Vi**
- **Moverse por el archivo**: Usa las teclas de las flechas o las teclas `h`, `j`, `k`, `l` para moverte.
   - `h`: mover a la izquierda
   - `j`: mover hacia abajo
   - `k`: mover hacia arriba
   - `l`: mover a la derecha
- **Buscar texto**: Para buscar una palabra en el archivo, presiona `/` seguido de la palabra que deseas buscar. Luego presiona `Enter`. Para buscar la siguiente aparición de la palabra, presiona `n`.
- **Borrar texto**: Para borrar una letra, estando en el modo de comando, presiona `x`. Para borrar una línea completa, escribe `dd`.
- **Copiar y pegar texto**: Para copiar una línea, presiona `yy`. Para pegarla, presiona `p`.

### **Ejercicio práctico en Vi**
1. Abre Vi y escribe el siguiente texto (en modo de inserción):
   ```text
   Esto es un archivo de prueba en Vi.
   Vamos a aprender a editar con Vi.
   ```
2. Guarda el archivo y sal de Vi.

## **Comparación entre Nano y Vi**

Ahora que has practicado con ambos editores, compara las diferencias principales entre ellos:

| Característica          | **Nano**                         | **Vi (o Vim)**                      |
|-------------------------|----------------------------------|-------------------------------------|
| **Interfaz**            | Interfaz simple y amigable       | Basado en comandos, más complejo    |
| **Modos de operación**  | No tiene modos, siempre en modo edición | Modo de inserción y modo de comando |
| **Curva de aprendizaje**| Baja, fácil para principiantes  | Alta, requiere tiempo para aprender |
| **Velocidad**           | Más lento en archivos grandes    | Muy rápido y eficiente en archivos grandes |
| **Características avanzadas** | Limitadas                    | Amplias, con muchas extensiones y configuraciones |

### **Contesta**

Después de completar el ejercicio, responde a las siguientes preguntas para reflexionar sobre tu experiencia:

1. ¿Con cuál editor te sentiste más cómodo y por qué?
2. ¿Qué aspectos de Vi te parecieron más difíciles de aprender?
3. ¿En qué situaciones crees que Nano sería más útil que Vi?
4. Si tuvieras que elegir uno de estos editores para un proyecto grande, ¿cuál elegirías y por qué?
