# instalação do vault da hashcorp
helm repo add hashicorp https://helm.releases.hashicorp.com
helm repo update
kubectl create namespace vault
helm install vault hashicorp/vault --namespace vault


# Para redirecionar o servico do vault para local
k port-forward service/vault -n vault 8200:8200 > /dev/null 2>&1 &

# use o export para redirecionar para a porta local
export VAULT_ADDR="http://localhost:8200"

vault status
vault operator init

# Saida deve parecer com isso
Unseal Key 1: S6rYAT3WI/x3K6oNCfmlU0PrkxdADtvm0Bx1AqH/qpQh
Unseal Key 2: 9aPDxB0lk+XX6QgSECv4oemCuRaZD7Qmv4Qjd4m/b5BS
Unseal Key 3: PmxlZZ+BQ1Hux4/DoLqDfBAvJWdE/1bQy8mEUqhhF7Nb
Unseal Key 4: 0UEYolcGNPMUZsjFiacSX2v9gM4F4tHTxXKDGxw2GzG3
Unseal Key 5: IGfYYiOyqDZJoYier63jLtjOtNaM+wT90fwvt7dtFFqU

Initial Root Token: hvs.FnvCrDgJ89An8bSyzUgKbznu

# precisa exportar para dar comando no vault o token root
export VAULT_TOKEN="hvs.FnvCrDgJ89An8bSyzUgKbznu"

# deslacrar o cofre precisa rodar 3x com chaves de unseal distintas
vault operator unseal

# logar com token root
vault login <token>
vault login hvs.FnvCrDgJ89An8bSyzUgKbznu




# Despois de deslacrado, logue com o token root
http://localhost:8200


# criar secrets
vault secrets enable -path=secret kv-v2
vault kv put secret/segredo-teste username=fernando senha=qwe123

vault kv get secret/segredo-teste
vault kv get -field=senha secret/segredo-teste






