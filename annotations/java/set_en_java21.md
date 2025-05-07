
# Set en Java 21

## 🧩 ¿Qué es un `Set`?

Un `Set` es una colección que **no permite elementos duplicados**. Si intentas agregar un elemento que ya existe, simplemente lo ignora.

---

## 🧠 Características

- No permite **elementos duplicados**.
- No garantiza un **orden específico** (aunque algunas implementaciones sí).
- Pertenece al paquete `java.util` y a la jerarquía de `Collection`.

---

## 🎯 Tipos de `Set` más comunes

| Tipo de Set       | Descripción                                  |
|-------------------|----------------------------------------------|
| `HashSet`         | Rápido, pero no mantiene ningún orden.       |
| `LinkedHashSet`   | Mantiene el orden en que se agregan los datos. |
| `TreeSet`         | Ordena los elementos automáticamente.        |

---

## ✏️ Ejemplo básico

```java
import java.util.HashSet;
import java.util.Set;

public class SetExample {
    public static void main(String[] args) {
        Set<String> frutas = new HashSet<>();

        frutas.add("Manzana");
        frutas.add("Banana");
        frutas.add("Naranja");
        frutas.add("Manzana"); // Duplicado

        System.out.println(frutas); // [Banana, Manzana, Naranja]
    }
}
```

---

## 🔍 Operaciones comunes

- `add(element)` → Agrega un elemento.
- `remove(element)` → Elimina un elemento.
- `contains(element)` → Verifica si existe.
- `size()` → Número de elementos.
- `clear()` → Borra todo.
- `isEmpty()` → ¿Está vacío?

---

## 🧪 Ejemplo: eliminar duplicados de una lista

```java
import java.util.*;

public class EliminarDuplicados {
    public static void main(String[] args) {
        List<String> listaConDuplicados = Arrays.asList("Java", "Python", "Java", "C++");

        Set<String> sinDuplicados = new HashSet<>(listaConDuplicados);

        System.out.println(sinDuplicados); // [Java, Python, C++]
    }
}
```

---

## 📌 ¿Cuándo usar un `Set`?

- Si no necesitas valores duplicados.
- Para buscar elementos rápidamente.
- Si el orden no importa (`HashSet`) o sí (`LinkedHashSet`, `TreeSet`).
