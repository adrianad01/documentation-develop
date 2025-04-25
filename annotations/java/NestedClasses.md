# Clases Anidadas (Nested Classes) en Java 21

## ¿Qué son?

Una **clase anidada** es una clase definida dentro de otra clase. Se usa para mejorar la organización, encapsulación y legibilidad del código.

---

## Tipos de clases anidadas

| Tipo                    | Descripción                                                         |
|-------------------------|---------------------------------------------------------------------|
| Static Nested Class     | Clase estática. No necesita instancia de la clase externa.          |
| Inner Class             | Clase NO estática. Necesita una instancia de la clase externa.      |
| Local Class             | Clase definida dentro de un método.                                |
| Anonymous Class         | Clase sin nombre. Se usa para sobreescribir métodos al vuelo.       |

---

## Ejemplos

### 1. Static Nested Class

```java
public class Contenedor {
    static class EstaticaInterna {
        void saludar() {
            System.out.println("Hola desde clase anidada estática");
        }
    }

    public static void main(String[] args) {
        Contenedor.EstaticaInterna obj = new Contenedor.EstaticaInterna();
        obj.saludar();
    }
}
```

---

### 2. Inner Class

```java
public class Contenedor {
    class Interna {
        void saludar() {
            System.out.println("Hola desde clase interna");
        }
    }

    public static void main(String[] args) {
        Contenedor cont = new Contenedor();
        Contenedor.Interna obj = cont.new Interna();
        obj.saludar();
    }
}
```

---

### 3. Local Class

```java
public class Contenedor {
    void metodoConClaseInterna() {
        class Local {
            void imprimir() {
                System.out.println("Clase definida dentro de un método");
            }
        }

        Local local = new Local();
        local.imprimir();
    }

    public static void main(String[] args) {
        new Contenedor().metodoConClaseInterna();
    }
}
```

---

### 4. Anonymous Class

```java
public class EjemploAnonima {

    interface Saludo {
        void decirHola();
    }

    public static void main(String[] args) {
        Saludo saludo = new Saludo() {
            @Override
            public void decirHola() {
                System.out.println("Hola desde clase anónima");
            }
        };

        saludo.decirHola();
    }
}
```

---

## ¿Cuándo usar cada una?

| Caso                                                             | Tipo de clase sugerida      |
|------------------------------------------------------------------|-----------------------------|
| No accede a miembros externos                                    | Static Nested Class         |
| Necesita miembros de la clase externa                            | Inner Class                 |
| Solo se necesita dentro de un método                            | Local Class                 |
| Lógica temporal o rápida (sobrescribir métodos)                  | Anonymous Class             |