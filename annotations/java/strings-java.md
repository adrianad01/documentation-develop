
# 📘 Strings en Java 21

## ¿Qué es un String?
Un `String` en Java representa una **secuencia de caracteres**. Es uno de los tipos más utilizados en cualquier aplicación Java.

```java
String saludo = "Hola, mundo!";
```

Los Strings en Java son **inmutables**, lo que significa que no se pueden modificar una vez creados.

---

## 🧰 Métodos más comunes

| Método                        | Descripción                                                                                 | Ejemplo                                                 |
|------------------------------|---------------------------------------------------------------------------------------------|---------------------------------------------------------|
| `length()`                   | Devuelve la longitud del String                                                             | `"Hola".length()` → `4`                                 |
| `charAt(int index)`          | Devuelve el carácter en la posición indicada                                                | `"Hola".charAt(1)` → `'o'`                              |
| `substring(int begin, int end)` | Devuelve una subcadena desde `begin` hasta `end - 1`                                     | `"Hola".substring(1, 3)` → `"ol"`                       |
| `toLowerCase()`              | Convierte a minúsculas                                                                     | `"HOLA".toLowerCase()` → `"hola"`                       |
| `toUpperCase()`              | Convierte a mayúsculas                                                                     | `"hola".toUpperCase()` → `"HOLA"`                       |
| `trim()`                     | Elimina espacios en blanco al inicio y final                                               | `"  hola  ".trim()` → `"hola"`                          |
| `equals(String otro)`        | Compara dos Strings (sensibles a mayúsculas/minúsculas)                                    | `"hola".equals("Hola")` → `false`                       |
| `equalsIgnoreCase(String otro)`| Compara dos Strings ignorando mayúsculas/minúsculas                                      | `"hola".equalsIgnoreCase("Hola")` → `true`              |
| `contains(String texto)`     | Verifica si el String contiene una secuencia de caracteres                                 | `"Java es cool".contains("cool")` → `true`             |
| `startsWith(String texto)`   | Verifica si el String comienza con el texto dado                                           | `"Java".startsWith("Ja")` → `true`                      |
| `endsWith(String texto)`     | Verifica si termina con el texto dado                                                      | `"Java".endsWith("va")` → `true`                        |
| `replace(char old, char new)`| Reemplaza caracteres o secuencias                                                           | `"casa".replace('a', 'o')` → `"coso"`                   |
| `split(String regex)`        | Divide un String por el delimitador indicado                                               | `"a,b,c".split(",")` → `["a", "b", "c"]`                |
| `isEmpty()`                  | Verifica si la cadena está vacía (longitud 0)                                               | `"".isEmpty()` → `true`                                 |
| `isBlank()`                  | Verifica si el String está vacío o contiene solo espacios (desde Java 11)                  | `"   ".isBlank()` → `true`                              |
| `repeat(int n)`              | Repite el String `n` veces (desde Java 11)                                                 | `"la".repeat(3)` → `"lalala"`                           |
| `strip()`                    | Elimina espacios Unicode (mejor que `trim()`) desde Java 11                                | `"  hola  ".strip()` → `"hola"`                         |

---

## 🔎 Ejemplos prácticos

### Ejemplo 1: Uso de varios métodos

```java
public class EjemploString {
    public static void main(String[] args) {
        String mensaje = "  Java es poderoso  ";

        System.out.println("Original: [" + mensaje + "]");
        System.out.println("Trim: [" + mensaje.trim() + "]");
        System.out.println("Uppercase: " + mensaje.toUpperCase());
        System.out.println("¿Contiene 'es'? " + mensaje.contains("es"));
        System.out.println("Longitud: " + mensaje.length());
        System.out.println("Primer caracter: " + mensaje.charAt(0));
    }
}
```

### Ejemplo 2: Comparación de Strings

```java
String a = "hola";
String b = "HOLA";

System.out.println(a.equals(b));            // false
System.out.println(a.equalsIgnoreCase(b));  // true
```

### Ejemplo 3: Repetir y dividir

```java
String nombre = "Adrián";
String repetido = nombre.repeat(3);
System.out.println(repetido); // AdriánAdriánAdrián

String lista = "pan,leche,huevo";
String[] items = lista.split(",");
for (String item : items) {
    System.out.println(item);
}
```

---

## 🆕 Métodos nuevos desde Java 11 en adelante

```java
String multilinea = "Hola\nMundo\nJava";
multilinea.lines().forEach(System.out::println);
```

---

¿Te gustaría agregar ejercicios prácticos sobre Strings?
