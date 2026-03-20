# criar o cluster com 
k3d cluster create meu-cluster \
  --k3s-arg "--disable=traefik@server:*" \
  --port "8080:80@loadbalancer" \
  --port "8443:443@loadbalancer"

# instalacao do metal LB ou instalar com helm (https://metallb.io/installation/)
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.14.3/config/manifests/metallb-native.yaml

# Aguarde os pods subirem
kubectl wait --namespace metallb-system \
  --for=condition=ready pod \
  --selector=app=metallb \
  --timeout=90s

  # como é o fluxo com ingress
  load balancer -> ingress -> svc -> deployment -> rs -> pod


  -------------

  kind create cluster --config kind-config.yaml --name meu-cluster

# instalacao metallb
  kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.14.5/config/manifests/metallb-native.yaml

# Aguardar os pods subirem
kubectl wait --namespace metallb-system \
  --for=condition=ready pod \
  --selector=app=metallb \
  --timeout=90s

  docker network inspect kind | grep -A 3 '"Subnet"'
# Exemplo de saída: "Subnet": "172.18.0.0/16", utilize para preencher o address-pool

kubectl apply -f rede/address-pool.yaml

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml

# Aguardar
kubectl wait --namespace ingress-nginx \
  --for=condition=ready pod \
  --selector=app.kubernetes.io/component=controller \
  --timeout=90s

kubectl apply -f rede/app.yaml
kubectl apply -f rede/ingress.yaml
echo "172.21.0.100  minha-app.local" | sudo tee -a /etc/hosts
