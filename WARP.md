# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Repository Overview

This is a Helm charts repository containing reusable Kubernetes deployment templates. Charts are published via GitHub Pages and available at `https://calebsargeant.github.io/helm-charts`.

**Current charts:**
- **homebridge**: Deploys Homebridge as a DaemonSet with host networking for HomeKit device discovery
- **n8n**: Deploys n8n automation platform

## Common Commands

### Linting
```bash
helm lint charts/homebridge/
helm lint charts/n8n/
```

### Testing Templates
Render chart templates without installing:
```bash
helm template test-release charts/homebridge/
helm template test-release charts/n8n/
```

### Packaging Charts
Create chart packages (.tgz files):
```bash
helm package charts/homebridge/
helm package charts/n8n/
```

### Validation
Dry-run an install to catch issues:
```bash
helm install --dry-run --debug test-release ./charts/homebridge/
```

## Architecture

### Chart Structure
Each chart follows Helm 3 standard structure:
- `Chart.yaml`: Chart metadata (version, appVersion, name)
- `values.yaml`: Default configuration values
- `templates/`: Kubernetes resource templates (YAML files with Go templating)
- `README.md`: Chart documentation

### Key Design Patterns

**Homebridge Chart**:
- Uses **DaemonSet** to run on every node (enables HomeKit device discovery across cluster)
- Enables `hostNetwork: true` for direct device communication
- Supports optional PersistentVolume with configurable hostPath for state storage
- Exposes service on port 8581

**n8n Chart**:
- Uses **Deployment** for standard workload orchestration
- Includes Secret management for sensitive configuration
- Supports Ingress for external access

### Common Parameters
All charts support standard Kubernetes configuration:
- **image**: Repository, tag, and pull policy
- **persistence**: PVC/PV configuration for state
- **ingress**: External access configuration
- **resources**: CPU/memory limits and requests
- **nodeSelector, affinity, tolerations**: Pod scheduling

## Release Process

Charts are automatically released on push to `main` branch when files in `charts/` directory change. The GitHub Actions workflow (`release.yaml`) uses `chart-releaser-action` to:
1. Package charts
2. Create GitHub releases
3. Update Helm repository index on `gh-pages` branch

The repository is then available via:
```bash
helm repo add calebsargeant https://calebsargeant.github.io/helm-charts
```

## Quality Gates

The project is scanned by:
- **SonarCloud**: Code quality and security analysis
- **Snyk**: Dependency vulnerability scanning
- **CodeQL**: GitHub security scanning (via Actions)

Configuration is in `sonar-project.properties`.
