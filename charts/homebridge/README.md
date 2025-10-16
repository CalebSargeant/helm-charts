# Homebridge Helm Chart

This chart deploys [Homebridge](https://homebridge.io) as a DaemonSet on a Kubernetes cluster using the Helm package manager.

## Prerequisites

- Kubernetes 1.19+
- Helm 3.0+

## Installing the Chart

To install the chart with the release name `my-homebridge`:

```bash
helm install my-homebridge ./charts/homebridge
```

## Uninstalling the Chart

To uninstall/delete the `my-homebridge` deployment:

```bash
helm uninstall my-homebridge
```

## Configuration

The following table lists the configurable parameters of the Homebridge chart and their default values.

| Parameter | Description | Default |
|-----------|-------------|---------|
| `image.repository` | Homebridge image repository | `homebridge/homebridge` |
| `image.tag` | Homebridge image tag | `2024-01-08` |
| `image.pullPolicy` | Image pull policy | `IfNotPresent` |
| `daemonset.hostNetwork` | Enable host networking for the DaemonSet | `true` |
| `daemonset.dnsPolicy` | DNS policy when using hostNetwork | `ClusterFirstWithHostNet` |
| `service.type` | Kubernetes service type | `ClusterIP` |
| `service.port` | Service port | `8581` |
| `service.targetPort` | Container port | `8581` |
| `ingress.enabled` | Enable ingress | `false` |
| `ingress.className` | Ingress class name | `""` |
| `ingress.hosts[0].host` | Hostname for the ingress | `homebridge.local` |
| `ingress.hosts[0].paths[0].path` | Path for the ingress | `/` |
| `ingress.hosts[0].paths[0].pathType` | Path type | `Prefix` |
| `persistence.enabled` | Enable persistence | `true` |
| `persistence.storageClass` | Storage class for PVC | `""` |
| `persistence.accessMode` | Access mode for PVC | `ReadWriteOnce` |
| `persistence.size` | Size of PVC | `1Gi` |
| `persistence.hostPath` | Host path for PV (when specified, creates a PV) | `/var/lib/homebridge` |
| `resources` | CPU/Memory resource requests/limits | `{}` |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example:

```bash
helm install my-homebridge ./charts/homebridge \
  --set ingress.enabled=true \
  --set ingress.hosts[0].host=homebridge.example.com
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart:

```bash
helm install my-homebridge ./charts/homebridge -f values.yaml
```

## Features

- **DaemonSet Deployment**: Runs Homebridge on each node in the cluster
- **Host Network**: Uses `hostNetwork: true` to enable Homebridge to discover and communicate with HomeKit devices
- **Persistent Storage**: Stores Homebridge configuration and plugins in a persistent volume
- **Ingress Support**: Optional ingress configuration for external access
- **Configurable Resources**: Customizable CPU and memory limits/requests

## Default Credentials

The default credentials for the Homebridge UI are:
- **Username**: admin
- **Password**: admin

**Important**: Change these credentials after your first login!

## Notes

- The chart uses host networking by default to allow Homebridge to discover HomeKit devices
- A PersistentVolume is created using hostPath when `persistence.hostPath` is specified
- The Homebridge UI is accessible on port 8581
