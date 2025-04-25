
# Interfaces en Java (Java 21)

## ¿Qué es una interface?
Una interfaz es un contrato que define qué métodos debe implementar una clase. No contiene lógica, solo firmas (salvo `default` y `static`).

## Características
- Métodos abstractos por defecto.
- Puede contener métodos `default` y `static` desde Java 8.
- Puede tener constantes (`public static final`).
- Soporta implementación múltiple.
- Interfaces funcionales para lambdas.

## Ejemplo Básico

```java
public interface Vehiculo {
    void conducir();
}

public class Carro implements Vehiculo {
    public void conducir() {
        System.out.println("Conduciendo un carro 🚗");
    }
}
```

## Métodos default y static

```java
public interface Calculadora {
    default void mensaje() {
        System.out.println("Soy una calculadora");
    }

    static int sumar(int a, int b) {
        return a + b;
    }
}
```

## Interfaces funcionales

```java
@FunctionalInterface
public interface Operacion {
    int aplicar(int a, int b);
}

Operacion suma = (a, b) -> a + b;
System.out.println(suma.aplicar(4, 5));
```

## Implementación múltiple

```java
interface Volador { void volar(); }
interface Nadador { void nadar(); }

class Pato implements Volador, Nadador {
    public void volar() { System.out.println("El pato vuela"); }
    public void nadar() { System.out.println("El pato nada"); }
}
```

## Clase abstracta vs Interface

| Concepto             | Clase Abstracta        | Interface                     |
|----------------------|------------------------|-------------------------------|
| Herencia             | Solo una               | Múltiples interfaces          |
| Métodos con lógica   | Sí                     | Desde Java 8 (`default`)      |
| Campos               | Variables normales     | Solo constantes (`static final`) |
| Uso típico           | Comportamiento común   | Contrato funcional            |
