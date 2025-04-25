
# 🧱 Módulos en Java (Java Platform Module System - JPMS)

## 🔹 ¿Qué es un módulo?

Un **módulo** en Java es una unidad de empaquetado que agrupa paquetes y recursos. Fue introducido en **Java 9** con el objetivo de mejorar la escalabilidad, seguridad y mantenimiento del código, especialmente en aplicaciones grandes.

Cada módulo tiene:
- Un archivo especial llamado `module-info.java`
- Sus propios paquetes y clases
- Control sobre qué paquetes expone y qué requiere de otros módulos

---

## 🧾 Estructura básica

```java
module com.ejemplo.saludos {
    exports com.ejemplo.saludos;
}
```

- `com.ejemplo.saludos`: es el **nombre del módulo**
- `exports`: indica qué paquetes pueden ser usados por otros módulos

---

## 📁 Ejemplo paso a paso

### 🎯 Paso 1: Crear dos módulos

#### Módulo `mod.saludos`

```java
// module-info.java
module mod.saludos {
    exports saludos;
}
```

```java
// saludos/Saludo.java
package saludos;

public class Saludo {
    public static String mensaje() {
        return "¡Hola desde el módulo saludos!";
    }
}
```

#### Módulo `mod.main`

```java
// module-info.java
module mod.main {
    requires mod.saludos;
}
```

```java
// app/Main.java
package app;

import saludos.Saludo;

public class Main {
    public static void main(String[] args) {
        System.out.println(Saludo.mensaje());
    }
}
```

---

## 🧠 ¿Cuándo usar módulos?

- Cuando tienes aplicaciones grandes y deseas controlar qué paquetes se exponen
- Cuando quieres reducir el tamaño del classpath
- Para mejorar la seguridad evitando acceso no deseado a clases internas
- En proyectos multi-módulo o librerías compartidas

---

## ⚖️ Diferencias con paquetes

| Característica         | Paquetes                   | Módulos                            |
|------------------------|----------------------------|------------------------------------|
| Nivel de encapsulamiento | Bajo (todo es público por defecto) | Alto (se controla con `exports`)   |
| Organización           | Solo agrupa clases         | Agrupa paquetes y gestiona dependencias |
| Seguridad              | Limitada                   | Se puede restringir qué se expone |
| Introducido en         | Desde Java 1.0             | Desde Java 9                       |

---

## 🛠️ Compilación y ejecución con módulos

```bash
# Compilar
javac -d out/mod.saludos mod.saludos/module-info.java saludos/Saludo.java
javac --module-path out -d out/mod.main mod.main/module-info.java app/Main.java

# Ejecutar
java --module-path out -m mod.main/app.Main
```

---

## 📌 Notas adicionales con Java 21

- El sistema de módulos **sigue presente** en Java 21 sin cambios significativos respecto a Java 17.
- No es obligatorio usar módulos, pero es recomendable en arquitecturas limpias o distribuidas.

---

## 🌍 ¿Dónde se usa en el mundo real?

- En frameworks modernos como **JavaFX**, que está modularizado.
- En aplicaciones corporativas con múltiples capas.
- En proyectos que usan **JLink** para crear runtimes personalizados.
