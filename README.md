# 🧩 Ingeniería Inversa y Análisis Algorítmico

---

## 📦 Parte 1: Ingeniería Inversa del archivo JAR

### 🛠 Herramienta Utilizada

- **Enhanced Class Decompiler** — instalada desde Eclipse Marketplace e integrada en **Eclipse IDE**
- Permite visualizar el código fuente equivalente en Java a partir de archivos `.class` compilados

---

### ⚙️ Proceso

1. **Instalación** — Se buscó e instaló Enhanced Class Decompiler desde Eclipse Marketplace y se reinició el IDE.
2. **Configuración** — Se asociaron los archivos `.class` para abrirse automáticamente con el Class Decompiler Viewer.
3. **Importación** — Se agregó el `.jar` al workspace y se expandió su contenido desde el Package Explorer.
4. **Decompilación** — Se hizo doble clic sobre cada `.class`; el decompiler convirtió el bytecode en código Java legible.



---

### 📚 Análisis del Código Decompilado

#### 1️⃣ Clases Identificadas

**Paquete `umg.edu.gt.data_structure.array`**

- `BubbleSort`
- `MergeSortDemo`
- `QuickSort`
- `SumArray`

**Paquete `umg.edu.gt.data_structure.introduction`**

- `App` — clase principal con método `main`

---

#### 2️⃣ Operaciones sobre Arreglos

- **`BubbleSort`** — Compara cada par de elementos uno al lado del otro y los intercambia si están en el orden incorrecto. Repite este proceso hasta que el arreglo quede ordenado.
- **`MergeSortDemo`** — Divide el arreglo en dos mitades, ordena cada mitad por separado y luego las une en un solo arreglo ya ordenado.
- **`QuickSort`** — Elige un elemento como pivote y mueve todos los elementos menores a su izquierda y los mayores a su derecha. Repite el proceso en cada subgrupo.
- **`SumArray`** — Recorre el arreglo de inicio a fin sumando cada elemento al resultado acumulado, sin modificar el arreglo.
---

#### 3️⃣ Algoritmos de Ordenamiento

---

**BubbleSort** — Recorre el arreglo varias veces. En cada pasada, compara dos elementos vecinos y los intercambia si el de la izquierda es mayor que el de la derecha. Continúa hasta que no haya más intercambios necesarios.

#### Fragmento de código

```java
for (int i = 0; i < n - 1; i++) {
    boolean swapped = false;
    for (int j = 0; j < n - 1 - i; j++) {
        if (arr[j] > arr[j + 1]) {
            int temp = arr[j];
            arr[j] = arr[j + 1];
            arr[j + 1] = temp;
            swapped = true;
        }
    }
    if (!swapped) break;
}
```

- Tiempo: `O(n²)` | Espacio: `O(1)` | Tipo: Iterativo

---

**MergeSortDemo** — Divide el arreglo en mitades hasta tener partes de un solo elemento. Luego va uniendo esas partes en orden, comparando elemento por elemento, hasta reconstruir el arreglo completamente ordenado.

#### Fragmento de código

```java
int mid = a.length / 2;
int[] left = Arrays.copyOfRange(a, 0, mid);
int[] right = Arrays.copyOfRange(a, mid, a.length);
mergeSort(left);
mergeSort(right);
merge(a, left, right);
```

- Tiempo: `O(n log n)` | Espacio: `O(n)` | Tipo: Recursivo

---

**QuickSort** — Toma un elemento del arreglo como pivote. Mueve todos los elementos menores al pivote hacia la izquierda y los mayores hacia la derecha. Luego repite el mismo proceso en cada mitad hasta ordenar todo el arreglo.

#### Fragmento de código

```java
int pivot = arr[high];
int i = low - 1;
for (int j = low; j < high; j++) {
    if (arr[j] <= pivot) {
        i++;
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
int temp = arr[i + 1];
arr[i + 1] = arr[high];
arr[high] = temp;
return i + 1;
```

- Tiempo promedio: `O(n log n)` / Peor caso: `O(n²)` | Espacio: `O(log n)` | Tipo: Recursivo

---

**SumArray** — No es un algoritmo de ordenamiento. Simplemente recorre el arreglo de principio a fin, sumando cada elemento a una variable acumuladora, y al final muestra el resultado total.

#### Fragmento de código

```java
int sum = 0;
for (int i = 0; i < arr.length; i++) {
    sum += arr[i];
}
System.out.println("Suma total: " + sum);
```

- Tiempo: `O(n)` | Espacio: `O(1)` | Tipo: Iterativo

---

## 🧠 Parte 2: Ejercicio Algorítmico

### 📌 Problema

Dado un arreglo de enteros, encontrar el **segundo mayor** y el **segundo menor**.

**Restricciones:**
- Recorrer el arreglo **una sola vez**
- **No** se permite ordenar el arreglo

---

### 🧮 Estrategia

Se mantienen cuatro variables que se actualizan dinámicamente en una sola pasada:

- `mayor`
- `segundoMayor`
- `menor`
- `segundoMenor`

---

### 📑 Pseudocódigo


```
ALGORITMO SegundoMayorMenor
ENTRADA: arreglo A de n enteros
SALIDA: segundoMayor, segundoMenor

INICIO
    SI n < 2 ENTONCES
        ESCRIBIR "Error: el arreglo debe tener al menos 2 elementos"
        TERMINAR
    FIN_SI

    mayor        ← A
    segundoMayor ← A
    menor        ← A
    segundoMenor ← A

    PARA i ← 1 HASTA n - 1 HACER
        SI A[i] > mayor ENTONCES
            segundoMayor ← mayor
            mayor        ← A[i]
        SINO_SI A[i] > segundoMayor Y A[i] ≠ mayor ENTONCES
            segundoMayor ← A[i]
        FIN_SI

        SI A[i] < menor ENTONCES
            segundoMenor ← menor
            menor        ← A[i]
        SINO_SI A[i] < segundoMenor Y A[i] ≠ menor ENTONCES
            segundoMenor ← A[i]
        FIN_SI
    FIN_PARA

    ESCRIBIR "Segundo Mayor: ", segundoMayor
    ESCRIBIR "Segundo Menor: ", segundoMenor
FIN
```



### ⏱ Análisis de Complejidad

**Tiempo — `O(n)`**
El arreglo se recorre una única vez, por lo que el tiempo crece de forma lineal según el tamaño de la entrada.

**Espacio — `O(1)`**
Solo se utilizan cuatro variables auxiliares independientemente del tamaño del arreglo, por lo que el uso de memoria es constante.
