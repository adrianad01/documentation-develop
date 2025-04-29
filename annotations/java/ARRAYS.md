# 📚 Arreglos Unidimensionales y Bidimensionales en Java 21

## 🔸 ¿Qué es un arreglo?

Un **arreglo (array)** es una estructura de datos que almacena **un conjunto de elementos** del **mismo tipo**.

- Los índices empiezan en **0**.
- Los arreglos tienen **tamaño fijo** (no se puede cambiar después de creado).

---

## 🔸 Arreglo Unidimensional

Un **arreglo unidimensional** es simplemente **una lista de elementos** en línea recta.

### Ejemplo de declaración:

```java
// Declarar un arreglo de 5 enteros
int[] numeros = new int[5];
```

### Inicialización directa:

```java
// Declarar e inicializar
String[] nombres = {"Ana", "Luis", "Carlos", "María"};
```

### Acceder a elementos:

```java
System.out.println(nombres[0]); // Imprime "Ana"
System.out.println(nombres[3]); // Imprime "María"
```

### Modificar elementos:

```java
nombres[1] = "Lucía";
System.out.println(nombres[1]); // Imprime "Lucía"
```

---

## 🔸 Arreglo Bidimensional

Un **arreglo bidimensional** es **una tabla de filas y columnas** (como una matriz).

### Ejemplo de declaración:

```java
// Crear una matriz de 2 filas y 3 columnas
int[][] matriz = new int[2][3];
```

### Inicialización directa:

```java
int[][] matriz = {
    {1, 2, 3},
    {4, 5, 6}
};
```

### Acceder a elementos:

```java
System.out.println(matriz[0][1]); // Imprime "2"
System.out.println(matriz[1][2]); // Imprime "6"
```

### Modificar elementos:

```java
matriz[1][1] = 99;
System.out.println(matriz[1][1]); // Imprime "99"
```

---

# 📚 Métodos principales de la clase `Arrays`

La clase `java.util.Arrays` proporciona **métodos estáticos** muy útiles para trabajar con arreglos.

| Método | Descripción | Ejemplo |
|:------:|:-----------|:--------|
| `Arrays.toString()` | Convierte el arreglo a una **cadena** legible. | `System.out.println(Arrays.toString(numeros));` |
| `Arrays.fill()` | Rellena todo el arreglo con un **valor**. | `Arrays.fill(numeros, 7);` |
| `Arrays.sort()` | Ordena el arreglo **ascendentemente**. | `Arrays.sort(numeros);` |
| `Arrays.copyOf()` | Copia un arreglo **a otro** con el tamaño especificado. | `int[] copia = Arrays.copyOf(numeros, 10);` |
| `Arrays.equals()` | Compara dos arreglos **por contenido**. | `Arrays.equals(arr1, arr2);` |
| `Arrays.binarySearch()` | Busca un elemento en un arreglo **ordenado**. | `Arrays.binarySearch(numeros, 5);` |
| `Arrays.deepToString()` | Convierte un **arreglo multidimensional** a String. | `System.out.println(Arrays.deepToString(matriz));` |

---

# 📌 Ejemplos de uso de `Arrays`

```java
import java.util.Arrays;

public class EjemploArrays {
    public static void main(String[] args) {
        int[] numeros = {5, 2, 8, 1, 3};

        // Imprimir arreglo
        System.out.println(Arrays.toString(numeros)); // [5, 2, 8, 1, 3]

        // Ordenar
        Arrays.sort(numeros);
        System.out.println(Arrays.toString(numeros)); // [1, 2, 3, 5, 8]

        // Buscar
        int posicion = Arrays.binarySearch(numeros, 5);
        System.out.println("El número 5 está en la posición: " + posicion);

        // Copiar
        int[] copia = Arrays.copyOf(numeros, 7);
        System.out.println(Arrays.toString(copia)); // [1, 2, 3, 5, 8, 0, 0]

        // Rellenar
        Arrays.fill(copia, 9);
        System.out.println(Arrays.toString(copia)); // [9, 9, 9, 9, 9, 9, 9]

        // Arreglo bidimensional
        int[][] matriz = {{1,2}, {3,4}};
        System.out.println(Arrays.deepToString(matriz)); // [[1, 2], [3, 4]]
    }
}
```

---

# ✨ Resumen

- Los **arreglos** son estructuras de datos de tamaño fijo que almacenan elementos del **mismo tipo**.
- **Unidimensional** ➞ Lista lineal.
- **Bidimensional** ➞ Tabla de filas y columnas.
- La clase `Arrays` ofrece utilidades para:
  - Imprimir,
  - Ordenar,
  - Buscar,
  - Copiar,
  - Comparar,
  - Rellenar arreglos de manera sencilla.

