# **Expresiones Regulares Básicas**

#### **¿Qué son las Expresiones Regulares?**  
Las **expresiones regulares (regex)** son patrones utilizados para buscar y manipular texto. Permiten identificar, extraer o reemplazar cadenas de caracteres basándose en reglas definidas. En Linux, se emplean ampliamente en herramientas como `grep`, `sed` y `awk` para el manejo eficiente de datos.

## **Elementos Clave de las Expresiones Regulares Básicas**

1. **Caracteres Literales**  
   Representan texto exacto.  
   - Ejemplo: Buscar "error" en un archivo.  
     ```bash
     grep "error" archivo.txt
     ```

2. **Metacaracteres**  
   Son símbolos con un significado especial que permiten crear patrones dinámicos y flexibles.  
   Los más comunes son:  
   - **`.` (punto):** Coincide con cualquier carácter excepto una nueva línea.  
     Ejemplo:  
     ```bash
     grep "e.r" archivo.txt
     ```
     Encuentra "ear", "err", "e1r", etc.  

   - **`^` (inicio de línea):** Coincide con el comienzo de una línea.  
     Ejemplo:  
     ```bash
     grep "^Error" archivo.txt
     ```
     Encuentra líneas que comiencen con "Error".  

   - **`$` (fin de línea):** Coincide con el final de una línea.  
     Ejemplo:  
     ```bash
     grep "error$" archivo.txt
     ```
     Encuentra líneas que terminen con "error".  

   - **`*` (cero o más repeticiones):** Coincide con cero o más repeticiones del carácter anterior.  
     Ejemplo:  
     ```bash
     grep "a*" archivo.txt
     ```
     Encuentra líneas con secuencias como "", "a", "aa", "aaa", etc.  

   - **`[]` (conjunto de caracteres):** Coincide con cualquiera de los caracteres especificados.  
     Ejemplo:  
     ```bash
     grep "c[au]t" archivo.txt
     ```
     Encuentra "cat" y "cut".  

   - **`|` (alternancia):** Representa una lógica OR entre patrones.  
     Ejemplo:  
     ```bash
     grep "cat|dog" archivo.txt
     ```
     Encuentra líneas que contengan "cat" o "dog".  

## **Construcción de Patrones Básicos**  

1. **Uso de Conjuntos de Caracteres (`[]`):**  
   Permiten definir un rango o lista de caracteres aceptables.  
   - Ejemplo: Buscar palabras que comiencen con "c" y terminen en "t", con una vocal intermedia.  
     ```bash
     grep "c[aeiou]t" archivo.txt
     ```
     Encuentra "cat", "cet", "cit", etc.  

2. **Rangos en Conjuntos (`[a-z]`, `[0-9]`):**  
   Definen un rango de caracteres, útil para simplificar patrones.  
   - Ejemplo: Buscar líneas con letras minúsculas de la "a" a la "f".  
     ```bash
     grep "[a-f]" archivo.txt
     ```

3. **Carácter de Escape (`\`):**  
   Se usa para tratar metacaracteres como caracteres literales.  
   - Ejemplo: Buscar líneas que contengan un punto literal ("."):  
     ```bash
     grep "\." archivo.txt
     ```

Las expresiones regulares básicas son una herramienta poderosa para buscar patrones simples o ligeramente complejos en texto. Una vez dominados los conceptos básicos, pueden expandirse con patrones avanzados para manejar escenarios más específicos y complejos. Su uso en herramientas como `grep` permite realizar análisis rápidos y efectivos en cualquier archivo de texto o flujo de datos.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)
#### [Siguiente](./04_herramientascomplementarias.md)