# 📚 Operaciones de Entrada/Salida (I/O) en Java

## ¿Qué es I/O en Java?

**I/O** significa **Input/Output** (Entrada/Salida) y en Java se refiere a cómo tu programa interactúa con el **exterior**: puede leer datos de archivos, teclado, red, etc., y escribir datos hacia archivos, pantalla, sockets, etc.

Java ofrece APIs muy potentes en los paquetes `java.io`, `java.nio` y otros más modernos.

---

## Tipos de I/O en Java

| Tipo                  | Descripción                                                               |
|------------------------|---------------------------------------------------------------------------|
| **Basado en Streams**  | Manejo de datos en forma de flujo continuo (ej. leer un archivo byte a byte). |
| **Basado en Reader/Writer** | Manejo de caracteres (especial para texto, respetando codificaciones como UTF-8). |
| **Basado en NIO (New I/O)**  | Más rápido y escalable (buffers, canales, paths, asíncrono). Desde Java 7/8. |

---

## 📅 Entrada Básica (Input) usando `Scanner`

```java
import java.util.Scanner;

public class InputExample {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Introduce tu nombre: ");
        String nombre = scanner.nextLine();
        System.out.println("Hola, " + nombre + "!");
        scanner.close();
    }
}
```

- `Scanner` simplifica la lectura de datos de entrada.

---

## 📄 Salida Básica (Output) usando `System.out`

```java
public class OutputExample {
    public static void main(String[] args) {
        System.out.println("¡Bienvenido a Java!");
    }
}
```

- `System.out` es un flujo de salida estándar (generalmente, la consola).

---

## 🧵 I/O basado en Streams (`InputStream` y `OutputStream`)

Lectura de bytes (ideal para archivos binarios como imágenes, audio, etc).

```java
import java.io.FileInputStream;
import java.io.IOException;

public class FileInputExample {
    public static void main(String[] args) {
        try (FileInputStream fis = new FileInputStream("archivo.txt")) {
            int contenido;
            while ((contenido = fis.read()) != -1) {
                System.out.print((char) contenido);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

- `read()` devuelve un byte a la vez.

---

## 🧵 I/O basado en Reader/Writer

Lectura de texto (ideal para archivos de texto, respetando UTF-8).

```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class BufferedReaderExample {
    public static void main(String[] args) {
        try (BufferedReader br = new BufferedReader(new FileReader("archivo.txt"))) {
            String linea;
            while ((linea = br.readLine()) != null) {
                System.out.println(linea);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

- `BufferedReader` mejora el rendimiento al leer grandes cantidades de datos.

---

## 📈 Mejoras con NIO (`java.nio.file`)

Desde Java 7, con NIO2 (`Paths`, `Files`, etc.), es mucho más sencillo.

```java
import java.nio.file.Files;
import java.nio.file.Path;
import java.io.IOException;

public class NIOExample {
    public static void main(String[] args) {
        try {
            String contenido = Files.readString(Path.of("archivo.txt"));
            System.out.println(contenido);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

- `Files.readString` lee todo el contenido en una sola llamada.

---

## 🧹 Buenas prácticas en I/O

- Siempre **cerrar** los flujos (`.close()`) o usar **try-with-resources**.
- **Manejar excepciones** (`IOException`) siempre.
- Preferir clases "**Buffered**" para eficiencia.
- Para archivos grandes, **usar NIO**.
- Cuidar la **codificación** (por ejemplo, `UTF-8`).

---

# 🧪 Ejercicio sencillo

Crear un programa que:

1. Pida el nombre del usuario.
2. Lo guarde en un archivo llamado `saludo.txt`.
3. Lea el archivo y lo imprima en consola.

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.Scanner;

public class SaludoIO {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("¿Cuál es tu nombre?: ");
        String nombre = scanner.nextLine();

        Path archivo = Path.of("saludo.txt");

        try {
            Files.writeString(archivo, "Hola, " + nombre + "!");
            String contenido = Files.readString(archivo);
            System.out.println(contenido);
        } catch (IOException e) {
            e.printStackTrace();
        }

        scanner.close();
    }
}
```

