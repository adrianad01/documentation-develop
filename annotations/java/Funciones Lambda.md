# Funciones Lambda

Una **expresión lambda** es una forma compacta de representar una función anónima (una función sin nombre). Se usa para simplificar el código, especialmente cuando quieres pasar comportamiento como parámetro.

### Sintaxis Básica:
```java
(param1, param2, ...) -> { cuerpo }
```

Se usan principalmente cuando estás trabajando con **interfaces funcionales**, que son interfaces que tienen solo un método abstracto.

---

### Ejemplos comunes:

| Interfaz        | Método único         | Para qué sirve                             |
|-----------------|----------------------|--------------------------------------------|
| `Runnable`      | `void run()`         | Ejecutar una tarea                         |
| `Callable<V>`   | `V call()`           | Ejecutar y devolver algo                   |
| `Consumer<T>`   | `void accept(T)`     | Recibir algo y usarlo                      |
| `Function<T,R>` | `R apply(T)`         | Recibir algo y transformarlo               |
| `Predicate<T>`  | `boolean test(T)`    | Evaluar si algo cumple una condición       |
| `Comparator<T>` | `int compare(T, T)`  | Comparar dos objetos                       |

---

## Estructura básica de interfaces funcionales

### 1. Runnable
- No recibe parámetros
- No retorna nada

```java
Runnable tarea = () -> {
    // lógica aquí
};
tarea.run();
```

---

### 2. Callable<V>
- No recibe parámetros
- Retorna un valor de tipo V
- Puede lanzar una excepción

```java
Callable<String> tarea = () -> {
    return "resultado";
};
String resultado = tarea.call();  // requiere try-catch
```

---

### 3. Consumer<T>
- Recibe un valor de tipo T
- No retorna nada

```java
Consumer<String> imprimir = texto -> {
    System.out.println(texto);
};
imprimir.accept("Hola mundo");
```

---

### 4. Function<T, R>
- Recibe un valor de tipo T
- Retorna un valor de tipo R

```java
Function<String, Integer> longitud = texto -> texto.length();
int resultado = longitud.apply("Adrián");
```

---

### 5. Predicate<T>
- Recibe un valor de tipo T
- Retorna un boolean (true/false)

```java
Predicate<Integer> esPar = numero -> numero % 2 == 0;
boolean resultado = esPar.test(4);
```

---

### 6. Comparator<T>
- Recibe dos valores de tipo T
- Retorna un int: negativo, cero o positivo según el orden

```java
Comparator<String> comparador = (a, b) -> a.compareTo(b);
int resultado = comparador.compare("Jose", "Miguel");
```
