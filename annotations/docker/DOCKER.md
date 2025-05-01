# :ballena: Docker - Comandos Básicos
## :paquete: Repositorio de Imágenes
- **Docker Hub** → [https://hub.docker.com](https://hub.docker.com)
---
## :portapapeles: Comandos útiles de Docker
| Comando                                                                                               | Descripción                                                                                                                                                         |
| ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `docker images`                                                                                       | Lista todas las imágenes locales disponibles en Docker.                                                                                                            |
| `docker run <imagen>`                                                                                 | Crea y ejecuta un contenedor basado en la imagen especificada.                                                                                                      |
| `docker ps`                                                                                           | Muestra los contenedores que están en ejecución.                                                                                                                    |
| `docker ps -a`                                                                                        | Muestra todos los contenedores, estén activos o no.                                                                                                                 |
| `docker search <imagen>`                                                                              | Busca imágenes en Docker Hub relacionadas con el término ingresado.                                                                                                |
| `docker pull <imagen>`                                                                                | Descarga una imagen desde Docker Hub o desde un repositorio configurado.                                                                                            |
| `docker rm <containerId>`                                                                             | Elimina un contenedor por su ID.                                                                                                                                    |
| `docker rmi <imagen>`                                                                                 | Elimina una imagen de Docker (requiere que no haya contenedores usando la imagen).                                                                                   |
| `docker rename <nombreAnterior> <nuevoNombre>`                                                        | Cambia el nombre de un contenedor.                                                                                                                                  |
| `docker inspect <nombreContenedor>`                                                                   | Muestra información detallada sobre un contenedor.                                                                                                                  |
| `docker container prune`                                                                              | Elimina **todos** los contenedores detenidos.                                                                                                                       |
| `docker run -it <imagen>`                                                                             | Ejecuta un contenedor en modo interactivo y abre la terminal dentro de él.                                                                                           |
| `docker run --name <nuevoNombreImagen> -d <nombreImagen> tail -f /dev/null`                            | Ejecuta un contenedor en segundo plano que se mantiene activo.                                                                                                       |
| `docker run -it --rm -d -p <puertoHost>:<puertoContenedor> --name <nombreContenedor> <imagen>:<tag>`   | Ejecuta un contenedor con puerto mapeado, en modo interactivo, en segundo plano y se elimina al detenerse.                                                          |
| `docker stop <nombreContenedor>`                                                                      | Detiene un contenedor en ejecución.                                                                                                                                 |
| `docker build -t <nombreImagenPorAsignar> .`                                                                    | Construye una imagen usando el `Dockerfile` ubicado en el directorio actual.                                                                                        |
| `docker build -f <rutaDockerfile> -t <nombreImagen> .`                                                 | Construye una imagen especificando un `Dockerfile` en particular.                                                                                                   |
| `docker login -u <usuario> -p <contraseña> <servidor>`                                                 | Inicia sesión en un registro privado de Docker, por ejemplo Nexus.                                                                                                  |
| `docker log -f <nombreContenedor>`                                                 | Visualiza logs en tiempo real del contenedor.                                                                                                  |
| `docker stats -f <nombreContenedor>`                                                 | Visualiza las estadisticas del contenedor en tiempo real.                                                                                                  |
---

## 🚀 Comandos para Contenedores Existentes

### ▶️ Iniciar un contenedor detenido

```bash
docker start <nombreContenedor>
```

Este comando **reinicia** un contenedor previamente detenido, sin crear uno nuevo.

### 🔄 Reiniciar un contenedor

```bash
docker restart <nombreContenedor>
```

Reinicia el contenedor (lo detiene y lo vuelve a arrancar).

### 💬 Acceder a un contenedor en ejecución

```bash
docker exec -it <nombreContenedor> bash
```

Abre una terminal dentro del contenedor en ejecución. Si no tiene `bash`, puedes probar con `sh`.

### 🛑 Detener un contenedor

```bash
docker stop <nombreContenedor>
```

Detiene de forma ordenada el contenedor especificado.

## :martillo_y_llave_inglesa: Flags comunes
| Flag         | Descripción                                 |
| ------------ | ------------------------------------------- |
| `-a`         | Muestra todos los elementos.                 |
| `-d`         | Ejecuta en segundo plano (detached mode).    |
| `-p`         | Mapea puertos `<Host>:<Contenedor>`.         |
| `--rm`       | Elimina el contenedor al detenerlo.          |
| `--name`     | Asigna un nombre personalizado al contenedor.|
| `-t`         | Especifica un **tag** para la imagen.         |
| `-f` o `--file` | Especifica un archivo Dockerfile diferente.|
---

## 🐳 Estructura de un Dockerfile

### 1. Imagen base
FROM openjdk:21-jdk-slim

### 2. Información del autor (opcional)
LABEL maintainer="tucorreo@example.com"

### 3. Variables de entorno (opcional)
ENV APP_HOME=/app

### 4. Crear directorio de trabajo
WORKDIR $APP_HOME

### 5. Copiar archivos al contenedor
COPY target/mi-app.jar app.jar

### 6. Exponer puertos (opcional, informativo)
EXPOSE 8080

### 7. Comando por defecto al iniciar el contenedor
ENTRYPOINT ["java", "-jar", "app.jar"]

| Instrucción | Descripción |
|------------|-------------|
| `FROM`     | Define la imagen base del contenedor (por ejemplo, un JDK si es una app Java) |
| `LABEL`    | Añade metadatos, como el autor del Dockerfile |
| `ENV`      | Establece variables de entorno |
| `WORKDIR`  | Define el directorio de trabajo dentro del contenedor |
| `COPY`     | Copia archivos desde tu máquina (build context) al contenedor |
| `RUN`      | Ejecuta comandos al construir la imagen (instalar dependencias, etc.) |
| `EXPOSE`   | Informa qué puerto usará la aplicación (no abre el puerto por sí mismo) |
| `ENTRYPOINT` o `CMD` | Define el comando principal que se ejecutará al iniciar el contenedor |


## 🧭 Redes en Docker

Docker permite que los contenedores se comuniquen entre sí y con el exterior usando diferentes tipos de redes.

### 🔌 Tipos de Redes

| Tipo de red | Descripción |
|-------------|-------------|
| `bridge`    | Red por defecto. Conecta contenedores en el mismo host. |
| `host`      | El contenedor usa directamente la red del host. Sin aislamiento. |
| `none`      | El contenedor no tiene acceso a la red. Máximo aislamiento. |
| `overlay`   | Red entre múltiples hosts. Requiere Docker Swarm. |
| `macvlan`   | El contenedor aparece como un dispositivo en la red física. |

---

## 🛠️ Comandos útiles

### 📄 Crear y listar redes

```bash
# Ver redes existentes
docker network ls

# Crear una red personalizada tipo bridge
docker network create --driver bridge mi_red
```

### 🧩 Conectar contenedores a redes

```bash
# Ejecutar un contenedor conectado a una red
docker run -d --name mi_app --network mi_red mi_imagen

# Conectar un contenedor ya existente a una red
docker network connect mi_red otro_contenedor

# Desconectar un contenedor de una red
docker network disconnect mi_red mi_app
```

### 🧽 Eliminar redes

```bash
docker network rm mi_red
```

### 🔍 Inspeccionar una red

```bash
docker network inspect mi_red
```

Muestra detalles como IPs, subred, gateway y contenedores conectados.

---

# 🗃️ Volúmenes y Bind Mounts en Docker

Docker ofrece dos formas principales de persistir datos en contenedores:

### 🔸 Volúmenes (`docker volume`)

Los volúmenes son gestionados por Docker y se almacenan fuera del sistema de archivos del contenedor.

#### 📦 Crear y usar un volumen

```bash
# Crear un volumen
docker volume create mi_volumen

# Ver volúmenes existentes
docker volume ls

# Usar volumen al correr un contenedor
docker run -d --name app --mount source=mi_volumen,target=/data nginx
```

#### 📜 Montaje de volumen usando `-v` (forma abreviada)

```bash
docker run -d --name app -v mi_volumen:/data nginx
```

- `mi_volumen` → nombre del volumen
- `/data` → carpeta dentro del contenedor

#### 🧼 Eliminar volúmenes

```bash
# Eliminar volumen individual
docker volume rm mi_volumen

# Eliminar volúmenes no usados por ningún contenedor
docker volume prune
```

---

### 🔸 Bind Mounts

Los Bind Mounts enlazan una carpeta del **host (tu PC)** con una carpeta del contenedor.

#### 📁 Montar una carpeta local al contenedor

```bash
docker run -d --name dev-app -v $(pwd)/html:/usr/share/nginx/html nginx
```

- `$(pwd)/html` → carpeta local
- `/usr/share/nginx/html` → ruta en el contenedor

Esto es útil para desarrollo: lo que cambias localmente se refleja dentro del contenedor.

---

### 📋 Diferencias clave

| Característica      | Volúmenes              | Bind Mounts                  |
|---------------------|------------------------|------------------------------|
| Gestionado por Docker | ✅ Sí                 | ❌ No                         |
| Portabilidad        | ✅ Alta                | ❌ Depende del path local     |
| Ideal para...       | Producción, persistencia | Desarrollo local             |
| Seguridad           | ✅ Mejor aislado        | ⚠️ Más expuesto al sistema    |



📝 _Recomendación_: Usa **volúmenes** para producción y **bind mounts** durante desarrollo.

--- 
# 🧩 Docker Compose - Estructura y Guía Básica

Docker Compose te permite definir y correr múltiples contenedores Docker con una sola configuración en YAML.

---

## 📄 Estructura Básica de un archivo `docker-compose.yml`

```yaml
version: '3.8'  # Versión del esquema de Compose

services:
  nombre_servicio:
    image: nombre_imagen:tag
    container_name: nombre_contenedor
    ports:
      - "puerto_host:puerto_contenedor"
    environment:
      - VARIABLE=valor
    volumes:
      - volumen_local:/ruta_en_contenedor
    networks:
      - mi_red
    depends_on:
      - otro_servicio

volumes:
  volumen_local:

networks:
  mi_red:
```

---

## 🧪 Ejemplo práctico: App Node + Base de datos

```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "3000:3000"
    depends_on:
      - db
    networks:
      - red_app

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: secret
      POSTGRES_DB: midb
    volumes:
      - db_data:/var/lib/postgresql/data
    networks:
      - red_app

volumes:
  db_data:

networks:
  red_app:
```

---

## 📌 Comandos útiles

```bash
# Levantar los servicios definidos
docker-compose up

# Levantar en segundo plano
docker-compose up -d

# Detener los servicios
docker-compose down

# Ver logs
docker-compose logs -f

# Ver estado de los servicios
docker-compose ps

# Reconstruir imágenes (si cambió el Dockerfile)
docker-compose build
```

---

📎 _Guarda este archivo como `docker-compose.yml` en el mismo directorio donde están tus archivos de proyecto._

📝 _Ideal para apps con múltiples contenedores: backend + base de datos, microservicios, etc._
---

## 🛠️ Comandos Completos de Docker Compose

| Comando                                      | Descripción                                                                 |
|---------------------------------------------|-----------------------------------------------------------------------------|
| `docker-compose up`                         | Crea y levanta todos los servicios definidos en el `docker-compose.yml`.   |
| `docker-compose up -d`                      | Lo mismo, pero en segundo plano (detached mode).                           |
| `docker-compose down`                       | Detiene y elimina todos los contenedores, redes y volúmenes anónimos.     |
| `docker-compose stop`                       | Detiene los servicios sin eliminarlos.                                     |
| `docker-compose start`                      | Reinicia servicios detenidos sin recrearlos.                               |
| `docker-compose restart`                    | Reinicia los servicios (detiene y arranca).                                |
| `docker-compose build`                      | Construye las imágenes especificadas en los servicios.                     |
| `docker-compose build --no-cache`           | Fuerza la reconstrucción sin usar cache.                                   |
| `docker-compose pull`                       | Descarga las imágenes desde un registro remoto (ej. Docker Hub).           |
| `docker-compose push`                       | Sube las imágenes al registro (si se configuró correctamente).             |
| `docker-compose logs`                       | Muestra los logs de todos los servicios.                                   |
| `docker-compose logs -f`                    | Logs en tiempo real (modo "follow").                                       |
| `docker-compose ps`                         | Lista el estado actual de los contenedores.                                |
| `docker-compose exec <servicio> bash`       | Accede al contenedor de un servicio con shell interactivo.                |
| `docker-compose run <servicio> <comando>`   | Ejecuta un comando puntual en un servicio (similar a `docker run`).        |
| `docker-compose config`                     | Valida y muestra el archivo de configuración final usado.                  |
| `docker-compose rm`                         | Elimina contenedores detenidos de los servicios.                           |
| `docker-compose kill`                       | Finaliza los contenedores inmediatamente.                                  |
| `docker-compose top`                        | Muestra los procesos en ejecución dentro de los contenedores.              |
| `docker-compose version`                    | Muestra la versión instalada de Docker Compose.                            |

---

📝 _Usa `docker-compose <comando> --help` para más detalles sobre cada comando._
---

## 🧹 Limpieza Total con `docker-compose down -v`

```bash
docker-compose down -v
```

### 🔥 ¿Qué elimina?

- Todos los contenedores definidos en el `docker-compose.yml`
- Las redes creadas automáticamente por Docker Compose
- Los **volúmenes** (anónimos o nombrados) declarados en el archivo

Ideal para **reiniciar por completo** tu entorno de desarrollo.

---

### ✅ Limpieza con eliminaci# :ballena: Docker - Comandos Básicos
## :paquete: Repositorio de Imágenes
- **Docker Hub** → [https://hub.docker.com](https://hub.docker.com)

---

## 🚀 Comandos para Contenedores Existentes

### ▶️ Iniciar un contenedor detenido

```bash
docker start <nombreContenedor>
```

Este comando **reinicia** un contenedor previamente detenido, sin crear uno nuevo.

### 🔄 Reiniciar un contenedor

```bash
docker restart <nombreContenedor>
```

Reinicia el contenedor (lo detiene y lo vuelve a arrancar).

### 💬 Acceder a un contenedor en ejecución

```bash
docker exec -it <nombreContenedor> bash
```

Abre una terminal dentro del contenedor en ejecución. Si no tiene `bash`, puedes probar con `sh`.

### 🛑 Detener un contenedor

```bash
docker stop <nombreContenedor>
```

Detiene de forma ordenada el contenedor especificado.

---

## :martillo_y_llave_inglesa: Flags comunes
| Flag         | Descripción                                 |
| ------------ | ------------------------------------------- |
| `-a`         | Muestra todos los elementos.                 |
| `-d`         | Ejecuta en segundo plano (detached mode).    |
| `-p`         | Mapea puertos `<Host>:<Contenedor>`.         |
| `--rm`       | Elimina el contenedor al detenerlo.          |
| `--name`     | Asigna un nombre personalizado al contenedor.|
| `-t`         | Especifica un **tag** para la imagen.         |
| `-f` o `--file` | Especifica un archivo Dockerfile diferente.|

---

## 🐳 Estructura de un Dockerfile

# 1. Imagen base
FROM openjdk:21-jdk-slim

# 2. Información del autor (opcional)
LABEL maintainer="tucorreo@example.com"

# 3. Variables de entorno (opcional)
ENV APP_HOME=/app

# 4. Crear directorio de trabajo
WORKDIR $APP_HOME

# 5. Copiar archivos al contenedor
COPY target/mi-app.jar app.jar

# 6. Exponer puertos (opcional, informativo)
EXPOSE 8080

# 7. Comando por defecto al iniciar el contenedor
ENTRYPOINT ["java", "-jar", "app.jar"]

| Instrucción | Descripción |
|------------|-------------|
| `FROM`     | Define la imagen base del contenedor (por ejemplo, un JDK si es una app Java) |
| `LABEL`    | Añade metadatos, como el autor del Dockerfile |
| `ENV`      | Establece variables de entorno |
| `WORKDIR`  | Define el directorio de trabajo dentro del contenedor |
| `COPY`     | Copia archivos desde tu máquina (build context) al contenedor |
| `RUN`      | Ejecuta comandos al construir la imagen (instalar dependencias, etc.) |
| `EXPOSE`   | Informa qué puerto usará la aplicación (no abre el puerto por sí mismo) |
| `ENTRYPOINT` o `CMD` | Define el comando principal que se ejecutará al iniciar el contenedor |


## 🧭 Redes en Docker

Docker permite que los contenedores se comuniquen entre sí y con el exterior usando diferentes tipos de redes.

### 🔌 Tipos de Redes

| Tipo de red | Descripción |
|-------------|-------------|
| `bridge`    | Red por defecto. Conecta contenedores en el mismo host. |
| `host`      | El contenedor usa directamente la red del host. Sin aislamiento. |
| `none`      | El contenedor no tiene acceso a la red. Máximo aislamiento. |
| `overlay`   | Red entre múltiples hosts. Requiere Docker Swarm. |
| `macvlan`   | El contenedor aparece como un dispositivo en la red física. |

---

## 🐳 Estructura de un Dockerfile

# 1. Imagen base
FROM openjdk:21-jdk-slim

# 2. Información del autor (opcional)
LABEL maintainer="tucorreo@example.com"

# 3. Variables de entorno (opcional)
ENV APP_HOME=/app

# 4. Crear directorio de trabajo
WORKDIR $APP_HOME

# 5. Copiar archivos al contenedor
COPY target/mi-app.jar app.jar

# 6. Exponer puertos (opcional, informativo)
EXPOSE 8080

# 7. Comando por defecto al iniciar el contenedor
ENTRYPOINT ["java", "-jar", "app.jar"]

| Instrucción | Descripción |
|------------|-------------|
| `FROM`     | Define la imagen base del contenedor (por ejemplo, un JDK si es una app Java) |
| `LABEL`    | Añade metadatos, como el autor del Dockerfile |
| `ENV`      | Establece variables de entorno |
| `WORKDIR`  | Define el directorio de trabajo dentro del contenedor |
| `COPY`     | Copia archivos desde tu máquina (build context) al contenedor |
| `RUN`      | Ejecuta comandos al construir la imagen (instalar dependencias, etc.) |
| `EXPOSE`   | Informa qué puerto usará la aplicación (no abre el puerto por sí mismo) |
| `ENTRYPOINT` o `CMD` | Define el comando principal que se ejecutará al iniciar el contenedor |


## 🧭 Redes en Docker

Docker permite que los contenedores se comuniquen entre sí y con el exterior usando diferentes tipos de redes.

### 🔌 Tipos de Redes

| Tipo de red | Descripción |
|-------------|-------------|
| `bridge`    | Red por defecto. Conecta contenedores en el mismo host. |
| `host`      | El contenedor usa directamente la red del host. Sin aislamiento. |
| `none`      | El contenedor no tiene acceso a la red. Máximo aislamiento. |
| `overlay`   | Red entre múltiples hosts. Requiere Docker Swarm. |
| `macvlan`   | El contenedor aparece como un dispositivo en la red física. |ón de imágenes también

```bash
docker-compose down --rmi all -v
```

- `--rmi all` → Elimina todas las imágenes relacionadas con los servicios
- `-v` → Elimina todos los volúmenes usados por los servicios

---

📌 Útil para cuando necesitas limpiar todo sin dejar residuos antes de un nuevo despliegue.

--- 

# 🏗️ Docker Multi-Stage Builds

Multi-stage builds permiten crear imágenes **más pequeñas y optimizadas**, separando el proceso de **construcción** del de **ejecución**.



## 🎯 ¿Por qué usar multi-stage?

- Reducción drástica del tamaño de imagen final
- Mejora de seguridad: la imagen final no contiene herramientas de build (ej. Maven, Node, etc.)
- Código más limpio y mantenible

---

## 🧱 Estructura General

```dockerfile
# Etapa 1: Build
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Etapa 2: Imagen final
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
```

---

## 🧪 Ejemplo completo: Java con Maven

```dockerfile
# Etapa 1: Compilación con Maven
FROM maven:3.9-eclipse-temurin-21 AS builder
WORKDIR /build
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Etapa 2: Imagen final con JDK ligero
FROM eclipse-temurin:21-jdk-alpine
WORKDIR /app
COPY --from=builder /build/target/miapp.jar app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]
```

✅ Resultado:
- La imagen final **no contiene Maven ni el código fuente**
- Solo incluye el `.jar` listo para ejecutarse

---

## 🔍 Buenas prácticas

- Nombrar etapas: `AS builder`, `AS base`, etc.
- Usar `COPY --from=<etapa>` para traer solo lo necesario
- Evitar copiar directorios completos (usa `.dockerignore`)
- Verificar el tamaño final con `docker image ls`

---

## 🧰 Comandos útiles

```bash
# Construir imagen multi-stage
docker build -t miapp:prod .

# Ver capas utilizadas
docker history miapp:prod
```

---

📦 _Multi-stage builds son esenciales en pipelines CI/CD y despliegue de microservicios._