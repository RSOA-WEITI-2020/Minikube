# Minikube
Kubernetes deployments and commands to do them

# HOW TO SETUP
1. minikube start --driver=docker
2. minikube addons enable ingress
3. kubectl apply -f .
4. wait some time if ingress fails:  
kubectl get pods --all-namespaces
5. if the above nginx ingress controller is in state Running proceed with:  
kubectl apply -f ingress.yml
6. setup rabbitmq  
kubectl create -f https://raw.githubusercontent.com/kubernetes/kubernetes/release-1.3/examples/celery-rabbitmq/rabbitmq-service.yaml  
kubectl create -f https://raw.githubusercontent.com/kubernetes/kubernetes/release-1.3/examples/celery-rabbitmq/rabbitmq-controller.yaml  


# TEST IF WORKS AFTER EVERYTHING STARTS


# HELPFUL COMMANDS FOR DEBUG
0. kubectl get all
1. enter pod:   
kubectl exec --stdin --tty pod/authservice-deployment-7f5466c9c5-f4msl -- /bin/bash  
on pod you can install mariadb with apt-get and then connect to mysql db master:  
mysql -h mysql-0.mysql  
  
MASTERHOST='mysql-0.mysql', \  
MASTERUSER='root', \  
MASTERPASSWORD='', \  

2. kubectl get ingress (if it doesnt have address attached wait till it gets one, it takes too long you did something wrong):  
curl http://ingress-address/v1/login and check if it matches correctly to authservice 


# DELETING EVERYTHING AND STARTING OVER
minikube delete


# Manual Commands

1. minikube start

create auth service deployment

2. kubectl create deployment authservice --image=rpwtouk/rosaauth:v0.0.7

expose auth service

3. kubectl expose deployment authservice --type=LoadBalancer --port=9090

# Commands using .yml objects

basically everything is done using kubectl apply -f <object name>

https://kubernetes.io/docs/concepts/workloads/controllers/deployment/

# Ingress

https://kubernetes.io/docs/tasks/access-application-cluster/ingress-minikube/

# Debug
1.1 kubectl get pods 

2.1 kubectl get deployments  
2.2 kubectl describe pod <ID>   
  
3.1 kubectl get services
3.2 minikube service authservice
