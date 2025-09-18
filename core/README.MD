
LB -> service -> deployments -> replicaSet-> pods

# comandos para ver a estrutura do yaml
kubectl explain deployment
kubectl explain deployment.spec
kubectl explain deployment.spec.template.spec.containers

# comandos kubectl, utilizar o -w para watch
kubectl top nodes
kubectl top pods
kubectl get hpa

# subir um pod para Troubleshooting
kubectl run prompt -it --image ubuntu -- /bin/bash
kubectl run --image alpine --rm -it demo sh

# redirecionar porta
kubectl port-forward service/webcolor
kubectl port-forward pod/meupod

# executar comando em um pod
kubectl exec pod-name-xyz -- ls
kubectl exec -it pod-name-xyz -- /bin/bash

# verifica os historicos de rollout
kubectl rollout history deployment meudeployment

# volta o deployment anterior
kubectl rollout undo deployment meudeployment

# criar cluster com Load Balancer, para isso usar nodeport
k3d cluster create meucluster --servers 3 --agents 3 -p "30000:30000@loadbalancer"

# criar namespace
kubectl create namespace nginx

# maneira simples de criar um pod
kubectl run --image httpd nome_pod --dry-run=client -o yaml | kubectl neat > manifesto.yaml

# Static pod (aqueles que nao tem os numeros randomicos) o arquivo fica fisicamente no /etc/kubernetes onde fica os manifestos dos static pods








