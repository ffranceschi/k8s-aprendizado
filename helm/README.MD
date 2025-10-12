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
helm install minhaapi ./api-produto

helm list
helm uninstall minhapi


# Adicionar o repositorio bitnami
helm repo add bitnami https://charts.bitnami.com/bitnami
helm search repo mysql

helm install mydb bitnami/mysql --set auth.rootPassword=test1234

comando --dry-run para teste de instalacao
helm install mydb bitnami/mysql --set auth.rootPassword=test1234 --dry-run



