# k8s_pro

A collection of Kubernetes manifests for experiments and application deployments.

## Manifests

### Deployment examples

| File | Description |
| --- | --- |
| `deploy-k8s/aztec.yaml` | HTTPD deployment with one replica |
| `deploy-k8s/frontend.yaml` | HTTPD deployment with ten replicas |
| `deploy-k8s/nginx-pod.yaml` | Nginx and BusyBox pod with a shared `emptyDir` volume |
| `deploy-k8s/nginx-mealie.yaml` | Nginx pod using the `mealie-data` persistent volume claim |
| `mealie/myK8.yaml` | Basic Nginx deployment |

### Mealie

The `mealie/` directory contains a complete Mealie deployment:

- `namespace.yaml` creates the `mealie` namespace.
- `storage.yaml` creates a 500 MiB persistent volume claim.
- `deployment.yaml` deploys Mealie and mounts the persistent volume at `/app/data`.
- `service.yaml` exposes Mealie on port `9000` through a LoadBalancer service.

## Usage

Deploy the Mealie resources in order:

```sh
kubectl apply -f mealie/namespace.yaml
kubectl apply -f mealie/storage.yaml
kubectl apply -f mealie/deployment.yaml
kubectl apply -f mealie/service.yaml
```

The individual manifests can be applied independently with `kubectl apply -f`:

```sh
kubectl apply -f deploy-k8s/
```

Apply the manifests from the repository root. A working Kubernetes cluster and a configured `kubectl` context are required.
