# 📚 Arrays vs ArrayList en Java

## 🧩 ¿Qué es un `Array`?

Un **array** en Java es una estructura de datos **de tamaño fijo** que almacena elementos del mismo tipo.

```java
int[] numeros = new int[3];  // array de tamaño fijo
numeros[0] = 10;
numeros[1] = 20;
numeros[2] = 30;
```

🔹 Ventajas:
- Más eficiente en cuanto a memoria.
- Acceso rápido a elementos por índice.

🔹 Desventajas:
- Tamaño fijo, no se puede redimensionar.
- No tiene métodos útiles como `add()` o `remove()`.

---

## 📦 ¿Qué es un `ArrayList`?

Un `ArrayList` es una **colección dinámica** del framework de colecciones de Java (`java.util.ArrayList`), que **puede cambiar de tamaño automáticamente**.

```java
import java.util.ArrayList;

ArrayList<Integer> numeros = new ArrayList<>();
numeros.add(10);
numeros.add(20);
numeros.add(30);
```

🔹 Ventajas:
- Tamaño dinámico.
- Métodos útiles: `add()`, `remove()`, `contains()`, etc.
- Funciona bien con estructuras más complejas.

🔹 Desventajas:
- Menor rendimiento en operaciones muy específicas (comparado con arrays).
- Solo puede almacenar objetos (no tipos primitivos directamente).

---

## 🆚 Diferencias clave

| Característica             | `Array`                      | `ArrayList`                        |
|---------------------------|------------------------------|------------------------------------|
| Tamaño                    | Fijo                         | Dinámico                           |
| Tipos soportados          | Tipos primitivos y objetos   | Solo objetos (`Integer`, no `int`) |
| Métodos disponibles       | Ninguno útil (`length`)      | Muchos (`add()`, `remove()`, etc.)|
| Parte de colecciones      | No                           | Sí (`java.util`)                   |
| Rendimiento               | Más rápido en acceso directo| Más flexible pero menos eficiente  |

---

## 🔁 Conversión entre ambos

### Array a ArrayList:
```java
String[] nombres = {"Ana", "Luis", "Pedro"};
List<String> lista = Arrays.asList(nombres);
```

> ⚠️ `Arrays.asList()` retorna una lista **de tamaño fijo**. Si necesitas modificarla:
```java
ArrayList<String> listaMutable = new ArrayList<>(Arrays.asList(nombres));
```

### ArrayList a Array:
```java
ArrayList<String> lista = new ArrayList<>();
lista.add("Ana");
lista.add("Luis");

String[] array = lista.toArray(new String[0]);
```

---

## 📌 ¿Cuándo usar cada uno?

| Caso de uso                                      | Recomendación     |
|--------------------------------------------------|-------------------|
| Sabes cuántos elementos manejarás               | Usa `Array`       |
| Necesitas agregar/eliminar elementos dinámicamente| Usa `ArrayList`   |
| Requieres métodos de búsqueda o manipulación     | Usa `ArrayList`   |
| Trabajas con estructuras de bajo nivel o muy eficientes | Usa `Array`  |