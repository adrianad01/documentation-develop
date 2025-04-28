# 🛡️ Encapsulación en Java

## ¿Qué es la encapsulación?

La **encapsulación** es un **principio de la programación orientada a objetos (OOP)** que consiste en **ocultar** los detalles internos de una clase y **controlar el acceso** a sus datos.

👉 La idea principal es **proteger los datos** de accesos no autorizados o modificaciones accidentales, permitiendo que solo se manipulen a través de **métodos públicos controlados**.

---

## 📦 ¿Cómo se logra la encapsulación?

1. **Haciendo los atributos `private`**: Los campos de la clase no son accesibles directamente desde fuera.
2. **Proporcionando métodos `public` de acceso**: Estos son conocidos como **getters** y **setters**.

---

## ✨ Ejemplo sencillo

```java
public class Persona {
    // 1. Atributos privados
    private String nombre;
    private int edad;

    // 2. Constructor
    public Persona(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    // 3. Getter para nombre
    public String getNombre() {
        return nombre;
    }

    // 4. Setter para nombre
    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    // 5. Getter para edad
    public int getEdad() {
        return edad;
    }

    // 6. Setter para edad
    public void setEdad(int edad) {
        if (edad >= 0) { // Validación
            this.edad = edad;
        }
    }
}
```

---

## 🧐 ¿Qué está pasando aquí?

- **`private`**: Evita que `nombre` y `edad` se accedan directamente.
- **`getNombre()` y `getEdad()`**: Permiten **consultar** el valor de los atributos.
- **`setNombre()` y `setEdad()`**: Permiten **modificar** el valor, **controlando** si se permiten cambios (ejemplo: no permitir edades negativas).

---

## 📋 ¿Por qué usar encapsulación?

| Ventaja | Descripción |
|:--------|:------------|
| Seguridad | Protege los datos de cambios accidentales o malintencionados. |
| Control | Permite validar cambios antes de modificar los datos. |
| Flexibilidad | Se puede cambiar la implementación interna sin afectar a quienes usan la clase. |
| Mantenimiento | El código es más limpio y fácil de entender. |

---

## 🛠️ Uso en Java moderno (Java 21)

Aunque **Lombok** u otras herramientas automáticas son muy usadas hoy día para generar getters y setters sin escribir tanto código manualmente, **el concepto de encapsulación sigue siendo el mismo**:

```java
import lombok.Data;

@Data
public class Producto {
    private String nombre;
    private double precio;
}
```

- `@Data` automáticamente crea getters, setters, `toString`, `equals` y `hashCode`.
- Aun usando herramientas modernas, **nunca exponemos atributos como `public`** directamente.

---

# 🚀 Resumen

- **Encapsulación** = **ocultar datos** + **controlar acceso** mediante métodos.
- **`private` atributos**, **`public` getters/setters**.
- **Valida** dentro de setters si es necesario.
- En **Java 21**, puedes apoyarte en **anotaciones** como `@Data` de **Lombok** para simplificar el código.

