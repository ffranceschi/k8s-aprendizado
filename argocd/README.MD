# instalacao do argo CD
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

kubectl port-forward svc/argocd-server -n argocd 8080:443

# para ver os recursos disponiveis no argocd
kubectl api-resources

kubectl port-forward -n webcolor service/webpage 30080:80



