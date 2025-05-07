# 🧠 Polimorfismo en Java 21

## ¿Qué es el Polimorfismo?

Polimorfismo significa que una **misma cosa puede comportarse de diferentes maneras**.

Imagina un control remoto que puede encender una TV, un ventilador o un aire acondicionado.  
Mismo botón, diferentes acciones. En Java, eso pasa con clases y métodos.

---

## Tipos de Polimorfismo

### 1. Polimorfismo en tiempo de compilación (estático)

También llamado **sobrecarga de métodos**.

```java
public class Calculadora {
    int sumar(int a, int b) {
        return a + b;
    }

    double sumar(double a, double b) {
        return a + b;
    }

    int sumar(int a, int b, int c) {
        return a + b + c;
    }
}
```

---

### 2. Polimorfismo en tiempo de ejecución (dinámico)

También llamado **sobrescritura de métodos**.

```java
class Animal {
    void hacerSonido() {
        System.out.println("Algún sonido");
    }
}

class Perro extends Animal {
    @Override
    void hacerSonido() {
        System.out.println("Guau guau");
    }
}

class Gato extends Animal {
    @Override
    void hacerSonido() {
        System.out.println("Miau");
    }
}
```

Uso del polimorfismo:

```java
Animal a1 = new Perro();
Animal a2 = new Gato();

a1.hacerSonido(); // Guau guau
a2.hacerSonido(); // Miau
```

---

## ¿Para qué sirve el polimorfismo?

- ✅ Flexibilidad: código más genérico.
- ✅ Reutilización: trabajar con distintas clases fácilmente.
- ✅ Mantenibilidad: fácil de extender y mantener.

---

## Ejemplo completo

```java
public class Main {
    public static void main(String[] args) {
        Animal miAnimal = new Perro();
        miAnimal.hacerSonido(); // Guau guau

        miAnimal = new Gato();
        miAnimal.hacerSonido(); // Miau
    }
}
```