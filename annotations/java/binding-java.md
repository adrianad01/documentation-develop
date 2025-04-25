# Binding Estático vs Dinámico en Java 21

## 📌 ¿Qué es el *Binding* en Java?

El **binding** (o enlace) es el proceso mediante el cual el compilador o la JVM asocia una llamada a un método con su definición real.

---

## 🧩 Tipos de Binding

### 1. 🔒 Binding Estático (Early Binding)

- También conocido como **compile-time binding**.
- La asociación entre la llamada a un método y su definición se hace **en tiempo de compilación**.
- Aplica a:
  - Métodos `static`
  - Métodos `final`
  - Métodos `private`
  - Variables

#### Ejemplo:

```java
class Animal {
    static void makeSound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    static void makeSound() {
        System.out.println("Dog sound");
    }
}

public class Test {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.makeSound(); // Salida: Animal sound
    }
}
```

🧠 Aunque `a` apunta a un `Dog`, el método `makeSound` es `static`, así que se hace binding estático y se llama al de `Animal`.

---

### 2. 🔄 Binding Dinámico (Late Binding)

- También llamado **runtime binding**.
- La asociación se hace **en tiempo de ejecución**, basada en el objeto real.
- Aplica a:
  - Métodos **no static**, no final, no private.

#### Ejemplo:

```java
class Animal {
    void makeSound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Dog sound");
    }
}

public class Test {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.makeSound(); // Salida: Dog sound
    }
}
```

🧠 Aquí, aunque la variable es de tipo `Animal`, el objeto real es `Dog`, así que se llama al método sobreescrito.

---

## 📊 Diferencias clave

| Característica              | Binding Estático                  | Binding Dinámico                     |
|----------------------------|-----------------------------------|--------------------------------------|
| Momento                    | En compilación                    | En ejecución                         |
| Métodos aplicables         | `static`, `final`, `private`     | Métodos de instancia (no `static`)   |
| Polimorfismo               | ❌ No aplica                      | ✅ Sí aplica                         |
| Performance                | Más rápido                        | Un poco más lento                    |
| Flexibilidad               | Menor                             | Mayor                                |

---

## ✅ ¿Cuándo usar cuál?

- Usa **binding estático** cuando no necesitas polimorfismo ni sobreescritura.
- Usa **binding dinámico** para aprovechar el polimorfismo, sobreescritura y comportamiento flexible en tiempo de ejecución.