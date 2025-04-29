# Expresiones Regulares en Java 21

## 📙 ¿Qué es una Expresión Regular?

Una **expresión regular** (regex) es un **patrón** que se utiliza para **buscar, validar o reemplazar** texto que siga ciertas reglas.

- **Ejemplos de uso:**
  - Validar correos electrónicos.
  - Buscar números de teléfono en un texto.
  - Extraer fechas de un documento.

---

## 🛠️ ¿Cómo se usan en Java?

Java proporciona la clase `Pattern` y `Matcher` para trabajar con expresiones regulares:

```java
import java.util.regex.Pattern;
import java.util.regex.Matcher;
```

---

## 🎯 Pasos básicos para usar Regex

1. **Definir el patrón (regex)**.
2. **Crear un objeto `Pattern` con el patrón**.
3. **Crear un `Matcher` con el texto a analizar**.
4. **Usar métodos como `find()`, `matches()` o `replaceAll()`**.

---

## 🔥 Ejemplos sencillos

### 1. Validar si un texto es un número

```java
import java.util.regex.Pattern;
import java.util.regex.Matcher;

public class RegexExample {
    public static void main(String[] args) {
        String regex = "\\d+"; // uno o más dígitos
        String input = "12345";

        Pattern pattern = Pattern.compile(regex);
        Matcher matcher = pattern.matcher(input);

        if (matcher.matches()) {
            System.out.println("Es un número válido.");
        } else {
            System.out.println("No es un número.");
        }
    }
}
```

- `\\d+` significa: "uno o más dígitos (0-9)".

---

### 2. Buscar correos electrónicos en un texto

```java
import java.util.regex.Pattern;
import java.util.regex.Matcher;

public class EmailFinder {
    public static void main(String[] args) {
        String regex = "[\\w.-]+@[\\w.-]+\\.\\w+";
        String text = "Mis correos son ejemplo@mail.com y contacto@empresa.org";

        Pattern pattern = Pattern.compile(regex);
        Matcher matcher = pattern.matcher(text);

        while (matcher.find()) {
            System.out.println("Correo encontrado: " + matcher.group());
        }
    }
}
```

- `[\\w.-]+@[\\w.-]+\\.\\w+` busca correos simples.

---

### 3. Reemplazar números por "X"

```java
public class ReplaceNumbers {
    public static void main(String[] args) {
        String text = "Mi número es 1234 y el de mi amigo es 5678";
        String replaced = text.replaceAll("\\d+", "X");

        System.out.println(replaced);
    }
}
```

**Salida:**
```
Mi número es X y el de mi amigo es X
```

---

## 🎨 Componentes comunes de un patrón

| Símbolo | Significado                            | Ejemplo             |
|:--------|:----------------------------------------|:--------------------|
| `.`      | Cualquier carácter                     | `a.b` (match "acb", "a1b") |
| `\\d`    | Dígito (0-9)                           | `\\d+` (uno o más dígitos) |
| `\\w`    | Letra, número o guion bajo (_)          | `\\w+` (palabra) |
| `\\s`    | Espacio en blanco                      | `\\s+` (uno o más espacios) |
| `*`      | Cero o más veces                       | `a*` (ninguna o muchas 'a') |
| `+`      | Una o más veces                        | `a+` (una o muchas 'a') |
| `?`      | Cero o una vez                         | `a?` (opcional 'a') |
| `[...]`  | Un conjunto de caracteres              | `[abc]` (a o b o c) |
| `|`      | Alternativa (OR)                       | `a|b` (a o b) |

---

## 🖌️ Ejemplos adicionales de Regex

| Patrón        | Qué hace                                              | Ejemplo de uso                     |
|---------------|-------------------------------------------------------|-----------------------------------|
| `^\d{3}-\d{2}-\d{4}$` | Valida un número tipo SSN en EE.UU. | `123-45-6789`                      |
| `^[A-Z][a-z]+$`       | Palabra que inicia en mayúscula y sigue en minúscula | `Pedro`                         |
| `\bcat\b`             | Palabra exacta "cat" (no "concatenate")          | `cat`                             |
| `(\d{2})/(\d{2})/(\d{4})` | Fecha en formato DD/MM/AAAA                 | `23/04/2025`                      |
| `https?://[\w.-]+`    | URL que empieza con http o https                | `https://ejemplo.com`              |
| `^[01]?\d/\d{2}$`     | Hora en formato 24h o 12h                      | `09/30` o `23/59`                  |

---

## ✨ Mejoras en Java 21

Java 21 **no cambia la API de regex**, pero gracias a:
- **Pattern Matching mejorado** (para clases `Pattern` o `Matcher`).
- **Nuevas expresiones switch**.

Se pueden integrar patrones regex de forma más limpia en tu código moderno.

Ejemplo de combinación moderna:

```java
String text = "123";
if (Pattern.compile("\\d+").asMatchPredicate().test(text)) {
    System.out.println("Texto válido");
}
```

- `asMatchPredicate()` crea una función que directamente prueba si el texto cumple con el patrón.

---

# 📝 Resumen

- **Regex** = herramienta para buscar, validar o reemplazar texto basado en un patrón.
- **`Pattern` y `Matcher`** son las clases principales en Java.
- Java 21 permite usar **Predicates** para hacer tu código más limpio y funcional.

