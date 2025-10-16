<!-- Quality & Security Overview -->
[![CodeQL](https://github.com/CalebSargeant/helm-charts/actions/workflows/github-code-scanning/codeql/badge.svg)](https://github.com/CalebSargeant/mikrotik-chr/actions/workflows/github-code-scanning/codeql)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=CalebSargeant_helm-charts&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=CalebSargeant_helm-charts)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=CalebSargeant_helm-charts&metric=security_rating)](https://sonarcloud.io/summary/new_code?id=CalebSargeant_helm-charts)
[![Known Vulnerabilities](https://snyk.io/test/github/CalebSargeant/helm-charts/badge.svg)](https://snyk.io/test/github/CalebSargeant/helm-charts)

<!-- Code Quality & Maintainability -->
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=CalebSargeant_helm-charts&metric=sqale_rating)](https://sonarcloud.io/summary/new_code?id=CalebSargeant_helm-charts)
[![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=CalebSargeant_helm-charts&metric=reliability_rating)](https://sonarcloud.io/summary/new_code?id=CalebSargeant_helm-charts)
[![Technical Debt](https://sonarcloud.io/api/project_badges/measure?project=CalebSargeant_helm-charts&metric=sqale_index)](https://sonarcloud.io/summary/new_code?id=CalebSargeant_helm-charts)

<!-- Code Metrics -->
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=CalebSargeant_helm-charts&metric=coverage)](https://sonarcloud.io/summary/new_code?id=CalebSargeant_helm-charts)
[![Bugs](https://sonarcloud.io/api/project_badges/measure?project=CalebSargeant_helm-charts&metric=bugs)](https://sonarcloud.io/summary/new_code?id=CalebSargeant_helm-charts)
[![Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=CalebSargeant_helm-charts&metric=vulnerabilities)](https://sonarcloud.io/summary/new_code?id=CalebSargeant_helm-charts)
[![Code Smells](https://sonarcloud.io/api/project_badges/measure?project=CalebSargeant_helm-charts&metric=code_smells)](https://sonarcloud.io/summary/new_code?id=CalebSargeant_helm-charts)

<!-- Project Stats -->
[![Lines of Code](https://sonarcloud.io/api/project_badges/measure?project=CalebSargeant_helm-charts&metric=ncloc)](https://sonarcloud.io/summary/new_code?id=CalebSargeant_helm-charts)
[![Duplicated Lines (%)](https://sonarcloud.io/api/project_badges/measure?project=CalebSargeant_helm-charts&metric=duplicated_lines_density)](https://sonarcloud.io/summary/new_code?id=CalebSargeant_helm-charts)

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
