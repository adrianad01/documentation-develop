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
| `docker build -t <nombreImagen> .`                                                                    | Construye una imagen usando el `Dockerfile` ubicado en el directorio actual.                                                                                        |
| `docker build -f <rutaDockerfile> -t <nombreImagen> .`                                                 | Construye una imagen especificando un `Dockerfile` en particular.                                                                                                   |
| `docker login -u <usuario> -p <contraseña> <servidor>`                                                 | Inicia sesión en un registro privado de Docker, por ejemplo Nexus.                                                                                                  |
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