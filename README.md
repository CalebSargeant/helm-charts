# Helm Charts

Collection of reusable Helm charts and templates, published via GitHub Pages.

## Usage

[Helm](https://helm.sh) must be installed to use the charts. Please refer to Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm is set up properly, add the repo as follows:

```bash
helm repo add calebsargeant https://calebsargeant.github.io/helm-charts
```

You can then run `helm search repo calebsargeant` to see the charts.

## Available Charts

### Homebridge

A Helm chart for deploying [Homebridge](https://homebridge.io) as a DaemonSet on Kubernetes with host networking enabled.

```bash
helm install my-homebridge calebsargeant/homebridge
```

See the [chart README](charts/homebridge/README.md) for more information.

## Development

### Prerequisites

- Helm 3.0+
- Git

### Linting Charts

```bash
helm lint charts/homebridge/
```

### Packaging Charts

```bash
helm package charts/homebridge/
```

### Testing Templates

```bash
helm template test-release charts/homebridge/
```

## Releases

Charts are automatically packaged and released via GitHub Actions when changes are pushed to the `main` branch. The chart-releaser action will:

1. Package all charts in the `charts/` directory
2. Create GitHub releases for each chart version
3. Update the Helm repository index on the `gh-pages` branch

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.

## License

See [LICENSE](LICENSE) for more information.
