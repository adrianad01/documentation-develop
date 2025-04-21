# KUBERNETES (K8S)

## Comandos

| Comando                                                                       | Descripcion                                                                                           |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
|`minikube start`                                                               | Inicializar cluster minikube                                                                          |
|`minikube delete`                                                              | Eliminar el cluster                                                                                   |
|`minikube dashboard`                                                           | Abrir el dashboard del cluster                                                                        |
|`kubectl get pods`                                                             | Visualizar los pods activos                                                                           |
|`kubectl get nodes`                                                            | Visualizar los nodos activos                                                                          |
|`kubectl run <nombre del pod> --image <imagen docker>`                         | Crear un pod pasandole una imagen de docker                                                           |
|`kubectl describe pod <nombre del pod>`                                        | Ver descripcion detallada de un pod por su nombre                                                     |
|`kubectl exec -it <nombre del pod> -- /bin/bash`                               | Ejecutar comando dentro de un pod por medio de bin bash                                               |
|`kubectl exec pod/<nombre del pod> -- ls`                                      | Listar el contenido que tiene el pod                                                                  |
|`kubectl logs <nombreDelPod>`                                                  | Listado de los logs que tiene el pod                                                                  |
|`kubectl delete pod <nombrePod>`                                               | Eliminar un pod por su nombre                                                                         |
|`kubectl apply -f <nombreDelArchivoYamlGenerado.yml>`                          | Crear un pod con base a la estructura del archivo yaml                                                |
|`kubectl get pods -o wide`                                                     | Ver mas a detalle los pods creados                                                                    |
|`kubectl get pods --selector <etiquetaNombre>=<nombre>`                        | Busca un pod por medio del nombre del laben definido                                                  |
|`kubectl get pod --show-labels`                                                | Muestra todos los labels de los pods creados                                                          |
|`kubectl label pod <nombrePod> <etiquetalabel=nombreLabel>`                    | Crearle un label a un pod por medio de CLI                                                            |
|`kubectl label --overwrite pod <nombre pod> <etiquetalabel=nuevoNombre>`       | Cambiar el valor de la etiqueta de un pod                                                             |
|`kubectl label pod <nombrePod> <nombreEtiqueta>-`                              | Eliminar el label de un pod                                                                           |
|`kubectl get pods -l <etiquetaNombre>=<nombre>`                                | Busca un pod por medio del nombre del laben definido (con esta forma se abrevia el --selector con -l) |
|`kubectl get pods -l '<etiqueta> in (valorEtiqueta1, valorEtiqueta.....)'`     | trae los pods que estan dentro de esa etiqueta y en ese grupo de valore                               |
|`kubectl get pods -l '<etiqueta> notin (valorEtiqueta1, valorEtiqueta.....)'`  | trae los pods que no estan dentro de esa etiqueta ni en ese grupo de valores                          |
|`kubectl get pods --selector <key1>=<value1> <keyN>=<valueN>`                  | Lista todos los pods por medio de un selector y pasar n veces una propiedad (label)|
|`kubectl delete pods --selector app=backend `                                  | Elimina un pod por medio de un selector |
|`kubectl get pods <nombre-pod> -o jsonpath='{.metadata.annotations}'`          | Lista todas las anotaciones de un pod en un formato json|
|`kubectl annotate pod <nombre-pod> <propiedad>=<"valor">`                      | Crear una nueva anotacion por linea de comandos|
|`kubectl annotate pod <nombre-pod> <propiedad>=<"valor"> --overwrite`          | Modificar una anotacion existente por linea de comandos|
|`kubectl annotate pod <nombre-pod> <propiedad>-`                               | Eliminar una anotacion por su propiedad y el signo `-` posterior al nombre|



## Abreviatutas
| --port | pasar puertos por comando |
| ------ | ------------------------- |
|        |                           |


## Estructura YAML
apiVersion: v1
kind: Pod
metadata:
  name: myapp
  annotations: 
    annotation1: "value"
    annotation2: "value"
    annotationN: "value"
  labels:
    name: myapp
spec:
  containers:
  - name: myapp
    image: <Image>
    resources:
      limits:
        memory: "128Mi"
        cpu: "500m"
    ports:
      - containerPort: 9090

