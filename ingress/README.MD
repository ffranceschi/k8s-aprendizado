Ingress é a forma de expor os serviços para fora do kubernetes
ingress -> ingress controller -> service -> deployments -> replica set - > pod

# Criar cluster no kind 
kind create cluster --name meucluster --config kind-config.yaml

# Site https://kubernetes.github.io/ingress-nginx/user-guide/nginx-configuration/


# kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.13.2/deploy/static/provider/baremetal/deploy.yaml

