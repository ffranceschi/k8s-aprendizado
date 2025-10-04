# mudar usuario de execução do container
kubectl exec -it <pod-name> -c <container> -- /bin/bash
kubectl exec -it meudeployment-7c74f8c5d6-n5vqs -c web -- /bin/bash

# docker in docker (dind) 
kubectl exec -it dind-85dff7665c-d9vd9 -- /bin/sh

# service account é por namespace (kubectl api-resources) 
kubectl get serviceaccount
kubectl get sa -n default

# verificar se o service account vinculado ao pod
k describe pod meudeployment-79fdbbf57d-smpqg

