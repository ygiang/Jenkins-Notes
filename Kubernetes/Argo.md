# Installation of ArgoCD
1. Create argo namespace in the kubernete cluster
```sh
kubectl create namespace argocd
```
2. Install argocd
```sh
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
#### To get the default login password
```sh
kubectl get pods -n argocd -l app.kubernetes.io/name=argocd-server -o name | cut -d'/' -f 2
```
#### To login
1. Open local proxy to argo pod
```sh
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
2. Login with user `admin` and password obtained from step aboved

