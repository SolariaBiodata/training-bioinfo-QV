# **Ejercicio Práctico de Comandos con `grep`, `awk` y Redirección (`|`, `>`, `>>`)**

### **Escenario**:
Tienes un archivo llamado `registros.txt` que contiene información de ventas diarias en el siguiente formato:
```
2024-12-01,Juan Pérez,Electrónica,500
2024-12-01,Ana López,Alimentos,200
2024-12-02,Juan Pérez,Electrónica,300
2024-12-02,Ana López,Ropa,150
2024-12-03,Carlos Ruiz,Electrónica,400
```

El objetivo es analizar este archivo para obtener diferentes estadísticas y crear reportes.

## **Ejercicio 1: Filtrar Ventas por Categoría y Guardar en un Archivo**

**Paso 1:** Usa `grep` para encontrar todas las líneas que contienen la palabra "Electrónica" y redirígelas a un archivo llamado `ventas_electronica.txt`.

```bash
grep "Electrónica" registros.txt > ventas_electronica.txt
```

**Resultado esperado:**  
El archivo `ventas_electronica.txt` debe contener todas las ventas relacionadas con la categoría "Electrónica".

## **Ejercicio 2: Calcular el Total de Ventas por Persona**

**Paso 1:** Usa `awk` para sumar el total de ventas de cada persona y redirige el resultado a un archivo llamado `total_ventas.txt`.

```bash
awk -F',' '{suma[$2] += $4} END {for (persona in suma) print persona, suma[persona]}' registros.txt > total_ventas.txt
```

**Explicación:**
- `-F','`: Define la coma como delimitador de campos.
- `suma[$2] += $4`: Suma el valor del cuarto campo (monto de ventas) para cada persona (segundo campo).
- `END {for (persona in suma) print persona, suma[persona]}`: Imprime el total acumulado para cada persona.

## **Ejercicio 3: Filtrar Ventas Altas y Añadir al Archivo de Reportes**

**Paso 1:** Filtra las ventas mayores a 300 y añade el resultado al final de un archivo llamado `reporte_ventas_altas.txt`.

```bash
awk -F',' '$4 > 300 {print $0}' registros.txt >> reporte_ventas_altas.txt
```

**Resultado esperado:**  
El archivo `reporte_ventas_altas.txt` debe contener todas las líneas con ventas superiores a 300.

## **Ejercicio 4: Combinar Comandos con Pipes para Análisis Rápido**

**Paso 1:** Encuentra las líneas con "Juan Pérez", extrae solo el monto de las ventas y suma el total usando `awk`.

```bash
grep "Juan Pérez" registros.txt | awk -F',' '{suma += $4} END {print "Total de ventas de Juan Pérez:", suma}'
```

**Explicación:**
- `grep "Juan Pérez"`: Filtra las líneas donde aparece "Juan Pérez".
- `awk -F',' '{suma += $4} END {print "Total de ventas de Juan Pérez:", suma}'`: Suma el valor de las ventas y muestra el total.

#### [Menú Principal](../../index.md)
#### [Índice](./index.md)