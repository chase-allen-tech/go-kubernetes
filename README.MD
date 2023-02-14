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
