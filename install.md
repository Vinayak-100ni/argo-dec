```
 kubectl create ns argocd
 helm repo add argo https://argoproj.github.io/argo-helm
 helm repo update
 helm install argocd argo/argo-cd -n argocd   --set server.extraArgs[0]=--insecure
 kubectl port-forward svc/argocd-server -n argocd 8080:443 --address=0.0.0.0 &
 ```
get ```admin``` password 
```
kubectl get secret argocd-initial-admin-secret -n argocd \
-o jsonpath="{.data.password}" | base64 -d
```
