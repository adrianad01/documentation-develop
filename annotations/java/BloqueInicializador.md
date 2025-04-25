
# 🧱 Bloque Inicializador en Java (Java 21)

En Java, un **bloque inicializador** es una sección de código que se ejecuta automáticamente cuando se **crea un objeto** o cuando se **carga una clase**. Hay dos tipos:

1. **Bloque de instancia**: se ejecuta cada vez que se crea un objeto.
2. **Bloque estático**: se ejecuta solo una vez cuando se carga la clase.

---

## 🔹 Bloque de instancia

### ✅ ¿Qué es?

Un bloque de código que **se ejecuta antes del constructor** cada vez que creas un objeto (`new Clase()`).

### 📌 Sintaxis

```java
{
    // Código que se ejecuta al crear un objeto
}
```

### 🧪 Ejemplo práctico

```java
public class Persona {
    String nombre;

    // Bloque inicializador de instancia
    {
        System.out.println("Estoy en el bloque inicializador");
        nombre = "Sin nombre";
    }

    public Persona() {
        System.out.println("Estoy en el constructor");
    }

    public static void main(String[] args) {
        Persona p = new Persona();
    }
}
```

### 🧠 Salida esperada

```
Estoy en el bloque inicializador
Estoy en el constructor
```

### 🧰 ¿Para qué sirve?

- Para código que debe ejecutarse **en todos los constructores**.
- Para **inicializar atributos** antes del constructor.

---

## 🔸 Bloque estático

### ✅ ¿Qué es?

Un bloque que se ejecuta **una sola vez**, cuando la clase se carga por primera vez (antes de cualquier constructor o método estático).

### 📌 Sintaxis

```java
static {
    // Código que se ejecuta al cargar la clase
}
```

### 🧪 Ejemplo práctico

```java
public class Utilidad {

    // Bloque estático
    static {
        System.out.println("Cargando la clase Utilidad...");
    }

    public static void metodo() {
        System.out.println("Método ejecutado");
    }

    public static void main(String[] args) {
        Utilidad.metodo();
    }
}
```

### 🧠 Salida esperada

```
Cargando la clase Utilidad...
Método ejecutado
```

---

## 🆚 Diferencias clave

| Tipo de bloque        | ¿Cuándo se ejecuta?                  | ¿Cuántas veces? | ¿Necesita `static`? |
|-----------------------|--------------------------------------|------------------|----------------------|
| Instancia             | Al crear un objeto (`new Clase()`)   | Varias veces     | ❌                   |
| Estático              | Al cargar la clase por primera vez   | Solo una vez     | ✅                   |

---

## 🧠 Conclusión

Los bloques inicializadores permiten organizar mejor el código que **siempre se debe ejecutar**, ya sea al **crear objetos** (bloques de instancia) o al **cargar la clase** (bloques estáticos).
