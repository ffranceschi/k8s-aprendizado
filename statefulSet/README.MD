# drenar (drain) remover os pods de um node para parar de receber pods
kubectl drain <node-name> --ignore-daemonsets
# remover o node do cluster
kubectl delete node <node-name>
