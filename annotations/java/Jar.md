
# Archivos JAR en Java 21

## 🧪 ¿Qué es un archivo JAR?

Un **JAR (Java ARchive)** es un archivo comprimido que agrupa múltiples archivos `.class`, recursos (imágenes, archivos de propiedades, etc.) y metadatos en un solo archivo, generalmente con extensión `.jar`.

Se utiliza principalmente para:

- Distribuir aplicaciones Java.
- Reutilizar bibliotecas o librerías.
- Ejecutar aplicaciones directamente (`java -jar archivo.jar`).

---

## 🧱 Estructura de un archivo JAR

Un archivo `.jar` se basa en el formato ZIP e incluye:

```
mi-aplicacion.jar
│
├── META-INF/
│   └── MANIFEST.MF
│
├── com/
│   └── ejemplo/
│       └── MiClase.class
│
└── recursos/
    └── config.properties
```

---

## ✍️ Cómo crear un JAR desde consola

```java
// Archivo: HolaMundo.java
public class HolaMundo {
    public static void main(String[] args) {
        System.out.println("¡Hola desde el JAR!");
    }
}
```

1. Compilar:
```bash
javac HolaMundo.java
```

2. Crear JAR:
```bash
jar cfe hola.jar HolaMundo HolaMundo.class
```

3. Ejecutar:
```bash
java -jar hola.jar
```

---

## 📝 MANIFEST.MF

```txt
Manifest-Version: 1.0
Main-Class: HolaMundo
```

---

## 🧩 JAR como librería

Puedes usar clases desde otro proyecto:

```bash
javac -cp mi-libreria.jar MiAplicacion.java
java -cp .:mi-libreria.jar MiAplicacion
```

---

## 🚀 JAR ejecutable con Maven

```xml
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-jar-plugin</artifactId>
      <version>3.3.0</version>
      <configuration>
        <archive>
          <manifest>
            <mainClass>com.ejemplo.Main</mainClass>
          </manifest>
        </archive>
      </configuration>
    </plugin>
  </plugins>
</build>
```

Comando:
```bash
mvn package
```

---

## ✅ Ventajas

- Empaquetado simple de clases y recursos.
- Permite ejecución directa.
- Compatible con Maven, Gradle.
- Facilita distribución y reutilización.

---

## 📦 ¿Qué sigue?

Puedes usar `JMOD` o `jlink` para distribuir tu aplicación con una versión embebida del JDK.
