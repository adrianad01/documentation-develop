
# 🧵 Iterator en Java 21

## ¿Qué es un Iterator?

Imagina que tienes una **caja de juguetes**. Quieres sacar uno por uno para jugar con ellos.  
Un **Iterator** es como una **manita mágica** que te ayuda a sacar cada juguete de la caja **uno a la vez** sin perderte ninguno.

### ✅ ¿Para qué sirve?

Un `Iterator` sirve para **recorrer colecciones** (como listas o sets) sin tener que usar un `for` tradicional.  
Se usa mucho cuando no sabes cuántos elementos hay o si quieres **eliminar elementos mientras recorres**.

---

## 🛠️ ¿Cómo se usa un Iterator?

### Ejemplo básico con una Lista:

```java
import java.util.*;

public class EjemploIterator {
    public static void main(String[] args) {
        List<String> juguetes = new ArrayList<>();
        juguetes.add("Carro");
        juguetes.add("Muñeca");
        juguetes.add("Pelota");

        // Obtenemos el iterator
        Iterator<String> it = juguetes.iterator();

        // Recorremos uno a uno
        while (it.hasNext()) {
            String juguete = it.next();
            System.out.println("Jugando con: " + juguete);
        }
    }
}
```

### Métodos importantes

- `iterator()`: Crea la manita mágica (el iterator).
- `hasNext()`: Pregunta "¿hay otro juguete?".
- `next()`: Saca el siguiente juguete.
- `remove()`: Elimina el último juguete que sacaste.

---

## 🧽 Eliminar elementos con `Iterator`

```java
import java.util.*;

public class EliminarConIterator {
    public static void main(String[] args) {
        List<String> frutas = new ArrayList<>();
        frutas.add("Manzana");
        frutas.add("Pera");
        frutas.add("Plátano");

        Iterator<String> it = frutas.iterator();

        while (it.hasNext()) {
            String fruta = it.next();
            if (fruta.equals("Pera")) {
                it.remove(); // Elimina la "Pera" sin error
            }
        }

        System.out.println(frutas); // [Manzana, Plátano]
    }
}
```

---

## 🆚 ¿Cuándo usar Iterator y cuándo no?

| Situación                          | ¿Usar Iterator? |
|-----------------------------------|-----------------|
| Solo recorrer sin modificar       | Opcional        |
| Eliminar mientras recorres        | ✅ Sí           |
| Recorres con índices (posición)   | ❌ Mejor `for`  |
| Quieres usar Streams              | ❌ Usa `.stream()`|

---

¡Y eso es todo sobre `Iterator` en Java 21!
