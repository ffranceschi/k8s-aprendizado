# install do prometheus via helm
helm install prometheus oci://ghcr.io/prometheus-community/charts/prometheus --namespace monitoramento --create-namespace

helm upgrade prometheus oci://ghcr.io/prometheus-community/charts/prometheus --values values.yaml --namespace monitoramento --install --create-namespace






