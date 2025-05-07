
# Stack en Java 21

## ¿Qué es un Stack?

Un Stack es como una pila de panqueques. El último que se pone es el primero que se quita (LIFO: Last In, First Out).

## Ejemplo con java.util.Stack

```java
import java.util.Stack;

public class StackEjemplo {
    public static void main(String[] args) {
        Stack<String> pila = new Stack<>();

        pila.push("Panqueque 1");
        pila.push("Panqueque 2");
        pila.push("Panqueque 3");

        System.out.println("Tope de la pila: " + pila.peek());
        System.out.println("Quitando: " + pila.pop());
        System.out.println("Nuevo tope: " + pila.peek());
        System.out.println("¿Está vacía?: " + pila.isEmpty());
    }
}
```

## Métodos comunes

- `push(item)`: Agrega un item a la pila.
- `pop()`: Quita el item de arriba.
- `peek()`: Mira el item de arriba sin quitarlo.
- `isEmpty()`: Revisa si la pila está vacía.
- `search(obj)`: Busca un elemento en la pila.

## Recomendación moderna: usar Deque

```java
import java.util.ArrayDeque;
import java.util.Deque;

Deque<String> pila = new ArrayDeque<>();
pila.push("Panqueque 1");
pila.push("Panqueque 2");
pila.pop(); // Quita "Panqueque 2"
```

Deque (con `ArrayDeque`) es más eficiente y recomendado desde Java 21.
