## 🔩 Introducción a las Annotations en Java

### 🌍 ¿Qué son?
Las *annotations* (anotaciones) en Java son metadatos que se añaden al código fuente para proporcionar información adicional al compilador o a herramientas externas. No cambian directamente la lógica del programa, pero ayudan a validarlo o extender su funcionalidad.

---

### 🔐 Ejemplos de Annotations Comunes

#### 1. `@Override`
Indica que un método está sobrescribiendo uno de una clase padre o interfaz.
```java
class Animal {
    void hacerSonido() {
        System.out.println("Sonido genérico");
    }
}

class Perro extends Animal {
    @Override
    void hacerSonido() {
        System.out.println("Guau guau");
    }
}
```

#### 2. `@Deprecated`
Marca un método como obsoleto. El compilador puede lanzar advertencias si se usa.
```java
@Deprecated
void metodoAntiguo() {
    System.out.println("Este método está obsoleto");
}
```

#### 3. `@SuppressWarnings`
Ignora ciertas advertencias del compilador.
```java
@SuppressWarnings("unchecked")
void ejemplo() {
    List lista = new ArrayList();
}
```

#### 4. `@FunctionalInterface`
Indica que una interfaz solo debe tener un método abstracto (ideal para lambdas).
```java
@FunctionalInterface
interface Operacion {
    int aplicar(int a, int b);
}
```

---

### 🛠️ Uso y ámbitos
Las anotaciones pueden aplicarse a:
- Clases e interfaces
- Métodos
- Campos o variables
- Parámetros
- Paquetes o módulos

---

### 🧰 Crear una Annotation Personalizada
Las anotaciones personalizadas son útiles cuando necesitas agregar reglas o comportamientos específicos en tu aplicación. Por ejemplo, podrías usarlas para marcar métodos que requieren validación especial, para registrar acciones, o definir roles de acceso.

#### 1. Definición de la annotation
```java
import java.lang.annotation.*;

@Retention(RetentionPolicy.RUNTIME) // Disponible en tiempo de ejecución
@Target(ElementType.METHOD)         // Aplicable solo a métodos
public @interface MiAnotacion {
    String autor();
    String fecha();
}
```

- `@Retention(RetentionPolicy.RUNTIME)` indica que la anotación estará disponible en tiempo de ejecución para poder ser leída mediante reflexión.
- `@Target(ElementType.METHOD)` especifica que esta anotación solo se puede aplicar a métodos.

#### 2. Uso en un método
```java
@MiAnotacion(autor = "Adrián", fecha = "2025-04-24")
public void procesar() {
    System.out.println("Método procesar ejecutado");
}
```

#### 3. Leer la annotation con reflexión
```java
import java.lang.reflect.Method;

public class LectorAnotacion {
    public static void main(String[] args) throws Exception {
        Method metodo = ClaseEjemplo.class.getMethod("procesar");

        if (metodo.isAnnotationPresent(MiAnotacion.class)) {
            MiAnotacion anotacion = metodo.getAnnotation(MiAnotacion.class);
            System.out.println("Autor: " + anotacion.autor());
            System.out.println("Fecha: " + anotacion.fecha());
        }
    }
}
```

Esta lectura te permite adaptar dinámicamente el comportamiento de tu aplicación según los metadatos definidos con la annotation.

---

### ✅ Resumen

| Anotación             | Descripción                                     |
|-----------------------|-------------------------------------------------|
| `@Override`           | Asegura que un método está sobrescribiendo otro |
| `@Deprecated`         | Marca código como obsoleto                      |
| `@SuppressWarnings`   | Suprime advertencias del compilador            |
| `@FunctionalInterface`| Indica una interfaz funcional                   |
| `@interface`          | Crea una anotación personalizada                |

---

Este archivo te da una vista general pero muy clara para comenzar a trabajar con anotaciones en Java. ¡Ideal para programadores que están empezando!

