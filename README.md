kubectl
minikube

## Verify Installation
Run 
`minikube version`
to verify that Minikube is installed correctly.

## Run Minikube
We'll be using Kubernetes with Docker, which is arguably the most common way to use Kubernetes. Make sure your Docker daemon is running before starting Minikube. If you haven't yet taken our Docker course, you should do that first.

Next, run:

`minikube start --extra-config="apiserver.cors-allowed-origins=['http://boot.dev']"`

## Dashboard
Next, run the following command:
`minikube dashboard --port=63840`


## Previous Minikube Installations
If you've installed minikube in the past, you might have conflicts. If you don't care about your old minikube clusters, you can delete them by running:

`minikube stop`
`minikube delete`

### Important kubectl commands
`kubectl get pods`
`kubectl get pods -o wide`
`kubectl logs <PODNAME>`
`kubectl delete pod <PODNAME>`
`kubectl proxy`
`kubectl get deployment synergychat-web -o yaml`
`kubectl edit deployment synergychat-web`
`kubectl get replicasets`
`kubectl get deployment synergychat-web -o yaml > web-deployment.yaml`
`kubectl apply -f web-deployment.yaml`
`kubectl port-forward <pod-name> 8080:8080`
`kubectl port-forward service/web-service 8080:80`
`kubectl get svc web-service -o yaml`

## Gateway
`kubectl apply --server-side -f https://github.com/envoyproxy/gateway/releases/download/v1.5.1/install.yaml`

## Tunnel
`minikube tunnel -c`

## Namespaces
`kubectl get namespaces`

## Metrics
To get metrics working, we need to enable the metrics-server addon. Run:

`minikube addons enable metrics-server`

Take a look inside the kube-system namespace:

`kubectl -n kube-system get pod`

You should see a new "metrics-server" pod. It might take a couple of minutes to get started, but once that pod is ready, you should be able to run:

`kubectl top pod`

The kubectl top command will show you the resources that each pod is using. In the example above, each pod is using about 1 milliCPU and 15 megabytes of memory.