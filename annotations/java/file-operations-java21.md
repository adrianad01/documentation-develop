
# 📂 File Operations en Java 21

Cuando quieres guardar, leer o borrar archivos en tu computadora, Java te ayuda con clases como `Files` y `Path` del paquete `java.nio.file`.

---

## ✅ Verificar si un archivo existe

```java
import java.nio.file.*;

public class VerificarArchivo {
    public static void main(String[] args) {
        Path ruta = Paths.get("archivo.txt");

        if (Files.exists(ruta)) {
            System.out.println("¡Sí existe!");
        } else {
            System.out.println("No lo encuentro 😢");
        }
    }
}
```

---

## 📝 Escribir en un archivo (crear si no existe)

```java
import java.nio.file.*;
import java.io.IOException;
import java.util.List;

public class EscribirArchivo {
    public static void main(String[] args) throws IOException {
        Path ruta = Paths.get("archivo.txt");
        List<String> lineas = List.of("Hola mundo", "Estoy escribiendo en un archivo!");
        Files.write(ruta, lineas);
    }
}
```

---

## 📖 Leer un archivo línea por línea

```java
import java.nio.file.*;
import java.io.IOException;
import java.util.List;

public class LeerArchivo {
    public static void main(String[] args) throws IOException {
        Path ruta = Paths.get("archivo.txt");
        List<String> lineas = Files.readAllLines(ruta);
        for (String linea : lineas) {
            System.out.println(linea);
        }
    }
}
```

---

## 🗑️ Borrar un archivo

```java
import java.nio.file.*;
import java.io.IOException;

public class BorrarArchivo {
    public static void main(String[] args) throws IOException {
        Path ruta = Paths.get("archivo.txt");
        Files.deleteIfExists(ruta);
        System.out.println("Archivo eliminado 😎");
    }
}
```

---

## 📁 Crear una carpeta

```java
import java.nio.file.*;
import java.io.IOException;

public class CrearCarpeta {
    public static void main(String[] args) throws IOException {
        Path carpeta = Paths.get("mi_carpeta");

        if (!Files.exists(carpeta)) {
            Files.createDirectory(carpeta);
            System.out.println("Carpeta creada!");
        }
    }
}
```

---

## ℹ️ Notas

- Usa `java.nio.file` para trabajar con archivos y carpetas.
- `Path` representa la ruta del archivo o carpeta.
- `Files` contiene métodos para leer, escribir, borrar y más.

Ideal para proyectos con Java 21 y buenas prácticas modernas.
