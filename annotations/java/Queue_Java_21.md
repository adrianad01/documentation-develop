# 🧵 Queue en Java 21

## ¿Qué es una Queue?

Una Queue (o cola) es como hacer fila en un parque:
- El primero que llega es el primero que se va.
- Esto se llama **FIFO** (First In, First Out).

## ¿Cómo se usa una Queue en Java?

```java
import java.util.LinkedList;
import java.util.Queue;

public class QueueExample {
    public static void main(String[] args) {
        Queue<String> fila = new LinkedList<>();

        // Agregar elementos
        fila.add("Ana");
        fila.add("Luis");
        fila.add("Carlos");

        System.out.println("Primero en la fila: " + fila.peek()); // Ana

        // Sacar al primero
        System.out.println("Se va: " + fila.poll()); // Ana

        System.out.println("Ahora el primero es: " + fila.peek()); // Luis
    }
}
```

## Métodos comunes

| Método     | Acción                                                     |
|------------|------------------------------------------------------------|
| `add()`    | Agrega un elemento                                          |
| `offer()`  | Igual que `add`, pero retorna `false` si no puede agregar |
| `poll()`   | Saca el primero, o `null` si está vacía                     |
| `remove()` | Saca el primero, lanza excepción si está vacía             |
| `peek()`   | Ve el primero sin sacarlo                                  |
| `element()`| Igual que `peek()`, pero lanza excepción si está vacía     |

## Clases que implementan `Queue`

- `LinkedList`
- `PriorityQueue`
- `ArrayDeque`
- `ConcurrentLinkedQueue`

## Ejemplo con PriorityQueue

```java
import java.util.PriorityQueue;

public class PriorityQueueExample {
    public static void main(String[] args) {
        PriorityQueue<Integer> cola = new PriorityQueue<>();

        cola.add(5);
        cola.add(1);
        cola.add(3);

        while (!cola.isEmpty()) {
            System.out.println(cola.poll()); // 1, 3, 5
        }
    }
}
```

## Recuerda

> Una Queue es como hacer fila en la tiendita: ¡el primero en llegar es el primero en ser atendido!