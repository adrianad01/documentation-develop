# 🧺 Listas en Java (Java 21)

## 🐣 ¿Qué es una Lista?
Una **Lista** en Java es como una **fila de juguetes**. Puedes poner juguetes (datos), quitarlos, ver cuántos tienes o sacar el que está en la posición 3, por ejemplo.

En Java usamos `List` para hacer esto. Pero no puedes usar `List` directamente, necesitas algo que la implemente como `ArrayList`.

---

## 🎒 Cómo crear una Lista

```java
import java.util.List;
import java.util.ArrayList;

public class ListaEjemplo {
    public static void main(String[] args) {
        List<String> frutas = new ArrayList<>();
        frutas.add("Manzana");
        frutas.add("Plátano");
        frutas.add("Fresa");

        System.out.println(frutas); // [Manzana, Plátano, Fresa]
    }
}
```

---

## 🛠 Métodos más usados

| Método              | ¿Qué hace?                                        | Ejemplo                               |
|---------------------|--------------------------------------------------|----------------------------------------|
| `add()`             | Agrega un elemento                               | `frutas.add("Mango")`                  |
| `get(int i)`        | Obtiene el elemento en la posición `i`           | `frutas.get(0)` → "Manzana"           |
| `remove(int i)`     | Elimina el elemento en la posición `i`           | `frutas.remove(1)`                     |
| `size()`            | Dice cuántos elementos hay                       | `frutas.size()`                        |
| `contains(obj)`     | ¿La lista tiene este valor?                      | `frutas.contains("Fresa")` → true     |
| `clear()`           | Borra toda la lista                              | `frutas.clear()`                       |
| `isEmpty()`         | ¿Está vacía la lista?                            | `frutas.isEmpty()`                     |

---

## 📦 Tipos de Listas

### ✅ `ArrayList`
- La más común.
- Muy rápida para acceder a un elemento.

### 🔁 `LinkedList`
- Buena cuando agregas o quitas muchos elementos al inicio o al medio.
- Más lenta para acceder a elementos por posición.

```java
import java.util.LinkedList;

List<String> nombres = new LinkedList<>();
nombres.add("Juan");
nombres.add("Ana");
```

---

## 🧪 Recorrer una lista

### 🔁 Usando for-each

```java
for (String fruta : frutas) {
    System.out.println(fruta);
}
```

### 🔢 Usando for tradicional

```java
for (int i = 0; i < frutas.size(); i++) {
    System.out.println(frutas.get(i));
}
```

---

## 🧠 Desde Java 21 (y anteriores)

### ✅ `List.of(...)` (desde Java 9)
Crear listas **inmutables** (no puedes modificarlas).

```java
List<String> colores = List.of("Rojo", "Verde", "Azul");
// colores.add("Amarillo"); // ERROR: UnsupportedOperationException
```

---

## ⚠️ Inmutabilidad vs Mutabilidad

| Tipo de Lista     | ¿Se puede modificar? | ¿Cómo se crea?               |
|------------------|----------------------|------------------------------|
| Mutable          | ✅ Sí                 | `new ArrayList<>()`          |
| Inmutable        | ❌ No                | `List.of("a", "b")`          |

---

## 🧼 Buenas prácticas

- Usa `List<String> lista = new ArrayList<>();` para mayor flexibilidad.
- Prefiere `List` como tipo (interfaz) y no `ArrayList` directamente.
- Si no necesitas modificar la lista, usa `List.of()`.