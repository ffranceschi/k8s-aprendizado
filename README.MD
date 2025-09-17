https://github.com/ffranceschi/app-variaveis-ambiente

https://github.com/ffranceschi/conversao-temperatura

Metric Server - Base para monitoramento - https://github.com/kubernetes-sigs/metrics-server

# plugin para instalar que remove os campos vazios do yaml
https://krew.sigs.k8s.io/docs/user-guide/setup/install/
k krew install neat

#exemplo de uso
k get po nginx -o yaml | k neat
