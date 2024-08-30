## ArgoCD install and login
```
# create k3d cluster
k3d cluster create argo

# create namespace
kubectl create namespace argocd

# install ArgoCD
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# port-forward ArgoCD
kubectl port-forward svc/argocd-server -n argocd 8080:443&

# in a new terminal tab get password in base64 format and decrypt it 
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"|base64 -d;echo
```
![ArgoCD login](argocd-login.gif)
