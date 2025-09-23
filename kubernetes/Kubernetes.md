# Kubernetes

Kubernetes es una plataforma de orquestación de contenedores Open Source.

- Administra contenedores.
- Permite definir como deben comportarse las aplicaciones(Resplicas, recursos, comunicación).
- Matiene el estado deseado, reparando fallos.

## Proposito

1. Automatiozación del despliegue

  - Define aplicaciones en archivos yaml.
  - K8s crea los contenedores, redes, volumenes, etc.

2. Escalabilidad automatica

  - Escala horizontalmente(Más replicas).
  - Escala verticalmente(Más cpu/ram).

3. Alta disponibilidad

  - Si un nodo falla, k8s mueve los contenedores a otro nodo
  - Reintenta automaticamente los pods que fallan.

4. Gestion de configuracion y secretos 

  - Maneja variables de entorno, archivos de configuracion y credenciales de forma segura.

5. Balanceo de carga y descubrimiento de servicios

  - Asigna IPs internas y DNS a servicios.
  - Balanceo automatico entre replicas.

6. Actualizacion sin interrupciones

  - Permite hacer rolling updates y rolling backs facilmente.

## Componentes

### Componentes del control plane

- Kube-Apiserver: expone la api de k8s. Es el frontend de k8s, recibe las peticiones y actualiza acorde al estado etcd. Tambien, es una implementacion preparada para ejecutarse en alta disponibilidad y que puede escalar horizontalmente para balancear la carga entre varias instancias.

- etcd: Almacen de datos persistente, consistente y distribuido de clave-valor utilizado para guardar toda la informacion del cluster.

- Kube-Scheduler: Componente que esta pendiente de los pods que no han sido asignados a algun nodo, selecciona uno donde ejecutarlo. Para decidir, toma en cuenta requisitos de recursos, restricciones de hardware, software, politicas, afinidad, anti afinidad, entre otros.

Kube-controller manager: Ejecuta los contoladores de k8s.

---
Cluster: instance of kubernetes
cluster has:
  - Control plane: control creation, modification and deletion of nodes and pods
  - Worker node/s
    - Worker nodes contains pods which contains containers or replicas
---

## Install kubernetes

1. Run in command line
   
   `
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    sudo install minikube-linux-amd64 /usr/local/bin/minikube
    `

# Minikube Commands

- Start a cluster
   
   `minikube start`

- Install kubectl from minikube
   
   `minikube kubectl -- get po -A`

- Set an alias

  `alias kubectl="minikube kubectl --"`

- Create tunnel for Service yaml
  `minikube tunnel`
  - Run service yaml after 

### service commands

- Start a cluster
  
  `minikube start`

- Status a cluster
  
  `minikube status`

- Stop a cluster
  
  `minikube stop`

- Delete a cluster
  
  `minikube delete`

- Open the Dashboard
  
  `minikube dashboard`

# Kubectl Commands

### Info commands

- Pods info
  
  `kubectl get pods -A -o wide`
  - Delete a pod

    `kubectl delete pod <podname> -n <namespace>`

- Nodes info
  
  `kubectl get nodes`

- Namespaces info
  
  `kubectl get namespaces`

- Services info
  
  `kubectl get services -A`

- Cluster info
  
  `kubectl cluster-info`

- deployments info
  
  `kubectl get deployments -A`

  - Delete deployments

    `kubectl delete deployments -n <namespace> --all`

### Namespaces commands

- Create namespaces
  
  `kubectl apply -f namespaces.yaml`

- Delete namespaces
  
  `kubeclt delete -f namespaces.yaml`

### Deploy images

- Create deployments
  
  `kubectl apply -f namespaces.yaml`

- Delete deployments
  
  `kubeclt delete -f namespaces.yaml` 
  
  or

  `kubectl delete deployments -n <namespace> --all`

## Logs

  `kubectl describe pod <podname> -n <namespace>`

- Is the pod up?

`kubectl logs <podname> -n <namespace>`


# Notes yaml kinds

Deployment: Deploy apps

Namespace: Create namespaces

Service: expose the pod to the internet(use deployment label app to define which apps would be exposed)

- It has three types of Service:
  - LoadBalancer(exposes app to the internet)
  - NodePort
  - ClusterIp 
