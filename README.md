## kubernetes-basics


# Minikube installation on AWS ec2 instance

```
1.Install kubectl
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"

chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl

2.Install docker
sudo apt-get update && \
    sudo apt-get install docker.io -y
	
3.Install Minikube
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
  && chmod +x minikube
  
sudo mkdir -p /usr/local/bin/
sudo install minikube /usr/local/bin/

4.Check Minikube Version
minikube version

5.Running Minikube on EC2 Ubuntu
sudo -i
sudo apt-get install -y conntrack
minikube start --vm-driver=none
minikube status

```
# Run and deploy pod:

```
1.Let us run our first container
kubectl run hello-minikube --image=gcr.io/google_containers/echoserver:1.4 --port=8080
2.kubectl get pods
3.kubectl create deployment hello-minikube --image=gcr.io/google_containers/echoserver:1.4 
4.kubectl get deployments
5.kubectl expose deployment hello-minikube --type=NodePort --port=8080
6.kubectl get services
```
# kubectl pod commands:

```
kubectl run nginx --image=nginx
kubectl get pods
kubectl describe pod nginx
kubectl get pods -o wide
```
 
# Replicaset command:
```
kubectl edit replicaset myapp-replicaset
kubectl describe replicaset myapp-replicaset
kubect delete pod myapp-replicaset
kubectl create -f replicaset.yaml
kubectl scale replicaset myapp-replicaset --replicas=4
```