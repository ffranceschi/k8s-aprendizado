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
Unseal Key 1: pXdaMGoRfCziORaap/jnpBHLYYgwzpPokwfiEzmcSfS1
Unseal Key 2: I5W8N7p9rh4YgOeOcruJORiqz+2DcA5xOv8Hc4vbdcld
Unseal Key 3: +R7SJGLZ/+AA99U4G29qEFDhvYOz2OSlPHFLuEKA5apt
Unseal Key 4: 8jMeZtgx08zwunb5foWKZov8lWoefCVVGbjoV2rtY0jF
Unseal Key 5: IFBx4l4t9u82tZ1vdwYqgP//SDfASGF+wrdxqfFdIlpR

Initial Root Token: hvs.eFF1x2faszZyFnhkLDRtka6O

# precisa exportar para dar comando no vault o token root
export VAULT_TOKEN="hvs.eFF1x2faszZyFnhkLDRtka6O"

# deslacrar o cofre precisa rodar 3x com chaves de unseal distintas
vault operator unseal

# logar com token root
vault login <token>
vault login hvs.eFF1x2faszZyFnhkLDRtka6O




# Despois de deslacrado, logue com o token root
http://localhost:8200


# criar secrets
vault secrets enable -path=secret kv-v2
vault kv put secret/segredo-teste username=fernando senha=qwe123

vault kv get secret/segredo-teste
vault kv get -field=senha secret/segredo-teste






