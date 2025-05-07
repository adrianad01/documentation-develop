
# Valor vs Referencia en Java (Java 21)

## 🧠 ¿Qué significa "por valor" y "por referencia"?

Imagina que tienes dos formas de prestar tus juguetes:

- 🎁 **Por valor:** Le das una **copia** de tu juguete a tu amigo. Si él lo rompe, **tu juguete sigue igual**.
- 🔗 **Por referencia:** Le prestas **el juguete real**. Si lo rompe, **tu juguete también se rompe**.

En Java, funciona así:

- Los **tipos primitivos** (`int`, `double`, `char`, etc.) se pasan **por valor**.
- Los **objetos** (como `String`, `ArrayList`, tus propias clases) se pasan también **por valor**, **pero** lo que se copia es la **referencia al objeto**, no el objeto en sí.

---

## 🧪 Ejemplo 1: Por valor (tipos primitivos)

```java
public class ValorVsReferencia {
    public static void main(String[] args) {
        int numeroOriginal = 10;
        cambiarNumero(numeroOriginal);
        System.out.println("Después: " + numeroOriginal); // Imprime 10
    }

    static void cambiarNumero(int numero) {
        numero = 99; // Cambia la copia, no el original
    }
}
```

---

## 🧪 Ejemplo 2: Por "referencia" (objetos)

```java
import java.util.ArrayList;

public class ValorVsReferencia {
    public static void main(String[] args) {
        ArrayList<String> lista = new ArrayList<>();
        lista.add("Hola");

        modificarLista(lista);
        System.out.println("Después: " + lista); // Imprime [Hola, Mundo]
    }

    static void modificarLista(ArrayList<String> l) {
        l.add("Mundo"); // Se modifica el objeto original
    }
}
```

---

## 🎓 Resumen

| Tipo de dato       | ¿Qué se pasa al método?        | ¿Se puede cambiar el original? |
|--------------------|-------------------------------|-------------------------------|
| `int`, `double`, etc. | Copia del valor               | ❌ No                         |
| Objetos (`String`, `ArrayList`, etc.) | Copia de la referencia       | ✅ Sí, el objeto sí se puede modificar |
