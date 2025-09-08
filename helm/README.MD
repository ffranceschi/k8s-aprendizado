# Instalacao
brew install helm

helm repo add stable https://charts.helm.sh/stable

helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx

helm repo update

kubectl create namespace nginx
helm install meu-ingress-controller ingress-nginx/ingress-nginx --namespace nginx

helm list -n nginx

# criar um helm chart
helm create api-produto


# Para instalar o heml criado da pasta api-produto
helm install minhapi ./api-produto

