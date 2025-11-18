# secret fica em base64
# configMap não fica em base64

# para criar um secret
kubectl create secret generic meu-secret --from-literal=username=admin --from-literal=password=123456

# para ver os secrets
kubectl get secret

# para ver os detalhes de um secret
kubectl describe secret meu-secret

# As secrets por padrão são passadas como variáveis de ambiente e não são expostas no filesystem
# Para expor um secret no filesystem, é necessário montar o volume do secret no pod
