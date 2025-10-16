# n8n Helm Chart

This Helm chart deploys n8n, an extensible workflow automation platform, on Kubernetes.

## Installation

Add the repository and install the chart:

```bash
helm repo add calebsargeant https://calebsargeant.github.io/helm-charts
helm repo update
helm install n8n calebsargeant/n8n --namespace automation --create-namespace
```

## Configuration

Key values to customize:

- `image.tag`: Container image tag
- `resources`: CPU and memory requests/limits
- `env`: Environment variables for n8n configuration
- `secrets`: PostgreSQL credentials and encryption key
- `ingress`: Ingress configuration for external access
- `persistence`: Storage configuration

See `values.yaml` for all available options.

## Prerequisites

- PostgreSQL database accessible at `postgres.database.svc.cluster.local:5432`
- PersistentVolume support for persistent storage
- Ingress controller (e.g., Traefik) for external access
