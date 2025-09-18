# para verificar os limites de recursos do pod, usar goldilocks
# https://github.com/FairwindsOps/goldilocks
# instalacao
kubectl krew install goldilocks
# uso
kubectl goldilocks deployment meudeployment

# probe (healthcheck) readiness (ready -> quando está pronto e liveness-> quando estiver ativo)

# Exemplo de probe
kubectl create deployment --image nginx nginx --dry-run=client -o yaml | kubectl neat > probe.yaml