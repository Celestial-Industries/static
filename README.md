[![Lint and Test Charts](https://github.com/Celestial-Industries/static/actions/workflows/main.yaml/badge.svg)](https://github.com/Celestial-Industries/static/actions/workflows/main.yaml)

# Static Site Helm Chart

A helm chart for testing. Deploys a static site running in NGINX. Uses a custom image that is found in [Celestial-Industries/nginx](https://github.com/Celestial-Industries/nginx).

Added some extra elements such as readiness & liveness probe, deployment strategy and a regcred for Dockerhub to be able to pull custom image used in the chart.

## Automatic linting and testing deployment
Uses GitHub actions and [Kind](https://kind.sigs.k8s.io/) to test the chart when there are pull requests or pushes to specific branch. The kind config creates a control plane and two nodes, these are labeled and the helm chart is set to use `nodeSelector` to ensure these are deployed to the specific nodes. The Github action also checks the deployment rollout progress and notifies Slack on successful completion. This allows the full deployment lifecycle of a Helm chart via GitHub actions in advance of actually deploying to a real cluster and can be integrated into a development workflow.

## Usage
To deploy to cluster run

```sh
$ helm upgrade --install static --namespace=default . -f ./values.yaml
```

## License

This tool is released under the [MIT License](LICENSE).
