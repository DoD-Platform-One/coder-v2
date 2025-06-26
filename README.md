# coder

![Version: 2.22.1-bb.0](https://img.shields.io/badge/Version-2.22.1--bb.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 2.22.1](https://img.shields.io/badge/AppVersion-2.22.1-informational?style=flat-square)

Remote development environments on your infrastructure

**Homepage:** <https://github.com/coder/coder>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Coder Technologies, Inc. | <support@coder.com> | <https://coder.com/contact> |

## Source Code

* <https://github.com/coder/coder/tree/main/helm/coder>

## Requirements

Kubernetes: `>= 1.19.0-0`

| Repository | Name | Version |
|------------|------|---------|
| https://helm.coder.com/v2 | upstream(coder) | 2.22.1 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| domain | string | `"bigbang.dev"` |  |
| istio.coder.gateways[0] | string | `"istio-system/main"` |  |
| istio.coder.hosts[0] | string | `"coder.{{ .Values.domain }}"` |  |
| istio.enabled | bool | `false` |  |
| istio.hardened.customAuthorizationPolicies | list | `[]` |  |
| istio.hardened.customServiceEntries | list | `[]` |  |
| istio.hardened.enabled | bool | `false` |  |
| istio.hardened.outboundTrafficPolicyMode | string | `"REGISTRY_ONLY"` |  |
| monitoring.enabled | bool | `false` |  |
| monitoring.namespace | string | `"monitoring"` |  |
| networkPolicies.additionalPolicies | list | `[]` |  |
| networkPolicies.controlPlaneCidr | string | `"0.0.0.0/0"` |  |
| networkPolicies.enabled | bool | `false` |  |
| networkPolicies.ingressLabels.app | string | `"istio-ingressgateway"` |  |
| networkPolicies.ingressLabels.istio | string | `"ingressgateway"` |  |
| sso.enabled | bool | `false` |  |
| upstream.coder.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].podAffinityTerm.labelSelector.matchExpressions[0].key | string | `"app.kubernetes.io/instance"` |  |
| upstream.coder.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].podAffinityTerm.labelSelector.matchExpressions[0].operator | string | `"In"` |  |
| upstream.coder.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].podAffinityTerm.labelSelector.matchExpressions[0].values[0] | string | `"coder"` |  |
| upstream.coder.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].podAffinityTerm.topologyKey | string | `"kubernetes.io/hostname"` |  |
| upstream.coder.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].weight | int | `1` |  |
| upstream.coder.annotations | object | `{}` |  |
| upstream.coder.certs.secrets | list | `[]` |  |
| upstream.coder.commandArgs | list | `[]` |  |
| upstream.coder.command[0] | string | `"/opt/coder"` |  |
| upstream.coder.env | list | `[]` |  |
| upstream.coder.envFrom | list | `[]` |  |
| upstream.coder.envUseClusterAccessURL | bool | `true` |  |
| upstream.coder.image.pullPolicy | string | `"IfNotPresent"` |  |
| upstream.coder.image.pullSecrets[0].name | string | `"private-registry"` |  |
| upstream.coder.image.repo | string | `"registry1.dso.mil/ironbank/coder/coder-enterprise/coder-service-2"` |  |
| upstream.coder.image.tag | string | `"2.22.1"` |  |
| upstream.coder.ingress.annotations | object | `{}` |  |
| upstream.coder.ingress.className | string | `""` |  |
| upstream.coder.ingress.enable | bool | `false` |  |
| upstream.coder.ingress.host | string | `""` |  |
| upstream.coder.ingress.tls.enable | bool | `false` |  |
| upstream.coder.ingress.tls.secretName | string | `""` |  |
| upstream.coder.ingress.tls.wildcardSecretName | string | `""` |  |
| upstream.coder.ingress.wildcardHost | string | `""` |  |
| upstream.coder.initContainers | list | `[]` |  |
| upstream.coder.labels | object | `{}` |  |
| upstream.coder.lifecycle | object | `{}` |  |
| upstream.coder.nodeSelector | object | `{}` |  |
| upstream.coder.podAnnotations | object | `{}` |  |
| upstream.coder.podLabels | object | `{}` |  |
| upstream.coder.replicaCount | int | `1` |  |
| upstream.coder.resources | object | `{}` |  |
| upstream.coder.securityContext.allowPrivilegeEscalation | bool | `false` |  |
| upstream.coder.securityContext.readOnlyRootFilesystem | string | `nil` |  |
| upstream.coder.securityContext.runAsGroup | int | `1000` |  |
| upstream.coder.securityContext.runAsNonRoot | bool | `true` |  |
| upstream.coder.securityContext.runAsUser | int | `1000` |  |
| upstream.coder.securityContext.seccompProfile.type | string | `"RuntimeDefault"` |  |
| upstream.coder.service.annotations | object | `{}` |  |
| upstream.coder.service.enable | bool | `true` |  |
| upstream.coder.service.externalTrafficPolicy | string | `"Cluster"` |  |
| upstream.coder.service.httpNodePort | string | `""` |  |
| upstream.coder.service.httpsNodePort | string | `""` |  |
| upstream.coder.service.loadBalancerClass | string | `""` |  |
| upstream.coder.service.loadBalancerIP | string | `""` |  |
| upstream.coder.service.sessionAffinity | string | `"None"` |  |
| upstream.coder.service.type | string | `"LoadBalancer"` |  |
| upstream.coder.serviceAccount.annotations | object | `{}` |  |
| upstream.coder.serviceAccount.disableCreate | bool | `false` |  |
| upstream.coder.serviceAccount.enableDeployments | bool | `true` |  |
| upstream.coder.serviceAccount.extraRules | list | `[]` |  |
| upstream.coder.serviceAccount.name | string | `"coder"` |  |
| upstream.coder.serviceAccount.workspacePerms | bool | `true` |  |
| upstream.coder.tls.secretNames | list | `[]` |  |
| upstream.coder.tolerations | list | `[]` |  |
| upstream.coder.topologySpreadConstraints | string | `nil` |  |
| upstream.coder.volumeMounts | list | `[]` |  |
| upstream.coder.volumes | list | `[]` |  |
| upstream.coder.workspaceProxy | bool | `false` |  |
| upstream.extraTemplates | string | `nil` |  |
| upstream.provisionerDaemon.pskSecretName | string | `""` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
