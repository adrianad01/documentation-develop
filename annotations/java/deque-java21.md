# Deque en Java 21

## 🧠 ¿Qué es un `Deque`?

Deque viene de "Double Ended Queue", que significa "cola de doble extremo". Es una estructura de datos que permite agregar y quitar elementos tanto por el principio como por el final.

---

## 🛠️ ¿Cómo se usa en Java?

```java
import java.util.Deque;
import java.util.ArrayDeque;

public class DequeEjemplo {
    public static void main(String[] args) {
        Deque<String> fila = new ArrayDeque<>();

        // Agregar elementos
        fila.addFirst("A"); // al inicio
        fila.addLast("B");  // al final
        fila.addLast("C");

        System.out.println("Deque: " + fila); // [A, B, C]

        // Quitar elementos
        System.out.println("Quitar del inicio: " + fila.removeFirst()); // A
        System.out.println("Quitar del final: " + fila.removeLast());   // C

        System.out.println("Deque después: " + fila); // [B]
    }
}
```

---

## ✨ Métodos importantes

| Método           | ¿Qué hace?                            |
|------------------|----------------------------------------|
| `addFirst(e)`    | Agrega `e` al **inicio**               |
| `addLast(e)`     | Agrega `e` al **final**                |
| `removeFirst()`  | Quita el primero                       |
| `removeLast()`   | Quita el último                        |
| `peekFirst()`    | Mira el primero sin quitarlo           |
| `peekLast()`     | Mira el último sin quitarlo            |
| `offerFirst(e)`  | Agrega al inicio sin lanzar excepción  |
| `offerLast(e)`   | Agrega al final sin lanzar excepción   |

---

## 🧸 Ejemplo visual

```
Inicio ----->   [A] [B] [C]   <----- Final
```

- `removeFirst()` quita A.
- `removeLast()` quita C.

---

## 🆕 Novedades en Java 21

No hubo cambios en la interfaz `Deque`, pero se sigue recomendando usar `ArrayDeque` como implementación eficiente para la mayoría de los casos (excepto si necesitas sincronización).