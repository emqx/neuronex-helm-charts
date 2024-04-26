# NeuronEX Chart

Helm chart for NeuronEX.

This chart must be used with [NeuronEX Operator](../neuronex-operator/README.md).

## Values Explanation

| Key | Type | Default | Description |
| --- | --- | --- | --- |
| replicaCount | int | 1 | Number of replicas, set to 0 to disable pod creation |
| image.repository | string | emqx/neuronex | Image repository |
| image.pullPolicy | string | IfNotPresent | Image pull policy |
| image.tag | string | latest | Image tag |
| imagePullSecrets | list | [] | Image pull secrets |
| auth.enabled | bool | true | Enable authentication |
| auth.jwt | list | [] | See [JWT Configuration](#jwt-configuration) |
| env | list | [] | Environment variables for container |
| podSecurityContext | object | {} | Pod security context |
| securityContext | object | {} | Container security context |
| resources | object | {} | Resource requests and limits |
| initContainers | list | [] | Init containers |
| extraContainers | list | [] | Sidecar containers |
| livernessProbe | object | {} | Liveness probe, see <https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/> |
| readinessProbe | object | {} | Readiness probe |
| startupProbe | object | {} | Startup probe |
| storageClass.enabled | bool | false | Enable a custom storage class, you must provide the storage class name |
| storageClass.name | string | "" | Storage class name |
| storageClass.accessModes | list | ReadWriteOnce | Storage class access modes |
| storageClass.size | string | 256Mi | Storage class size |
| volumeClaimTemplates | list | [] | Custom volume claim templates, if you provide this, the `storageClass` will be ignored |
| externalVolumes | list | [] | External volumes you want to include in the pod |
| externalVolumeMounts | list | [] | External volume mounts you want to mount to the container |
| nodeSelector | object | {} | Node selector |
| tolerations | list | [] | Tolerations |
| affinity | object | {} | Affinity |
| nodeName | string | "" | Node name |
| services | list | [] | Custom services you want to expose |

## JWT Configuration

Refer to <https://docs.emqx.com/en/neuronex/latest/api/jwt.html>, if you want to custom JWT, you need to provide a list of name/value pairs in the `auth.jwt` field, which indicates the key files for JWT. When bootstrapping the NeuronEX instance, the operator will create the key files and mount them to the NeuronEX instance.

```yaml
auth:
  jwt:
    - name: neuronex_key
      data: ...
    - name: neuronex_key.pub
      data: ...
```

For generating JWT public/private keys, you can refer to <https://docs.emqx.com/en/neuronex/latest/api/jwt.html#generate-public-and-private-keys>.

> Note: you need to encode the key files with base64 before adding them to the `auth.jwt` field.

We provide an example, you can check the [examples/neuronex/jwt/values.yaml](../../examples/neuronex/jwt/values.yaml).
