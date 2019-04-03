# Instructions

```bash
minikube delete
```

```bash
minikube start \
  --cpus=2 \
  --memory=3072 \
  --kubernetes-version="v1.13.0" \
  --vm-driver=virtualbox
```

## Operator

```bash
kubectl apply -f ./bootstrap/
kubectl rollout status deployment/prometheus-operator -n monitoring
```

```bash
kubectl apply -f ./prometheus/
kubectl rollout status statefulset/prometheus-k8s -n monitoring
```

```bash
kubectl apply -f ./services/
kubectl get servicemonitors --all-namespaces
```

```bash
kubectl apply -f ./alertmanager/
kubectl rollout status statefulset/alertmanager-k8s -n monitoring
```
