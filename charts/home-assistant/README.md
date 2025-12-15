# Home Assistant Helm Chart

This Helm chart deploys Home Assistant on Kubernetes.

## Installation

```bash
helm install home-assistant ./home-assistant
```

## Configuration

See `values.yaml` for configuration options.

## Parameters

### Home Assistant parameters

| Name                                            | Description                                                                                                                         | Value                                   |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------- |
| `enabled`                                       | Whether to enable Home Assistant.                                                                                                   | `true`                                  |
| `replicaCount`                                  | The number of replicas to deploy.                                                                                                   | `1`                                     |
| `image.repository`                              | The Docker repository to pull the image from.                                                                                       | `ghcr.io/home-assistant/home-assistant` |
| `image.tag`                                     | The image tag to use.                                                                                                               | `2024.11.3`                             |
| `image.pullPolicy`                              | The logic of image pulling.                                                                                                         | `IfNotPresent`                          |
| `imagePullSecrets`                              | The image pull secrets to use.                                                                                                      | `[]`                                    |
| `deployment.strategy.type`                      | The deployment strategy to use.                                                                                                     | `Recreate`                              |
| `serviceAccount.create`                         | Whether to create a service account.                                                                                                | `true`                                  |
| `serviceAccount.annotations`                    | Additional annotations to add to the service account.                                                                               | `{}`                                    |
| `serviceAccount.name`                           | The name of the service account to use. If not set and create is true, a new service account will be created with a generated name. | `""`                                    |
| `podAnnotations`                                | Additional annotations to add to the pod.                                                                                           | `{}`                                    |
| `podSecurityContext`                            | The security context to use for the pod.                                                                                            | `{}`                                    |
| `securityContext.privileged`                    | Whether to run the container in privileged mode.                                                                                    | `true`                                  |
| `initContainers`                                | Additional init containers to add to the pod.                                                                                       | `[]`                                    |
| `service.type`                                  | The type of service to create.                                                                                                      | `ClusterIP`                             |
| `service.port`                                  | The port on which the service will run.                                                                                             | `8123`                                  |
| `service.nodePort`                              | The nodePort to use for the service. Only used if service.type is NodePort.                                                         | `""`                                    |
| `ingress.enabled`                               | Whether to create an ingress for the service.                                                                                       | `false`                                 |
| `ingress.className`                             | The ingress class name to use.                                                                                                      | `""`                                    |
| `ingress.annotations`                           | Additional annotations to add to the ingress.                                                                                       | `{}`                                    |
| `ingress.hosts[0].host`                         | The host to use for the ingress.                                                                                                    | `chart-example.local`                   |
| `ingress.hosts[0].paths[0].path`                | The path to use for the ingress.                                                                                                    | `/`                                     |
| `ingress.hosts[0].paths[0].pathType`            | The path type to use for the ingress.                                                                                               | `ImplementationSpecific`                |
| `ingress.tls`                                   | The TLS configuration for the ingress.                                                                                              | `[]`                                    |
| `resources`                                     | The resources to use for the pod.                                                                                                   | `{}`                                    |
| `autoscaling.enabled`                           | Whether to enable autoscaling.                                                                                                      | `false`                                 |
| `autoscaling.minReplicas`                       | The minimum number of replicas to scale to.                                                                                         | `1`                                     |
| `autoscaling.maxReplicas`                       | The maximum number of replicas to scale to.                                                                                         | `100`                                   |
| `autoscaling.targetCPUUtilizationPercentage`    | The target CPU utilization percentage to use for autoscaling.                                                                       | `80`                                    |
| `autoscaling.targetMemoryUtilizationPercentage` | The target memory utilization percentage to use for autoscaling.                                                                    | `80`                                    |
| `nodeSelector`                                  | The node selector to use for the pod.                                                                                               | `{}`                                    |
| `tolerations`                                   | The tolerations to use for the pod.                                                                                                 | `[]`                                    |
| `affinity`                                      | The affinity to use for the pod.                                                                                                    | `{}`                                    |
| `env.TZ`                                        | The timezone to use for the pod.                                                                                                    | `Europe/London`                         |
| `persistence.enabled`                           | Whether to enable persistence.                                                                                                      | `true`                                  |
| `persistence.storageClass`                      | The storage class to use for the persistence.                                                                                       | `""`                                    |
| `persistence.existingClaim`                     | The name of an existing claim to use for the persistence.                                                                           | `""`                                    |
| `persistence.accessMode`                        | The access mode to use for the persistence.                                                                                         | `ReadWriteOnce`                         |
| `persistence.size`                              | The size to use for the persistence.                                                                                                | `1Gi`                                   |
| `persistence.additionalVolumes`                 | Additional volumes to add to the pod.                                                                                               | `[]`                                    |
| `persistence.additionalMounts`                  | Additional volume mounts to add to the pod.                                                                                         | `[]`                                    |

