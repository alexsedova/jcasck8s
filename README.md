# jcasck8s

There is test project to try run jcasc on k8s cluster. Jcasc image stolen from here https://github.com/figaw/configuration-as-code-jenkins-k8s/tree/master/jcasc

## Minikube

Start minikube on your local machine.

To get jcasc pod up and running:
```
kubectl create -f deployment.yaml
```
Jcasc run as a deployment with two replicas. 
Expose pods ports:

```
kubectl expose deployment jcasc --type=NodePort --port=8080
```
Alternatively create service using service.yml

```
kubectl create -f service.yml
```
Now forward the node port to make your browser see it

```
kubectl port-forward service/jcasc 8080:8080
```

## Learnings

You can create yml files describing existing entities by run kubectl get \<type of service\> \<name of service\> -o yaml > name.yaml 
For example:
```
kubectl get service jcasc -o yaml > service.yml
```