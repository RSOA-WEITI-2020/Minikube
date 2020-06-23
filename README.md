# Minikube
Kubernetes deployments and commands to do them

# Manual Commands

1. minikube start

create auth service deployment

2. kubectl create deployment authservice --image=rpwtouk/rosaauth:v0.0.7

expose auth service

3. kubectl expose deployment authservice --type=LoadBalancer --port=9090

# Commands using .yml objects

basically everything is done using kubectl apply -f <object name>

https://kubernetes.io/docs/concepts/workloads/controllers/deployment/

# Debug
1.1 kubectl get pods 

2.1 kubectl get deployments  
2.2 kubectl describe pod <ID>   
  
3.1 kubectl get services
3.2 minikube service authservice
