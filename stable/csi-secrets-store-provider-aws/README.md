# csi-secrets-store-provider-aws

AWS Secrets Manager and Config Provider for Secret Store CSI Driver allows you to get secret contents stored in AWS Key Management Service instance and use the Secrets Store CSI driver interface to mount them into Kubernetes pods.

### Prerequisites

- [Helm3](https://helm.sh/docs/intro/quickstart/#install-helm)

### Installing the Chart

- This chart installs the [secrets-store-csi-driver](https://github.com/kubernetes-sigs/secrets-store-csi-driver) and the AWS Secrets Manager and Config Provider for Secret Store CSI Driver

```shell
helm repo add eks https://aws.github.io/eks-charts
helm install eks/csi-secrets-store-provider-aws --generate-name --namespace kube-system
```

### Create the access policy

Follow the [Usage](https://github.com/aws/secrets-store-csi-driver-provider-aws#usage) guide.

### Configuration

The following table lists the configurable parameters of the csi-secrets-store-provider-aws chart and their default values.

> Refer to [doc](https://github.com/kubernetes-sigs/secrets-store-csi-driver/tree/main/charts/secrets-store-csi-driver/README.md) for configurable parameters of the secrets-store-csi-driver chart.

| Parameter | Description | Default |
| --- | --- | --- |
| `imagePullSecrets` | Secrets to be used when pulling images | `[]` |
| `image.repository` | Image repository | `public.ecr.aws/aws-secrets-manager/secrets-store-csi-driver-provider-aws` |
| `image.pullPolicy` | Image pull policy | `Always` |
| `image.tag`| Image tag | `1.0.r2-2021.08.13.20.34-linux-amd64` |
| `nodeSelector` | Node Selector for the daemonset on nodes | `{}` |
| `tolerations` | Tolerations for the daemonset on nodes  | `[]` |
| `ports` | Liveness and readyness tcp probe port  | `8989` |
| `privileged` | Privileged security context | `false`
| `resources`| Resource limit for provider pods on nodes | `requests.cpu: 50m`<br>`requests.memory: 100Mi`<br>`limits.cpu: 50m`<br>`limits.memory: 100Mi` |
| `podLabels`| Additional pod labels | `{}` |
| `podAnnotations` | Additional pod annotations| `{}` |
| `updateStrategy` | Configure a custom update strategy for the daemonset on nodes | `RollingUpdate`|
| `secrets-store-csi-driver.install` | Secrets Store CSI Driver chart install | `false`
| `rbac.install` | Install default service account | true |
| `rbac.pspEnabled` | Pod Security Pods | false |
| `rbac.serviceAccount.name` | Service account to be used. If not set and serviceAccount.create is true a name is generated using the fullname template. | |
