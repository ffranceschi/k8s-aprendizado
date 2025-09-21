# Tipos de services, clusterIP, nodePort, loadBalancer
## clusterIP nao expõe o service para fora do cluster, apenas para dentro
## nodePort expõe o service para fora do cluster, na porta especificada
## loadBalancer expõe o service para fora do cluster, na porta especificada, e cria um load balancer
### loadBalancer é um tipo de service que expõe o service para fora do cluster, na porta especificada, e cria um load balancer

# dns é <nome do service>.<namespace>.svc.cluster.local

# para saber o endpoint do service, que retorna o ip e a porta dos pods
kubectl get endpoints 

# os labels do service, são usados para fazer a seleção dos pods

# Ver os labels dos pods
kubectl get po --show-labels

