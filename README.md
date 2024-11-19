[![Lint and Test Charts](https://github.com/Celestial-Industries/static/actions/workflows/main.yaml/badge.svg)](https://github.com/Celestial-Industries/static/actions/workflows/main.yaml)

# Static Site Helm Chart

A helm chart for testing. Deploys a static site running in NGINX. Uses a custom image that is found in [Celestial-Industries/nginx](https://github.com/Celestial-Industries/nginx).

Added some extra elements such as readiness & liveness probe, deployment strategy and a custom image pull secret for GHCR to be able to pull custom image used in the chart. If using GHCR and a custom image then the repo action needs to be added to the [package settings](https://github.com/orgs/Celestial-Industries/packages/container/nginx%2Fgary-nginx/settings) for the container with `read` access. Also see this [documentation](https://docs.github.com/en/actions/use-cases-and-examples/publishing-packages/publishing-docker-images#publishing-images-to-github-packages) as well as this [issue answer for some further details](https://github.com/orgs/community/discussions/46641#discussioncomment-6242949).

## Automatic linting and testing deployment
Uses GitHub actions and [Kind](https://kind.sigs.k8s.io/) to test the chart when there are pull requests or pushes to specific branch. The kind config creates a control plane and two nodes, these are labeled and the helm chart is set to use `nodeSelector` to ensure these are deployed to the specific nodes. The Github action also checks the deployment rollout progress and notifies Slack on successful completion. This allows the full deployment lifecycle of a Helm chart via GitHub actions in advance of actually deploying to a real cluster and can be integrated into a development workflow.

## Usage
To deploy to cluster run

```sh
helm upgrade --install static --namespace=default . -f ./values.yaml --set autoscaling.enabled=false
```

## License

This tool is released under the [MIT License](LICENSE).
