https://www.bogotobogo.com/GoLang/GoLang_Web_Building_Docker_Image_and_Deploy_to_Kubernetes.php

docker login

docker build -t go-app-img .
docker run -d -p 3333:3000 --name go-app-container go-app-img
docker stop go-app-container

<!-- Deploy to Kuberneetes cluster -->
minikube start
kubectl get svc
kubectl get pods
kubectl get deployments

<!-- Push the image to DockerHub -->
docker build -t chaseallen/go-app .
docker push chaseallen/go-app:latest

<!-- Deploy to minikube cluster -->
kubectl create -f deployment.yaml
kubectl get deployments
kubectl get pods

<!-- Exposing the go-app pod -->
kubectl expose deployment my-go-app --type=NodePort --name=go-app-svc --target-port=3000 
kubectl get svc
minikube ip