
# Overloading vs Overriding en Java 21

## 🧠 ¿Qué son Overloading y Overriding?

| Concepto        | Significado                                                                 | Dónde aplica                    |
|-----------------|------------------------------------------------------------------------------|---------------------------------|
| **Overloading** | Sobrecarga: varios métodos con el mismo nombre pero distintos parámetros     | Dentro de **una misma clase**  |
| **Overriding**  | Sobrescritura: redefinir un método heredado de una superclase                | Entre una **superclase y subclase** |

---

## 🔁 Overloading (Sobrecarga de métodos)

### ✅ Qué es
Cuando defines **varios métodos con el mismo nombre**, pero **con diferentes parámetros** (tipo, orden o cantidad).

### 📌 Reglas
- Mismo nombre.
- Diferente firma del método (parámetros).
- Puede tener distinto tipo de retorno.

### 📦 Ejemplo:

```java
public class Calculadora {

    public int sumar(int a, int b) {
        return a + b;
    }

    public double sumar(double a, double b) {
        return a + b;
    }

    public int sumar(int a, int b, int c) {
        return a + b + c;
    }
}
```

```java
Calculadora calc = new Calculadora();
System.out.println(calc.sumar(2, 3));         // Usa sumar(int, int)
System.out.println(calc.sumar(2.5, 3.5));     // Usa sumar(double, double)
System.out.println(calc.sumar(1, 2, 3));      // Usa sumar(int, int, int)
```

---

## 🧬 Overriding (Sobrescritura de métodos)

### ✅ Qué es
Cuando una subclase **vuelve a definir un método** que ya existía en la superclase, para **modificar su comportamiento**.

### 📌 Reglas
- Misma firma (nombre + parámetros).
- Mismo tipo de retorno o un subtipo (covarianza).
- El método en la superclase debe ser `public` o `protected`, y **no puede ser `private` o `final`**.
- Se recomienda usar `@Override`.

### 📦 Ejemplo:

```java
class Animal {
    public void hacerSonido() {
        System.out.println("Algún sonido genérico");
    }
}

class Perro extends Animal {
    @Override
    public void hacerSonido() {
        System.out.println("Guau Guau!");
    }
}
```

```java
Animal miAnimal = new Perro();
miAnimal.hacerSonido(); // Guau Guau!
```

---

## 📋 Diferencias Clave

| Característica         | Overloading                               | Overriding                           |
|------------------------|-------------------------------------------|--------------------------------------|
| ¿Dónde ocurre?         | En la **misma clase**                     | Entre **superclase y subclase**      |
| Firma del método       | **Debe cambiar** (parámetros)             | **Debe ser igual**                   |
| Tipo de retorno        | Puede variar                              | Debe ser igual o subtipo             |
| Tiempo de decisión     | **Compilación**                           | **Ejecución (polimorfismo)**         |
