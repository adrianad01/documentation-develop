# 🧠 Kubernetes (K8s) - Comandos Esenciales y Estructuras

## 🚀 Comandos Básicos de Minikube

| Comando                     | Descripción                                 |
|----------------------------|---------------------------------------------|
| `minikube start`           | Inicializa un clúster local de Minikube     |
| `minikube delete`          | Elimina el clúster de Minikube              |
| `minikube dashboard`       | Abre el dashboard gráfico del clúster       |

---

## 🔧 Gestión de Pods

| Comando                                                         | Descripción                                                                 |
|------------------------------------------------------------------|-----------------------------------------------------------------------------|
| `kubectl get pods`                                              | Lista todos los pods activos                                               |
| `kubectl get pods -o wide`                                      | Muestra los pods con información extendida                                 |
| `kubectl get pod --show-labels`                                 | Muestra todos los labels de los pods                                       |
| `kubectl describe pod <nombre-pod>`                             | Muestra los detalles completos de un pod específico                        |
| `kubectl delete pod <nombre-pod>`                               | Elimina un pod por su nombre                                               |
| `kubectl logs <nombre-pod>`                                     | Muestra los logs del pod                                                   |
| `kubectl exec -it <nombre-pod> -- /bin/bash`                    | Abre una terminal bash dentro del pod                                      |
| `kubectl exec pod/<nombre-pod> -- ls`                           | Lista archivos/directorios dentro del pod                                  |

---

## 🛠️ Crear Pods

| Comando                                                              | Descripción                                                                 |
|----------------------------------------------------------------------|-----------------------------------------------------------------------------|
| `kubectl run <nombre> --image <imagen-docker>`                       | Crea un pod a partir de una imagen Docker                                   |
| `kubectl apply -f <archivo.yaml>`                                    | Crea/actualiza recursos con base en un archivo YAML                         |

---

## 🔍 Filtrar Pods por Labels

| Comando                                                                                   | Descripción                                                                                     |
|--------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| `kubectl get pods --selector <etiqueta>=<valor>`                                           | Filtra pods usando un selector (forma larga)                                                    |
| `kubectl get pods -l <etiqueta>=<valor>`                                                   | Filtra pods usando un selector (forma corta)                                                    |
| `kubectl get pods -l '<etiqueta> in (valor1, valor2)'`                                     | Muestra pods cuyo label esté dentro de una lista de valores                                     |
| `kubectl get pods -l '<etiqueta> notin (valor1, valor2)'`                                  | Muestra pods cuyo label **no** esté dentro de una lista de valores                              |
| `kubectl get pods --selector <key1>=<value1> <keyN>=<valueN>`                              | Aplica múltiples filtros por label                                                              |
| `kubectl delete pods --selector <label>=<valor>`                                           | Elimina pods con base en un selector                                                            |

---

## 🏷️ Labels en Pods

| Comando                                                                 | Descripción                                                      |
|--------------------------------------------------------------------------|------------------------------------------------------------------|
| `kubectl label pod <nombre> <etiqueta>=<valor>`                          | Asigna una etiqueta al pod                                       |
| `kubectl label --overwrite pod <nombre> <etiqueta>=<nuevoValor>`        | Modifica una etiqueta existente                                  |
| `kubectl label pod <nombre> <etiqueta>-`                                 | Elimina una etiqueta del pod                                     |

---

## 📝 Anotaciones (Annotations) en Pods

| Comando                                                                 | Descripción                                                      |
|--------------------------------------------------------------------------|------------------------------------------------------------------|
| `kubectl get pods <nombre> -o jsonpath='{.metadata.annotations}'`       | Lista todas las anotaciones de un pod                           |
| `kubectl annotate pod <nombre> <clave>=<"valor">`                       | Crea una anotación en el pod                                    |
| `kubectl annotate pod <nombre> <clave>=<"valor"> --overwrite`          | Modifica una anotación existente                                |
| `kubectl annotate pod <nombre> <clave>-`                                | Elimina una anotación                                            |

---

## 🔁 Abreviaturas Útiles

| Opción     | Descripción                    |
|------------|--------------------------------|
| `--port`   | Permite mapear puertos         |

---

## 📄 Ejemplo de Estructura YAML (Pod)

```yaml
apiVersion: v1              # Versión de la API de Kubernetes que se usará
kind: Pod                   # Tipo de recurso: Pod

metadata:                   # Metadatos del pod
  name: myapp               # Nombre del pod
  annotations:              # Anotaciones informativas
    annotation1: "value"
    annotation2: "value"
    annotationN: "value"
  labels:                   # Etiquetas para selección y filtrado
    name: myapp

spec:                       # Especificaciones del pod
  containers:
    - name: myapp           # Nombre del contenedor dentro del pod
      image: <Image>        # Imagen Docker (ej. nginx:latest)

      resources:            # Recursos asignados
        limits:
          memory: "128Mi"   # Memoria máxima: 128 MB
          cpu: "500m"       # CPU máximo: 0.5 cores

      ports:
        - containerPort: 9090  # Puerto expuesto dentro del contenedor
