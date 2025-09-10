<!-- Warning: Do not manually edit this file. See notes on gluon + helm-docs at the end of this file for more information. -->
# coder

![Version: 2.24.0-bb.0](https://img.shields.io/badge/Version-2.24.0--bb.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 2.24.3](https://img.shields.io/badge/AppVersion-2.24.3-informational?style=flat-square) ![Maintenance Track: community_maintained](https://img.shields.io/badge/Maintenance_Track-community_maintained-red?style=flat-square)

Remote development environments on your infrastructure

## Upstream References

- <https://github.com/coder/coder>
- <https://github.com/coder/coder/tree/main/helm/coder>

## Upstream Release Notes

- [Find upstream chart's release notes and CHANGELOG here](https://coder.com/docs/install/releases)

## Learn More

- [Application Overview](docs/overview.md)
- [Other Documentation](docs/)

## Pre-Requisites

- Kubernetes Cluster deployed
- Kubernetes config installed in `~/.kube/config`
- Helm installed

Kubernetes: `>= 1.19.0-0`

Install Helm

https://helm.sh/docs/intro/install/

## Deployment

- Clone down the repository
- cd into directory

```bash
helm install coder chart/
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| domain | string | `"bigbang.dev"` |  |
| sso.enabled | bool | `false` |  |
| istio.enabled | bool | `false` |  |
| istio.hardened.enabled | bool | `false` |  |
| istio.hardened.customAuthorizationPolicies | list | `[]` |  |
| istio.hardened.outboundTrafficPolicyMode | string | `"REGISTRY_ONLY"` |  |
| istio.hardened.customServiceEntries | list | `[]` |  |
| istio.coder.gateways[0] | string | `"istio-system/main"` |  |
| istio.coder.hosts[0] | string | `"coder.{{ .Values.domain }}"` |  |
| networkPolicies.enabled | bool | `false` |  |
| networkPolicies.ingressLabels.app | string | `"istio-ingressgateway"` |  |
| networkPolicies.ingressLabels.istio | string | `"ingressgateway"` |  |
| networkPolicies.controlPlaneCidr | string | `"0.0.0.0/0"` |  |
| networkPolicies.additionalPolicies | list | `[]` |  |
| monitoring.enabled | bool | `false` |  |
| monitoring.namespace | string | `"monitoring"` |  |
| upstream.nameOverride | string | `"coder"` |  |
| upstream.coder.env | list | `[]` |  |
| upstream.coder.envFrom | list | `[]` |  |
| upstream.coder.envUseClusterAccessURL | bool | `true` |  |
| upstream.coder.image.repo | string | `"registry1.dso.mil/ironbank/coder/coder-enterprise/coder-service-2"` |  |
| upstream.coder.image.tag | string | `"2.22.1"` |  |
| upstream.coder.image.pullPolicy | string | `"IfNotPresent"` |  |
| upstream.coder.image.pullSecrets[0].name | string | `"private-registry"` |  |
| upstream.coder.initContainers | list | `[]` |  |
| upstream.coder.annotations | object | `{}` |  |
| upstream.coder.labels | object | `{}` |  |
| upstream.coder.podAnnotations | object | `{}` |  |
| upstream.coder.podLabels | object | `{}` |  |
| upstream.coder.serviceAccount.workspacePerms | bool | `true` |  |
| upstream.coder.serviceAccount.enableDeployments | bool | `true` |  |
| upstream.coder.serviceAccount.extraRules | list | `[]` |  |
| upstream.coder.serviceAccount.annotations | object | `{}` |  |
| upstream.coder.serviceAccount.name | string | `"coder"` |  |
| upstream.coder.serviceAccount.disableCreate | bool | `false` |  |
| upstream.coder.securityContext.runAsNonRoot | bool | `true` |  |
| upstream.coder.securityContext.runAsUser | int | `1000` |  |
| upstream.coder.securityContext.runAsGroup | int | `1000` |  |
| upstream.coder.securityContext.readOnlyRootFilesystem | string | `nil` |  |
| upstream.coder.securityContext.seccompProfile.type | string | `"RuntimeDefault"` |  |
| upstream.coder.securityContext.allowPrivilegeEscalation | bool | `false` |  |
| upstream.coder.volumes | list | `[]` |  |
| upstream.coder.volumeMounts | list | `[]` |  |
| upstream.coder.tls.secretNames | list | `[]` |  |
| upstream.coder.replicaCount | int | `1` |  |
| upstream.coder.workspaceProxy | bool | `false` |  |
| upstream.coder.lifecycle | object | `{}` |  |
| upstream.coder.resources | object | `{}` |  |
| upstream.coder.certs.secrets | list | `[]` |  |
| upstream.coder.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].podAffinityTerm.labelSelector.matchExpressions[0].key | string | `"app.kubernetes.io/instance"` |  |
| upstream.coder.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].podAffinityTerm.labelSelector.matchExpressions[0].operator | string | `"In"` |  |
| upstream.coder.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].podAffinityTerm.labelSelector.matchExpressions[0].values[0] | string | `"coder"` |  |
| upstream.coder.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].podAffinityTerm.topologyKey | string | `"kubernetes.io/hostname"` |  |
| upstream.coder.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].weight | int | `1` |  |
| upstream.coder.topologySpreadConstraints | string | `nil` |  |
| upstream.coder.tolerations | list | `[]` |  |
| upstream.coder.nodeSelector | object | `{}` |  |
| upstream.coder.service.enable | bool | `true` |  |
| upstream.coder.service.type | string | `"LoadBalancer"` |  |
| upstream.coder.service.sessionAffinity | string | `"None"` |  |
| upstream.coder.service.externalTrafficPolicy | string | `"Cluster"` |  |
| upstream.coder.service.loadBalancerIP | string | `""` |  |
| upstream.coder.service.loadBalancerClass | string | `""` |  |
| upstream.coder.service.annotations | object | `{}` |  |
| upstream.coder.service.httpNodePort | string | `""` |  |
| upstream.coder.service.httpsNodePort | string | `""` |  |
| upstream.coder.ingress.enable | bool | `false` |  |
| upstream.coder.ingress.className | string | `""` |  |
| upstream.coder.ingress.host | string | `""` |  |
| upstream.coder.ingress.wildcardHost | string | `""` |  |
| upstream.coder.ingress.annotations | object | `{}` |  |
| upstream.coder.ingress.tls.enable | bool | `false` |  |
| upstream.coder.ingress.tls.secretName | string | `""` |  |
| upstream.coder.ingress.tls.wildcardSecretName | string | `""` |  |
| upstream.coder.command[0] | string | `"/opt/coder"` |  |
| upstream.coder.commandArgs | list | `[]` |  |
| upstream.provisionerDaemon.pskSecretName | string | `""` |  |
| upstream.extraTemplates | string | `nil` |  |

## Contributing

Please see the [contributing guide](./CONTRIBUTING.md) if you are interested in contributing.

---

_This file is programatically generated using `helm-docs` and some BigBang-specific templates. The `gluon` repository has [instructions for regenerating package READMEs](https://repo1.dso.mil/big-bang/product/packages/gluon/-/blob/master/docs/bb-package-readme.md)._

