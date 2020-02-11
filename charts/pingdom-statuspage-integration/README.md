# Pingdom StatusPage integration

## Introduction

pingdom-statuspage-integration finds StatusPage Component based on name of Pingdom Check and changes it's status based on currentStatus field from Pingdom Webhook. If there is more than one StatusPage Component with the same name(f.ex. on multiple pages) as Pingdom Check then status of all those components will be affected.
We recommend using one replica because of the rate limits.

## Prerequisites

-  kubernetes 1.11+

## Installing the Chart

To install the chart with the release name `pingdom-statuspage-integration`:

```bash
$ helm repo add docplanner https://docplanner.github.io/helm-charts/ 
$ helm repo update
$ helm install docplanner/pingdom-statuspage-integration --name pingdom-statuspage-integration --values=my-values.yaml
```

## Uninstalling the Chart

To uninstall/delete the `pingdom-statuspage-integration` deployment:

```bash
$ helm delete pingdom-statuspage-integration
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the pingdom-statuspage-integration chart and their default values.

| Parameter                                  | Description                               | Default                            |
| ------------------------------------------ | ----------------------------------------- | ---------------------------------- |
| `replicaCount` | replica count | `1`|
| `image.repository` | Docker image repo | `docplanner/pingdom-statuspage-integration`|
| `image.tag` | Docker image tag | `latest`|
| `image.pullPolicy` | Docker image pull policy| `IfNotPresent`|
| `imagePullSecrets` | Image pull secrets | `[]` |
| `serviceAccount.create` | If `true`, create a new service account	| `true` |
| `serviceAccount.name` | Service account to be used | `pingdom-statuspage-integration` |
| `podSecurityContext` | Pod Security Context | `{}` |
| `securityContext` | Security Context | `{}` |
| `service.type` | Service type to be used	| `ClusterIP` |
| `service.port` | Service port to be used	| `80` |
| `resources` | Resources | `{}`|
| `nodeSelector` | NodeSelector | `{}`|
| `tolerations` | Tolerations | `[]`|
| `affinity` | Affinity | `{}`|
| `ingress.enabled` | Ingress enabled | `false` |
| `ingress.annotations` | Ingress annotations | `{}` |
| `ingress.hosts` | Ingress hosts YAML | `[]` |
| `ingress.tls` | Ingress TLS | `[]` |
| `config.secret` | secret used in communication from Pingdom | `""` |
| `config.statuspageToken` | StatusPage API key | `""` |
| `config.maxRetries` | Number of retries | `"2"` |
| `config.retryInterval` | Numer of seconds between retries | `"10"` |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example:

```bash
$ helm install --name pingdom-statuspage-integration --set image.tag=v1.0.0 docplanner/pingdom-statuspage-integration
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart.