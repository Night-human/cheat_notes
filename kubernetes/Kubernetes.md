# Kubernetes


---
Cluster: instance of kubernetes
cluster has:
  - Control plane: control creation, modification and deletion of nodes and pods
  - Worker node/s
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