# subir um pod para Troubleshooting
kubectl run prompt -it --image ubuntu -- /bin/bash

# redirecionar porta
kubectl port-forward service/webcolor
kubectl port-forward pod/meupod

# executar comando em um pod
kubectl exec pod-name-xyz -- ls
kubectl exec -it pod-name-xyz -- /bin/bash




