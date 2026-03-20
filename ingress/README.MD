Ingress é a forma de expor os serviços para fora do kubernetes
ingress -> ingress controller -> service -> deployments -> replica set - > pod

# Criar cluster no kind 
kind create cluster --name meu-cluster --config kind-config.yaml

# Site https://kubernetes.github.io/ingress-nginx/user-guide/nginx-configuration/


# kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.13.2/deploy/static/provider/baremetal/deploy.yaml

----
# Fazer com o K3d
adicionar entrada no /etc/hosts 
127.0.0.1 green.localdev.me
127.0.0.1 blue.localdev.me



k3d cluster create --api-port 6550 -p "30000:80@loadbalancer"
subir o arquivo core/serviceClusterIp.yaml
kubectl apply -f core/serviceClusterIp.yaml
kubectl apply -f core/serviceClusterIpBlue.yaml
kubectl apply -f ingress/ingress.yaml

curl http://api.localdev.me:30000

loadbalancer:30000 -> ingress controller (green.localdev.me) -> service:8080 -> deployment:80
loadbalancer:30000 -> ingress controller (blue.localdev.me) -> service:8080 -> deployment:80