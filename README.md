[![Lint and Test Charts](https://github.com/Celestial-Industries/static/actions/workflows/main.yaml/badge.svg)](https://github.com/Celestial-Industries/static/actions/workflows/main.yaml)

# Static Site Helm Chart

A helm chart for testing. Deploys a static site running in NGINX. Uses a custom image that is found in [Celestial-Industries/nginx](https://github.com/Celestial-Industries/nginx).

Added some extra elements such as readiness & liveness probe, deployment strategy and a regcred for Dockerhub to be able to pull custom image used in the chart.

## Usage
To deploy to cluster run

```sh
$ helm upgrade --install static --namespace=default . -f ./values.yaml
```

## License

This tool is released under the [MIT License](LICENSE).
