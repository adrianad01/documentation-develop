
# Method Chaining en Java (Encadenamiento de Métodos)

## 🧩 ¿Qué es Method Chaining?

**Method Chaining** es un patrón donde se llaman múltiples métodos uno tras otro en una sola línea, y cada uno devuelve un objeto que permite continuar la cadena.

---

## 🔁 Requisitos

- Los métodos deben devolver el objeto actual (`this`) u otro encadenable.
- Muy usado en APIs Fluent, patrones Builder y configuraciones complejas.

---

## 📦 Ejemplo básico con `this`

```java
public class Persona {
    private String nombre;
    private int edad;

    public Persona setNombre(String nombre) {
        this.nombre = nombre;
        return this;
    }

    public Persona setEdad(int edad) {
        this.edad = edad;
        return this;
    }

    public void imprimir() {
        System.out.println("Nombre: " + nombre + ", Edad: " + edad);
    }

    public static void main(String[] args) {
        Persona persona = new Persona()
                .setNombre("Adrián")
                .setEdad(30);

        persona.imprimir(); // Nombre: Adrián, Edad: 30
    }
}
```

---

## 🛠 Ejemplo con Builder Pattern

```java
public class Auto {
    private String marca;
    private String modelo;

    private Auto() {}

    public static class Builder {
        private Auto auto;

        public Builder() {
            auto = new Auto();
        }

        public Builder setMarca(String marca) {
            auto.marca = marca;
            return this;
        }

        public Builder setModelo(String modelo) {
            auto.modelo = modelo;
            return this;
        }

        public Auto build() {
            return auto;
        }
    }

    public void mostrar() {
        System.out.println("Auto: " + marca + " " + modelo);
    }

    public static void main(String[] args) {
        Auto auto = new Auto.Builder()
                        .setMarca("Toyota")
                        .setModelo("Corolla")
                        .build();

        auto.mostrar(); // Auto: Toyota Corolla
    }
}
```

---

## ✅ Ventajas

| Ventaja                  | Descripción                                 |
|--------------------------|---------------------------------------------|
| ✅ Más legibilidad       | Código más limpio y expresivo.              |
| ✅ Menos líneas           | Se evita código repetitivo.                |
| ✅ Ideal para configuración | Muy útil en frameworks como Spring.       |

---

## ⚠️ Cuidados

- Puede dificultar el debugging.
- No abusar en métodos que realizan muchas tareas distintas.

---

## 🧪 Ejemplo con `StringBuilder`

```java
public class EjemploStringBuilder {
    public static void main(String[] args) {
        String resultado = new StringBuilder()
                .append("Hola")
                .append(" ")
                .append("mundo")
                .toString();

        System.out.println(resultado); // Hola mundo
    }
}
```

---

## 📌 Dónde se usa comúnmente

- `StringBuilder`, `StringBuffer`
- `Stream API`
- `Builder Pattern`
- Librerías como `AssertJ`, `Mockito`
- Configuraciones de objetos en frameworks como Spring, Hibernate
