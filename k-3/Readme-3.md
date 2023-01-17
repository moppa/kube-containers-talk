# Minikube
minikube start

minikube image ls

docker buildx build -t kubedemo:local ../d-1/

minikube image load kubedemo:local

docker images
minikube docker-env
eval $(minikube -p minikube docker-env)
eval $(minikube -p minikube docker-env -u)
docker images
docker buildx build -t kubedemo:mini ../d-1/

minikube dashboard

kubectl config get-contexts
kubectl config use-context aks-digital-tmp-dev-se
kubectl config use-context minikube

# Namespaces
kubectl get namespace

kubectl create namespace demo-3
kubectl create namespace demo-x -o yaml
kubectl delete namespace demo-x

kubectl -n demo-3 get all

# Deployment, Replicaset & Pod
kubectl -n demo-3 apply -f deployment.yml -o yaml
kubectl -n demo-3 get all

kubectl -n demo-3 logs -l app=nginx
kubectl -n demo-3 exec -it pod/XX -- /bin/bash

curl http://localhost:80

# Service
kubectl -n demo-3 apply -f service.yml -o yaml
kubectl -n demo-3 get all

curl http://SERVICEIP
kubectl -n demo-3 exec -it pod/XX -- /bin/bash
curl http://SERVICEIP
curl http://web-lb

# Ingress

## Ingress Controller - Nginx
https://kubernetes.github.io/ingress-nginx/deploy/

`helm upgrade [RELEASE] [CHART] [flags]`
helm upgrade --install ingress-local ingress-nginx --repo https://kubernetes.github.io/ingress-nginx --namespace ingress --create-namespace --dry-run | code -

minikube tunnel

kubectl -n ingress get all
http://localhost

## Ingress
kubectl -n demo-3 apply -f ingress.yml

http://mytest.localhost.direct

### SSL
kubectl create secret tls -n demo-3 local-default-cert --key /home/moppa/code/localhost.direct/localhost.direct.key --cert /home/moppa/code/localhost.direct/localhost.direct.crt

kubectl -n demo-3 apply -f ingress-tls.yml

chrome://net-internals/#hsts