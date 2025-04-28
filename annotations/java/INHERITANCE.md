# 📚 Inheritance en Java 21

## ¿Qué es la herencia?

La **herencia** es un principio fundamental de la **Programación Orientada a Objetos (OOP)** que permite que una clase adquiera (**herede**) propiedades y comportamientos de otra clase.

- **Clase Padre (Superclase)**: Proporciona atributos y métodos.
- **Clase Hija (Subclase)**: Hereda esos atributos y métodos.

> **Beneficio**: Reutilizar código y construir jerarquías lógicas.

---

## 📊 Sintaxis básica

```java
class Animal { // Superclase
    void comer() {
        System.out.println("Este animal come");
    }
}

class Perro extends Animal { // Subclase
    void ladrar() {
        System.out.println("El perro ladra");
    }
}
```

`Perro` hereda el método `comer()` de `Animal`.

---

## 🛠 Ejemplo práctico explicado

```java
public class Animal {
    void makeSound() {
        System.out.println("El animal hace un sonido");
    }
}

public class Dog extends Animal {
    void bark() {
        System.out.println("El perro ladra: ¡Guau!");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.makeSound(); // Heredado de Animal
        dog.bark();      // Propio de Dog
    }
}
```

**Salida:**
```
El animal hace un sonido
El perro ladra: ¡Guau!
```

---

## 🌟 Ventajas principales

- Evitar **duplicación** de código.
- Permitir comportamientos **comunes** en distintas clases.
- Facilitar la **extensión** y el **mantenimiento** del código.

---

## 🧬 Conceptos clave en Herencia

| Concepto                   | Explicación                                                                 |
|-----------------------------|------------------------------------------------------------------------------|
| **extends**                 | Palabra clave para heredar de una clase.                                     |
| **super**                   | Referencia a la superclase para constructores o métodos.                    |
| **@Override**               | Anotación para sobrescribir métodos heredados correctamente.               |
| **Herencia simple**         | Java permite heredar de una sola clase padre (no herencia múltiple de clases). |

---

## 📦 Uso de `super`

```java
class Animal {
    Animal() {
        System.out.println("Animal creado");
    }

    void comer() {
        System.out.println("Animal comiendo");
    }
}

class Gato extends Animal {
    Gato() {
        super(); // Llama al constructor de Animal
        System.out.println("Gato creado");
    }

    void comer() {
        super.comer(); // Llama al método de Animal
        System.out.println("Gato comiendo su comida");
    }
}
```

**Salida:**
```
Animal creado
Gato creado
Animal comiendo
Gato comiendo su comida
```

---

## ✨ Resumen rápido

- `extends` = Hacemos que una clase herede otra.
- `super` = Accedemos a constructor/métodos de la superclase.
- Java **no** permite herencia múltiple de clases (sí de interfaces).
- La herencia permite **reutilizar y extender** funcionalidades.
- Usa `@Override` para evitar errores al sobrescribir.

---

## 👊 Tips modernos (Java 17+ / 21)

### → Usa `sealed classes` para controlar quién puede heredar

```java
public sealed class Animal permits Dog, Cat {
}

public final class Dog extends Animal {
}

public final class Cat extends Animal {
}
```

- `sealed` = La clase **limita** qué otras clases pueden extenderla.
- `final` = No permite que otras clases hereden más de `Dog` o `Cat`.

Perfecto para arquitecturas más **seguras y controladas**.

---

# 📄 Fin del resumen de Inheritance en Java 21

