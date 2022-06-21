# Tekton Pipelines

This project provides a [Carvel package](https://carvel.dev/kapp-controller/docs/latest/packaging) for [Tekton Pipelines](https://tekton.dev/docs/pipelines), a cloud-native solution for building CI/CD systems.

## Components

* tekton-pipelines

## Configuration

The Tekton Pipelines package has the following configurable properties.

| Value | Required/Optional | Default | Description |
|-------|-------------------|---------|-------------|
| `artifact.pvc.size` | Optional | Size of the PVC volume for artifact persistence. |
| `artifact.pvc.storageClassName` | Optional | Storage class of the PVC volume for artifact persistence. |
| `cloudevents.enabled` | Optional | Enable the generation of CloudEvents for TaskRun, PipelineRun and Run lifecycle events. |
| `cloudevents.sink` | Optional | The URL of the sink where to send CloudEvents. |

```yaml
artifact:
  pvc:
    size: 5Gi
    storageClassName: default

cloudevents:
  enabled: "false"
  sink: ""
```

## Prerequisites

Before installing the Tekton Pipelines package, you need to add [the Neptunus Platform package repository](https://github.com/neptunus-platform/package-repository) to your cluster.

## Installation

You can install the Tekton package using `kctrl`:

   ```shell
   kctrl package install --package-install tekton-pipelines \
     --package tekton-pipelines.neptunus.thomasvitale.com \
     --version ${TEKTON_PIPELINES_PACKAGE_VERSION}
   ```

   > You can get the `${TEKTON_PIPELINES_PACKAGE_VERSION}` from running `kctrl
   > package available list -p tekton-pipelines.neptunus.thomasvitale.com`.
   > Specifying a namespace may be required depending on where your package
   > repository was installed.

## Documentation

For documentation specific to Tekton Pipelines, check out [tekton.dev](https://tekton.dev).
