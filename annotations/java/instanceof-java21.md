
# `instanceof` en Java 21

## ¿Qué es `instanceof`?

El operador `instanceof` se utiliza para verificar si un objeto es una instancia de una clase o subclase específica. Desde Java 16, y vigente en Java 21, también permite hacer Pattern Matching.

---

## Sintaxis básica

```java
obj instanceof Clase
```

---

## Ejemplo clásico (antes de Java 16)

```java
Object obj = "Hola mundo";

if (obj instanceof String) {
    String s = (String) obj;
    System.out.println("La longitud es: " + s.length());
}
```

---

## Ejemplo con Pattern Matching (Java 16+)

```java
Object obj = "Hola mundo";

if (obj instanceof String s) {
    System.out.println("La longitud es: " + s.length());
}
```

---

## Ejemplo con jerarquía de clases

```java
class Animal {}
class Perro extends Animal {
    void ladrar() {
        System.out.println("¡Guau!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Perro();

        if (a instanceof Perro p) {
            p.ladrar();
        }
    }
}
```

---

## instanceof con interfaces

```java
interface Volador {
    void volar();
}

class Pajaro implements Volador {
    public void volar() {
        System.out.println("Estoy volando");
    }
}

Object o = new Pajaro();

if (o instanceof Volador v) {
    v.volar();
}
```

---

## Buenas prácticas

- Prefiere el polimorfismo cuando sea posible.
- Utiliza pattern matching para escribir código más limpio.
- Úsalo en condiciones donde no se puede conocer el tipo exacto en tiempo de compilación.
