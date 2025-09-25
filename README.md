
# Tarea – Administración de Infraestructuras  
**Actividad de Taller – 08/09/2025**


## 📌 Primera Parte – Filtros en Shell

### 1. Comandos básicos
bash
# Mostrar el contenido de un archivo
cat archivo.txt
`

👉 Muestra en pantalla el contenido completo del archivo.

bash
# Filtrar líneas que contengan la palabra "error"
cat archivo.txt | grep "error"


👉 Busca dentro del archivo y muestra solo las líneas que contienen la palabra **error**.

bash
# Contar la cantidad de líneas en un archivo
wc -l archivo.txt


👉 Cuenta la cantidad de líneas existentes en el archivo.

bash
# Mostrar solo las primeras 4 columnas de cada línea
cut -c1-4 archivo.txt


👉 Extrae únicamente los primeros 4 caracteres de cada línea.

---

### 2. Pipes y redirecciones

bash
# Filtrar, ordenar y contar líneas con "error"
cat archivo.txt | grep "error" | sort | wc -l


👉 Encadena varios filtros: primero busca líneas con "error", luego las ordena alfabéticamente y finalmente cuenta cuántas hay.

bash
# Redirigir salida a un archivo nuevo
echo "nueva linea" > salida.txt


👉 Crea o sobrescribe el archivo `salida.txt` con el texto indicado.

bash
# Agregar salida al final de un archivo existente
echo "otra linea" >> salida.txt


👉 Añade texto al final del archivo sin borrar lo anterior.

bash
# Redirigir entrada desde un archivo
wc -l < archivo.txt


👉 Toma el archivo como entrada para `wc` y devuelve la cantidad de líneas.

---

### 3. Nuevo comando combinado

bash
cat archivo.txt | tr ' ' '\n' | grep -v "^$" | sort | uniq -c | sort -nr | head -5


👉 Divide el texto en palabras, elimina líneas vacías, las ordena, cuenta repeticiones y muestra las 5 más frecuentes.
Este ejemplo cumple con la consigna de **construir un nuevo comando combinando filtros básicos**.

---

### 4. Uso de `awk`

bash
echo -e "Juan,20\nAna,22\nLuis,19" > datos.csv
awk -F, '{print $1}' datos.csv


👉 Crea un archivo CSV y con `awk` (usando la coma como delimitador) imprime la primera columna: los nombres.

---

### 5. Uso de `sed`

bash
# Reemplazar todas las apariciones de "error" por "ok"
sed 's/error/ok/g' archivo.txt


👉 Edita el flujo de datos sustituyendo cada aparición de “error” por “ok”.


# Eliminar la segunda línea del archivo
sed '2d' archivo.txt


👉 Muestra el contenido del archivo sin la línea número 2.



## 📌 Segunda Parte – Filtros Propios

### 1. Script en Bash – `filtro.sh`


#!/bin/bash
# Convierte todo el texto a mayúsculas
tr 'a-z' 'A-Z'


Ejecución:


chmod +x filtro.sh
cat archivo.txt | ./filtro.sh


👉 Convierte todo el contenido de `archivo.txt` a mayúsculas.

---

### 2. Programa en C – `filtro.c`


#include <stdio.h>
#include <ctype.h>

int main() {
    int c;
    while ((c = getchar()) != EOF) {
        putchar(toupper(c));
    }
    return 0;
}


Compilar y ejecutar:


gcc filtro.c -o filtro
cat archivo.txt | ./filtro


👉 Convierte cada carácter de la entrada en mayúscula antes de mostrarlo en la salida.

---

### 3. Filtro extra en C – `filtro2.c`


#include <stdio.h>
#include <ctype.h>

int main() {
    int c;
    while ((c = getchar()) != EOF) {
        if (!isspace(c)) {
            putchar(c);
        }
    }
    return 0;
}


Compilar y ejecutar:

bash
gcc filtro2.c -o filtro2
cat archivo.txt | ./filtro2

👉 Elimina los espacios en blanco del texto de entrada, devolviendo la cadena “compacta”.

---

## 📌 Archivos incluidos en el repositorio

* `archivo.txt` → archivo de prueba
* `filtro.sh` → filtro en Bash
* `filtro.c` → filtro en C (mayúsculas)
* `filtro2.c` → filtro en C (elimina espacios)
* `README.md` → instrucciones y ejemplos de ejecución

---

## Conclusión

La práctica permitió comprobar el funcionamiento de los filtros básicos (`cat`, `cut`, `grep`, `wc`, `awk`, `sed`) y cómo se potencian al combinarlos con tuberías y redirecciones.
Además, se cumplió con la consigna de crear filtros propios en **Bash** y en **C**, demostrando cómo un administrador de sistemas puede adaptar y extender herramientas según sus necesidades.
Este ejercicio refleja la importancia del dominio de la línea de comandos en la administración de infraestructuras.


