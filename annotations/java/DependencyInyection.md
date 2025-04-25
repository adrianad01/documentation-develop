# Inyección de Dependencias en Java (Java 21)

## 🧩 ¿Qué es la Inyección de Dependencias?

La **Inyección de Dependencias (DI)** es un **patrón de diseño** que permite **desacoplar clases** de sus dependencias, facilitando el mantenimiento, las pruebas y la reutilización de código.

---

## ⚙️ Ejemplo sin Inyección de Dependencias

```java
public class Motor {
    public void encender() {
        System.out.println("Motor encendido");
    }
}

public class Auto {
    private Motor motor;

    public Auto() {
        this.motor = new Motor(); // Dependencia creada internamente
    }

    public void arrancar() {
        motor.encender();
    }
}
```

---

## ✅ Ejemplo con Inyección de Dependencias (Manual)

```java
public class Auto {
    private Motor motor;

    public Auto(Motor motor) {
        this.motor = motor; // Inyección por constructor
    }

    public void arrancar() {
        motor.encender();
    }
}
```

Uso:

```java
public class Main {
    public static void main(String[] args) {
        Motor motor = new Motor();
        Auto auto = new Auto(motor);
        auto.arrancar();
    }
}
```

---

## 🛠️ Tipos de Inyección

| Tipo                     | Descripción                                                             |
|--------------------------|-------------------------------------------------------------------------|
| **Constructor**          | Se inyecta a través del constructor                                     |
| **Setter / método**      | Se inyecta usando un método `set` o similar                             |
| **Campo (field)**        | Se inyecta directamente en un atributo (más usado con frameworks)       |

---

## ☕ Inyección de Dependencias con Spring Framework

```java
@Component
public class Motor {
    public void encender() {
        System.out.println("Motor encendido (Spring)");
    }
}
```

```java
@Component
public class Auto {
    private final Motor motor;

    @Autowired
    public Auto(Motor motor) {
        this.motor = motor;
    }

    public void arrancar() {
        motor.encender();
    }
}
```

```java
@SpringBootApplication
public class App {
    public static void main(String[] args) {
        ApplicationContext context = SpringApplication.run(App.class, args);
        Auto auto = context.getBean(Auto.class);
        auto.arrancar();
    }
}
```

---

## 🧪 Ventajas

- Bajo acoplamiento
- Mayor reutilización
- Fácil de testear
- Compatible con principios SOLID

---

## 🧠 Relación con Java 21

Java 21 mejora el lenguaje, pero DI se sigue aplicando con frameworks como Spring o Jakarta.

---

## 🧪 Prueba Unitaria

```java
@Test
void testArranque() {
    Motor mockMotor = Mockito.mock(Motor.class);
    Auto auto = new Auto(mockMotor);

    auto.arrancar();

    verify(mockMotor).encender();
}
```