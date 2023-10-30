1. install labeller,device plugin and exporter
```
microk8s helm install amd-gpu amdgpu-tool-chart --namespace amdgpu
```

2. install prometheus 
```
helm repo add prometheus-community \
   https://prometheus-community.github.io/helm-charts

helm install prometheus-community/kube-prometheus-stack \
   --create-namespace --namespace prometheus \
   --generate-name \
   --values /tmp/kube-prometheus-stack.values
```

3. (optional) patch grafana to NodePort
```
kubectl patch svc kube-prometheus-stack-1603211794-grafana \
   -n prometheus \
   --patch "$(cat grafana-patch.yaml)"
```