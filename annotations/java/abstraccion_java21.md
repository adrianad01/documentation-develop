
# 📚 Abstracción en Java 21

## ¿Qué es la abstracción?

La **abstracción** es el proceso de **ocultar detalles internos** y **mostrar sólo lo esencial** de un objeto o comportamiento.

Se logra mediante:
- **Clases abstractas**
- **Interfaces**

---

## 🎯 Clases Abstractas

Una **clase abstracta**:
- **Puede** tener métodos abstractos y métodos normales.
- **No se puede instanciar directamente**.
- **Sirve como plantilla** para otras clases.

### Ejemplo:

```java
abstract class Animal {
    abstract void hacerSonido();
    
    void dormir() {
        System.out.println("Zzz...");
    }
}

class Perro extends Animal {

    @Override
    void hacerSonido() {
        System.out.println("El perro ladra: ¡Guau guau!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal miPerro = new Perro();
        miPerro.hacerSonido(); // El perro ladra: ¡Guau guau!
        miPerro.dormir();      // Zzz...
    }
}
```

---

## 🎯 Interfaces

Una **interfaz**:
- Define **comportamientos** sin implementación.
- **Desde Java 8** puede tener métodos `default` y `static` con implementación.
- **Puede ser implementada por múltiples clases**.

### Ejemplo:

```java
interface Volador {
    void volar();
}

class Pajaro implements Volador {

    @Override
    public void volar() {
        System.out.println("El pájaro vuela en el cielo.");
    }
}

public class Main {
    public static void main(String[] args) {
        Volador miPajaro = new Pajaro();
        miPajaro.volar(); // El pájaro vuela en el cielo.
    }
}
```

---

## 🚀 Diferencias entre Clase Abstracta e Interfaz

| Aspecto                  | Clase Abstracta                           | Interfaz                             |
|---------------------------|-------------------------------------------|--------------------------------------|
| Instanciación             | No se puede instanciar                    | No se puede instanciar               |
| Métodos                   | Puede tener abstractos y normales         | Solo abstractos, default o estáticos |
| Herencia/Implementación   | Se hereda con `extends`                   | Se implementa con `implements`       |
| Múltiple herencia         | Solo una clase abstracta a la vez         | Puede implementar múltiples interfaces |

---

## 🛠 Ejemplo Combinado

```java
interface Nadador {
    void nadar();
}

abstract class AnimalAcuatico {
    abstract void respirarBajoAgua();
}

class Delfin extends AnimalAcuatico implements Nadador {

    @Override
    public void nadar() {
        System.out.println("El delfín nada rápidamente.");
    }

    @Override
    void respirarBajoAgua() {
        System.out.println("El delfín respira usando sus pulmones.");
    }
}

public class Main {
    public static void main(String[] args) {
        Delfin delfin = new Delfin();
        delfin.nadar();            // El delfín nada rápidamente.
        delfin.respirarBajoAgua();  // El delfín respira usando sus pulmones.
    }
}
```

---

## ✅ Resumen

- **Abstracción** = Mostrar solo lo importante, ocultar detalles internos.
- **Clase abstracta** = Plantilla con métodos opcionalmente implementados.
- **Interfaz** = Solo define comportamientos (aunque ahora puede tener `default` y `static`).

---

# 🎯 Ejercicio Práctico

**Crea un programa que tenga:**
- Una clase abstracta `Vehiculo` con un método abstracto `moverse()`.
- Una interfaz `Electrico` con un método `cargarBateria()`.
- Una clase `CarroElectrico` que extienda de `Vehiculo` e implemente `Electrico`.

**Salida esperada:**
```
El carro eléctrico se está moviendo silenciosamente.
Cargando batería del carro eléctrico...
```
