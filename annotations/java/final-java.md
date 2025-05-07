# `final` en Java

La palabra clave `final` se utiliza para **restringir la modificación**. Puede aplicarse a:

1. **Variables**: no se pueden reasignar.
2. **Métodos**: no se pueden sobrescribir (override).
3. **Clases**: no se pueden heredar.

---

## Uso de `final` en variables

Una variable `final` se comporta como una **constante**: solo puede asignarse una vez.

```java
final int edad = 30;
edad = 40; // ❌ Error: no se puede cambiar un valor final
```

Si se declara sin valor, puede inicializarse **una sola vez** más adelante:

```java
final int edad;
edad = 25; // ✅ permitido
edad = 30; // ❌ error
```

### En objetos (`final` con referencias)

```java
final List<String> nombres = new ArrayList<>();
nombres.add("Ana"); // ✅ permitido (se modifica el contenido)
nombres = new ArrayList<>(); // ❌ no permitido (no se puede cambiar la referencia)
```

---

## Uso de `final` en métodos

Impide que un método sea **sobrescrito por una subclase**.

```java
class Animal {
    public final void respirar() {
        System.out.println("Respirando...");
    }
}

class Perro extends Animal {
    // ❌ Error: no se puede sobrescribir
    // public void respirar() { }
}
```

---

## Uso de `final` en clases

Una clase `final` **no puede tener subclases** (no se puede heredar).

```java
final class Utilidades {
    public static void imprimir(String msg) {
        System.out.println(msg);
    }
}

class MiClase extends Utilidades { // ❌ Error
}
```

---

## Cuándo usar `final`

| Contexto         | Uso recomendado |
|------------------|------------------|
| Variables        | Para constantes o parámetros inmutables |
| Métodos          | Para asegurar que una lógica no se altere en subclases |
| Clases           | Para clases utilitarias o de seguridad (como `String`, `Integer`) |

---

## Ejemplo combinado

```java
final class Constantes {
    public static final double PI = 3.1416;
}

class Circulo {
    private final double radio;

    public Circulo(double radio) {
        this.radio = radio;
    }

    public final double calcularArea() {
        return Constantes.PI * radio * radio;
    }
}
```