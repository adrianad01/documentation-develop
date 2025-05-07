# 🗺️ Map en Java 21

Un `Map` es como una caja de llaves y valores.  
Tú le das una **llave** y él te regresa el **valor** que está guardado ahí.

Ejemplo real: una agenda de teléfonos.

```java
nombre -> número
"Adrián" -> "12345"
"Lucía" -> "67890"
```

## 👨‍🏫 Tipos comunes de `Map`

| Tipo de Map       | Qué hace                                                   |
|-------------------|-------------------------------------------------------------|
| `HashMap`         | Orden **aleatorio**, rápido para guardar y buscar.         |
| `LinkedHashMap`   | Mantiene el **orden en que se agregaron** los elementos.   |
| `TreeMap`         | Ordena las llaves **alfabéticamente** o **numéricamente**. |

## ✏️ Ejemplo básico con `HashMap`

```java
import java.util.HashMap;
import java.util.Map;

public class Agenda {
    public static void main(String[] args) {
        Map<String, String> telefono = new HashMap<>();

        telefono.put("Adrián", "12345");
        telefono.put("Lucía", "67890");

        String numero = telefono.get("Lucía");
        System.out.println("Número de Lucía: " + numero);

        if (telefono.containsKey("Adrián")) {
            System.out.println("¡Adrián está en la agenda!");
        }

        telefono.remove("Lucía");

        for (Map.Entry<String, String> entrada : telefono.entrySet()) {
            System.out.println("Nombre: " + entrada.getKey() + ", Teléfono: " + entrada.getValue());
        }
    }
}
```

## ✅ Métodos comunes

| Método                      | Qué hace                                       |
|----------------------------|------------------------------------------------|
| `put(clave, valor)`        | Agrega o actualiza un valor                    |
| `get(clave)`               | Obtiene el valor asociado a esa clave         |
| `remove(clave)`            | Elimina esa clave y su valor                  |
| `containsKey(clave)`       | Verifica si existe esa clave                  |
| `keySet()`                 | Devuelve todas las llaves                     |
| `values()`                 | Devuelve todos los valores                    |
| `entrySet()`               | Devuelve todas las llaves con sus valores     |
| `size()`                   | Cuántas entradas tiene                        |
| `isEmpty()`                | ¿Está vacío el mapa?                          |

## 💡 Ejemplo con números

```java
Map<Integer, String> frutas = new HashMap<>();
frutas.put(1, "Manzana");
frutas.put(2, "Banana");
frutas.put(3, "Sandía");

System.out.println(frutas.get(2)); // Banana
```

## 🚨 ¿Qué pasa si pido una clave que no existe?

```java
System.out.println(frutas.get(10)); // Esto imprime: null
```

No explota, solo dice “no encontré nada” (`null`).