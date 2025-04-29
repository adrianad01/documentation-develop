# 📦 Introducción a Maven (Java 21)

## ¿Qué es Maven?
**Maven** es una herramienta de gestión de proyectos para Java que nos ayuda a:
- **Compilar** código
- **Construir** paquetes (como archivos `.jar` o `.war`)
- **Gestionar dependencias** de librerías externas
- **Automatizar** procesos de construcción

> Maven hace que tu proyecto sea **repetible** y **consistente**, sin que tengas que configurar todo a mano.

---

## 🯫 Estructura Básica de un Proyecto Maven

Cuando creas un proyecto Maven, sigue una estructura estándar:

```
mi-proyecto/
│
├── src/
│   ├── main/
│   │   ├── java/       (Código fuente)
│   │   └── resources/  (Archivos de configuración, plantillas, etc.)
│   └── test/
│       ├── java/       (Pruebas unitarias)
│       └── resources/  (Datos para las pruebas)
│
├── target/             (Carpeta generada, aquí se crean los .class y el .jar)
├── pom.xml             (Archivo principal de configuración)
```

---

## 📟 ¿Qué es el `pom.xml`?

**`pom.xml`** significa **Project Object Model**.

Este archivo define:
- **Dependencias** (qué librerías usarás)
- **Plugins** (qué tareas automatizadas quieres)
- **Datos del proyecto** (nombre, versión, descripción)
- **Configuraciones adicionales** (por ejemplo, compatibilidad con Java 21)

**Ejemplo sencillo de un `pom.xml`:**

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.ejemplo</groupId>
    <artifactId>mi-aplicacion</artifactId>
    <version>1.0.0</version>

    <properties>
        <maven.compiler.source>21</maven.compiler.source>
        <maven.compiler.target>21</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Ejemplo: agregar Spring Boot Starter Web -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
            <version>3.2.5</version>
        </dependency>
    </dependencies>

</project>
```

---

## 📜 Comandos Básicos de Maven

| Comando                         | ¿Qué hace?                                                |
|----------------------------------|-----------------------------------------------------------|
| `mvn clean`                     | Borra la carpeta `target` para limpiar el proyecto        |
| `mvn compile`                   | Compila el código fuente                                  |
| `mvn package`                   | Empaqueta el proyecto (por ejemplo, crea un `.jar`)       |
| `mvn install`                   | Instala el paquete en tu repositorio local                |
| `mvn test`                      | Ejecuta las pruebas unitarias                             |
| `mvn spring-boot:run`            | (Si es Spring Boot) Levanta la aplicación                 |

---

## 🛠 Cómo instalar Maven

1. Descarga Maven desde [la página oficial](https://maven.apache.org/download.cgi).
2. Descomprime el archivo en tu máquina.
3. Configura las variables de entorno:
   - **MAVEN_HOME** apuntando a la carpeta de Maven
   - **Path** agregando `MAVEN_HOME/bin`
4. Verifica que funcione:
```bash
mvn -v
```
Te debe salir algo como:

```
Apache Maven 3.9.6
Java version: 21
```

---

## ⚙️ ¿Cómo hacer que Maven use Java 21?

Asegúrate de que en el `pom.xml` tengas:

```xml
<properties>
    <maven.compiler.source>21</maven.compiler.source>
    <maven.compiler.target>21</maven.compiler.target>
</properties>
```

Además, asegúrate que tu computadora tenga configurado **JAVA_HOME** apuntando a JDK 21.

---

## 🎯 Ejemplo completo paso a paso

1. **Crear proyecto vacío**:
   ```bash
   mvn archetype:generate -DgroupId=com.ejemplo -DartifactId=mi-aplicacion -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
   ```

2. **Entrar al proyecto**:
   ```bash
   cd mi-aplicacion
   ```

3. **Empaquetar**:
   ```bash
   mvn package
   ```

4. **Correrlo** (si es app tipo consola):
   ```bash
   java -cp target/mi-aplicacion-1.0.0.jar com.ejemplo.App
   ```

---

# 📋 Resumen rápido

- Maven organiza, compila y empaqueta proyectos Java automáticamente.
- Define todo en un archivo `pom.xml`.
- Usa una estructura estándar.
- Se integra perfectamente con Java 21.
- Automatiza dependencias, pruebas, empaquetado y despliegue.

