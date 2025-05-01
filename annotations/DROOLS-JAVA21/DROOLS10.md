# 🧠 Etapa 1: Fundamentos de Drools con Java 21

---

## ✅ Lección 1: ¿Qué es Drools y qué problema resuelve?

### 📌 1. ¿Qué es Drools?

Drools es un *motor de reglas de negocio* (BRMS - Business Rule Management System) que permite:

- Definir reglas como condiciones + consecuencias
- Ejecutarlas sobre objetos Java (hechos)
- Separar la lógica de negocio del código fuente principal

Desde Drools 10 en adelante, ya **no necesitas archivos `.drl`**, puedes trabajar 100% en Java con el modelo canónico (Java DSL).

---

### 🆚 2. Lógica Imperativa vs. Declarativa

**Imperativa (Java clásico):**

```java
if (cliente.getEdad() > 18 && cliente.isActivo()) {
    System.out.println("Cliente válido");
}
```

**Declarativa (Drools):**

```java
rule "Cliente válido"
    when
        $c: Cliente(edad > 18, activo == true)
    then
        System.out.println("Cliente válido: " + $c.getNombre());
end
```

Drools decide **cómo y cuándo** ejecutar las reglas por ti.

---

### 🎯 3. ¿Qué problema resuelve?

| Problema                         | Solución con Drools                        |
|----------------------------------|--------------------------------------------|
| Lógica compleja dispersa         | Centralización de reglas                   |
| Cambios frecuentes en reglas     | Actualización sin tocar lógica de negocio  |
| Muchas condiciones combinadas    | Evaluación eficiente con Rete              |
| Lógica repetida                  | Reutilización modular de reglas            |

---

### 🧠 4. ¿Dónde se usa?

- Validaciones complejas
- Scoring, reglas fiscales, reglas legales
- Evaluaciones de elegibilidad
- Workflows y motores de decisión

---

## ✅ Lección 2: Arquitectura Moderna de Drools 10

### 📌 1. ¿Qué es el Modelo Canónico?

Es una forma de definir reglas usando Java puro:

```java
public class ClienteRules implements Model {
    public Collection<Rule> getRules() {
        return List.of(
            rule("Cliente mayor de edad")
                .build(
                    pattern(Cliente.class).expr("edad", c -> c.getEdad() >= 18),
                    on(Cliente.class).execute(c -> System.out.println("✅ " + c.getNombre()))
                )
        );
    }
}
```

---

### 🧱 2. Componentes Clave

| Componente       | Rol                                               |
|------------------|----------------------------------------------------|
| `Model`          | Clase que define tus reglas Java DSL              |
| `Rule`           | Representación de una regla                       |
| `Pattern`        | Condiciones sobre los hechos                      |
| `KieBase`        | Base de conocimiento                              |
| `KieSession`     | Sesión para insertar hechos y ejecutar reglas     |
| `RETE`           | Motor de evaluación de reglas                     |

---

### 🔄 3. Flujo de Ejecución

1. Definir reglas (Java DSL)
2. Compilar con `drools-model-compiler`
3. Crear `KieBase`
4. Iniciar `KieSession`
5. Insertar hechos
6. Ejecutar `fireAllRules()`

---

### 💡 4. Ventajas

- ✅ 100% Java (sin `.drl`)
- ✅ Compatible con Java 21
- ✅ Integración con Spring Boot 3
- ✅ Testeable y modular
- ✅ Mejor mantenimiento en microservicios

---

### 📌 5. Diagrama de Arquitectura

📌 El siguiente flujo representa la arquitectura moderna:

```
[ No usa archivos .drl ]
            |
         [ DROOLS ] <--- [ V.10 -> JAVA 21 ]
            |
[ JAVA DSL ] → [ COMPILER ] → [ KIE BASE ] → [ KIE SESSION ] → [ RULE ENGINE (RETE) ]
```

---
