
# Optionals en Java 21 ☕

## ¿Qué es Optional?

`Optional<T>` es una clase contenedor que representa un valor que puede o no estar presente. Su objetivo principal es **evitar los NullPointerException** y hacer el código más limpio y expresivo.

---

## ¿Por qué usar Optional?

### Código tradicional:
```java
public String getEmail(User user) {
    if (user != null && user.getEmail() != null) {
        return user.getEmail();
    }
    return "Email no disponible";
}
```

### Con Optional:
```java
public Optional<String> getEmail(User user) {
    return Optional.ofNullable(user)
                   .map(User::getEmail);
}
```

---

## Métodos comunes

| Método                  | ¿Qué hace? |
|-------------------------|------------|
| `Optional.empty()`      | Crea un Optional sin valor |
| `Optional.of(valor)`    | Crea un Optional con valor (no debe ser null) |
| `Optional.ofNullable(v)`| Crea un Optional que acepta `null` |
| `isPresent()`           | Devuelve true si tiene valor |
| `isEmpty()`             | Devuelve true si no hay valor |
| `get()`                 | Devuelve el valor (puede lanzar excepción) |
| `orElse(valor)`         | Devuelve el valor o uno por defecto |
| `orElseGet(supplier)`   | Igual que orElse pero con lambda |
| `orElseThrow()`         | Lanza excepción si no hay valor |
| `ifPresent(consumer)`   | Ejecuta un bloque si hay valor |
| `map(func)`             | Transforma el valor si está presente |
| `flatMap(func)`         | Evita Optionals anidados |

---

## Ejemplos

### Crear Optionals
```java
Optional<String> nombre = Optional.of("Adrián");
Optional<String> vacio = Optional.empty();
Optional<String> posibleNull = Optional.ofNullable(obtenerNombre());
```

### Obtener valor
```java
String nombre = posibleNull.orElse("Nombre por defecto");
```

### Ejecutar si hay valor
```java
nombre.ifPresent(n -> System.out.println("Hola, " + n));
```

### Transformar
```java
Optional<String> nombreMayuscula = nombre.map(String::toUpperCase);
```

### Encadenar
```java
Optional<User> user = Optional.of(new User("Adrián", "correo@example.com"));
String email = user
    .map(User::getEmail)
    .orElse("Sin correo");
```

---

## Malas prácticas

- No uses Optional como parámetro en métodos públicos
- No uses `.get()` sin verificar si tiene valor
- No serialices Optional directamente (por ejemplo, con JSON)

---

## Optional en Java 21

Aunque no hay cambios directos en Optional en Java 21, sigue siendo una herramienta esencial del estilo moderno de Java. Su uso con nuevas características como `pattern matching` lo hace más poderoso.

---

¡Listo para escribir código más seguro y limpio con Optional!

---

## ¿En qué casos se puede usar Optional?

### 1. Consultas a base de datos (Spring Data)
```java
Optional<User> user = userRepository.findByEmail("correo@dominio.com");
String nombre = user.map(User::getName).orElse("Invitado");
```

### 2. Parámetros opcionales en lógica interna
```java
public void procesar(Optional<String> comentario) {
    comentario.ifPresent(c -> System.out.println("Comentario: " + c));
}
```

### 3. Configuraciones opcionales
```java
public Optional<String> getConfig(String key) {
    return Optional.ofNullable(System.getenv(key));
}
```

### 4. Encadenamiento limpio de operaciones
```java
Optional<String> nombre = Optional.of("adrian");
String result = nombre
    .filter(n -> n.length() > 3)
    .map(String::toUpperCase)
    .orElse("DEFAULT");
```

### 5. Respuesta de servicios externos
```java
Optional<ClienteDTO> cliente = clienteService.obtenerCliente(id);
cliente.ifPresent(c -> System.out.println("Cliente: " + c.getNombre()));
```

---

## ¿Dónde NO se recomienda usar Optional?

| Contexto                   | ¿Usar Optional? | Razón                                                  |
|----------------------------|------------------|a---------------------------------------------------------|
| Atributos de entidades JPA | ❌ No             | JPA no lo maneja bien y puede causar errores            |
| Parámetros públicos        | ❌ No             | Usar `null` es más claro para frameworks como Spring    |
| Serialización (ej. JSON)   | ❌ No             | Jackson y otros no lo manejan por defecto               |

---

## Optional vs Null (Comparación general)

| null                            | Optional                           |
|---------------------------------|------------------------------------|
| Puede lanzar NullPointerException | Previene errores si se usa bien    |
| Poco explícito                  | Claramente comunica ausencia de valor |
| Requiere `if (obj != null)`     | Usa `map`, `orElse`, `ifPresent`, etc. |
| Difícil de encadenar            | Fácil de combinar con operaciones funcionales |

---

## Conclusión general

✔️ `Optional` es una forma moderna, segura y expresiva de **manejar valores ausentes**.  
Su uso **reduce errores** y mejora la **legibilidad del código**, especialmente en:

- Consultas a base de datos
- Configuraciones opcionales
- Lógica interna sin `null`
- APIs funcionales y limpias

