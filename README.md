# coder

![Version: 2.20.3](https://img.shields.io/badge/Version-2.20.3-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 2.20.3](https://img.shields.io/badge/AppVersion-2.20.3-informational?style=flat-square)

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

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| coder | object | `{"affinity":{"podAntiAffinity":{"preferredDuringSchedulingIgnoredDuringExecution":[{"podAffinityTerm":{"labelSelector":{"matchExpressions":[{"key":"app.kubernetes.io/instance","operator":"In","values":["coder"]}]},"topologyKey":"kubernetes.io/hostname"},"weight":1}]}},"annotations":{},"certs":{"secrets":[]},"command":["/opt/coder"],"commandArgs":[],"env":[],"envFrom":[],"envUseClusterAccessURL":true,"image":{"pullPolicy":"IfNotPresent","pullSecrets":[{"name":"private-registry"}],"repo":"registry1.dso.mil/ironbank/coder/coder","tag":"2.20.3"},"ingress":{"annotations":{},"className":"","enable":false,"host":"","tls":{"enable":false,"secretName":"","wildcardSecretName":""},"wildcardHost":""},"initContainers":[],"labels":{},"lifecycle":{},"nodeSelector":{},"podAnnotations":{},"podLabels":{},"replicaCount":1,"resources":{},"securityContext":{"allowPrivilegeEscalation":false,"readOnlyRootFilesystem":null,"runAsGroup":1000,"runAsNonRoot":true,"runAsUser":1000,"seccompProfile":{"type":"RuntimeDefault"}},"service":{"annotations":{},"enable":true,"externalTrafficPolicy":"Cluster","httpNodePort":"","httpsNodePort":"","loadBalancerClass":"","loadBalancerIP":"","sessionAffinity":"None","type":"LoadBalancer"},"serviceAccount":{"annotations":{},"disableCreate":false,"enableDeployments":true,"extraRules":[],"name":"coder","workspacePerms":true},"tls":{"secretNames":[]},"tolerations":[],"topologySpreadConstraints":null,"volumeMounts":[],"volumes":[],"workspaceProxy":false}` | Primary configuration for `coder server`. |
| coder.env | list | `[]` | The environment variables to set for Coder. These can be used to configure all aspects of `coder server`. Please see `coder server --help` for information about what environment variables can be set. Note: The following environment variables are set by default and cannot be overridden: - CODER_HTTP_ADDRESS: set to 0.0.0.0:8080 and cannot be changed. - CODER_TLS_ADDRESS: set to 0.0.0.0:8443 if tls.secretName is not empty. - CODER_TLS_ENABLE: set if tls.secretName is not empty. - CODER_TLS_CERT_FILE: set if tls.secretName is not empty. - CODER_TLS_KEY_FILE: set if tls.secretName is not empty. - CODER_PROMETHEUS_ADDRESS: set to 0.0.0.0:2112 and cannot be changed.   Prometheus must still be enabled by setting CODER_PROMETHEUS_ENABLE. - KUBE_POD_IP - CODER_DERP_SERVER_RELAY_URL  We will additionally set CODER_ACCESS_URL if unset to the cluster service URL, unless coder.envUseClusterAccessURL is set to false. |
| coder.envFrom | list | `[]` | Secrets or ConfigMaps to use for Coder's environment variables. If you want one environment variable read from a secret, then use coder.env valueFrom. See the K8s docs for valueFrom here: https://kubernetes.io/docs/tasks/inject-data-application/distribute-credentials-secure/#define-container-environment-variables-using-secret-data  If setting CODER_ACCESS_URL in coder.envFrom, then you must set coder.envUseClusterAccessURL to false. |
| coder.envUseClusterAccessURL | bool | `true` | Determines whether the CODER_ACCESS_URL env is added to coder.env if it's not already set there. Set this to false if defining CODER_ACCESS_URL in coder.envFrom to avoid conflicts. |
| coder.image | object | `{"pullPolicy":"IfNotPresent","pullSecrets":[{"name":"private-registry"}],"repo":"registry1.dso.mil/ironbank/coder/coder","tag":"2.20.3"}` | The image to use for Coder. |
| coder.image.repo | string | `"registry1.dso.mil/ironbank/coder/coder"` | The repository of the image. |
| coder.image.tag | string | `"2.20.3"` | The tag of the image, defaults to {{.Chart.AppVersion}} if not set. If you're using the chart directly from git, the default app version will not work and you'll need to set this value. The helm chart helpfully fails quickly in this case. |
| coder.image.pullPolicy | string | `"IfNotPresent"` | The pull policy to use for the image. See: https://kubernetes.io/docs/concepts/containers/images/#image-pull-policy |
| coder.image.pullSecrets | list | `[{"name":"private-registry"}]` | The secrets used for pulling the Coder image from a private registry. |
| coder.initContainers | list | `[]` | Init containers for the deployment. See: https://kubernetes.io/docs/concepts/workloads/pods/init-containers/ |
| coder.annotations | object | `{}` | The Deployment annotations. See: https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/ |
| coder.labels | object | `{}` | The Deployment labels. See: https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/ |
| coder.podAnnotations | object | `{}` | The Coder pod annotations. See: https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/ |
| coder.podLabels | object | `{}` | The Coder pod labels. See: https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/ |
| coder.serviceAccount | object | `{"annotations":{},"disableCreate":false,"enableDeployments":true,"extraRules":[],"name":"coder","workspacePerms":true}` | Configuration for the automatically created service account. Creation of the service account cannot be disabled. |
| coder.serviceAccount.workspacePerms | bool | `true` | Whether or not to grant the coder service account permissions to manage workspaces. This includes permission to manage pods and persistent volume claims in the deployment namespace.  It is recommended to keep this on if you are using Kubernetes templates within Coder. |
| coder.serviceAccount.enableDeployments | bool | `true` | Provides the service account permission to manage Kubernetes deployments. Depends on workspacePerms. |
| coder.serviceAccount.extraRules | list | `[]` | Additional permissions added to the SA role. Depends on workspacePerms. |
| coder.serviceAccount.annotations | object | `{}` | The Coder service account annotations. |
| coder.serviceAccount.name | string | `"coder"` | The service account name |
| coder.serviceAccount.disableCreate | bool | `false` | Whether to create the service account or use existing service account. |
| coder.securityContext | object | `{"allowPrivilegeEscalation":false,"readOnlyRootFilesystem":null,"runAsGroup":1000,"runAsNonRoot":true,"runAsUser":1000,"seccompProfile":{"type":"RuntimeDefault"}}` | Fields related to the container's security context (as opposed to the pod). Some fields are also present in the pod security context, in which case these values will take precedence. |
| coder.securityContext.runAsNonRoot | bool | `true` | Requires that the coder container runs as an unprivileged user. If setting runAsUser to 0 (root), this will need to be set to false. |
| coder.securityContext.runAsUser | int | `1000` | Sets the user id of the container. For security reasons, we recommend using a non-root user. |
| coder.securityContext.runAsGroup | int | `1000` | Sets the group id of the container. For security reasons, we recommend using a non-root group. |
| coder.securityContext.readOnlyRootFilesystem | string | `nil` | Mounts the container's root filesystem as read-only. |
| coder.securityContext.seccompProfile | object | `{"type":"RuntimeDefault"}` | Sets the seccomp profile for the coder container. |
| coder.securityContext.allowPrivilegeEscalation | bool | `false` | Controls whether the container can gain additional privileges, such as escalating to root. It is recommended to leave this setting disabled in production. |
| coder.volumes | list | `[]` | A list of extra volumes to add to the Coder pod. |
| coder.volumeMounts | list | `[]` | A list of extra volume mounts to add to the Coder pod. |
| coder.tls | object | `{"secretNames":[]}` | The TLS configuration for Coder. |
| coder.tls.secretNames | list | `[]` | A list of TLS server certificate secrets to mount into the Coder pod. The secrets should exist in the same namespace as the Helm deployment and should be of type "kubernetes.io/tls". The secrets will be automatically mounted into the pod if specified, and the correct "CODER_TLS_*" environment variables will be set for you. |
| coder.replicaCount | int | `1` | The number of Kubernetes deployment replicas. This should only be increased if High Availability is enabled.  This is an Enterprise feature. Contact sales@coder.com. |
| coder.workspaceProxy | bool | `false` | Whether or not this deployment of Coder is a Coder Workspace Proxy. Workspace Proxies reduce the latency between the user and their workspace for web connections (workspace apps and web terminal) and proxied connections from the CLI. Workspace Proxies are optional and only recommended for geographically sparse teams.  Make sure you set CODER_PRIMARY_ACCESS_URL and CODER_PROXY_SESSION_TOKEN in the environment below. You can get a proxy token using the CLI:   coder wsproxy create \     --name "proxy-name" \     --display-name "Proxy Name" \     --icon "/emojis/xyz.png"  This is an Enterprise feature. Contact sales@coder.com Docs: https://coder.com/docs/admin/workspace-proxies |
| coder.lifecycle | object | `{}` | container lifecycle handlers for the Coder container, allowing for lifecycle events such as postStart and preStop events See: https://kubernetes.io/docs/tasks/configure-pod-container/attach-handler-lifecycle-event/ |
| coder.resources | object | `{}` | The resources to request for Coder. These are optional and are not set by default. |
| coder.certs | object | `{"secrets":[]}` | CA bundles to mount inside the Coder pod. |
| coder.certs.secrets | list | `[]` | A list of CA bundle secrets to mount into the Coder pod. The secrets should exist in the same namespace as the Helm deployment.  The given key in each secret is mounted at `/etc/ssl/certs/{secret_name}.crt`. |
| coder.affinity | object | `{"podAntiAffinity":{"preferredDuringSchedulingIgnoredDuringExecution":[{"podAffinityTerm":{"labelSelector":{"matchExpressions":[{"key":"app.kubernetes.io/instance","operator":"In","values":["coder"]}]},"topologyKey":"kubernetes.io/hostname"},"weight":1}]}}` | Allows specifying an affinity rule for the `coder` deployment. The default rule prefers to schedule coder pods on different nodes, which is only applicable if coder.replicaCount is greater than 1. |
| coder.tolerations | list | `[]` | Tolerations for tainted nodes. See: https://kubernetes.io/docs/concepts/configuration/taint-and-toleration/ |
| coder.nodeSelector | object | `{}` | Node labels for constraining coder pods to nodes. See: https://kubernetes.io/docs/concepts/configuration/assign-pod-node/#nodeselector |
| coder.service | object | `{"annotations":{},"enable":true,"externalTrafficPolicy":"Cluster","httpNodePort":"","httpsNodePort":"","loadBalancerClass":"","loadBalancerIP":"","sessionAffinity":"None","type":"LoadBalancer"}` | The Service object to expose for Coder. |
| coder.service.enable | bool | `true` | Whether to create the Service object. |
| coder.service.type | string | `"LoadBalancer"` | The type of service to expose. See: https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types |
| coder.service.sessionAffinity | string | `"None"` | Must be set to ClientIP or None AWS ELB does not support session stickiness based on ClientIP, so you must set this to None. The error message you might see: "Unsupported load balancer affinity: ClientIP" https://kubernetes.io/docs/reference/networking/virtual-ips/#session-affinity |
| coder.service.externalTrafficPolicy | string | `"Cluster"` | The external traffic policy to use. You may need to change this to "Local" to preserve the source IP address in some situations. https://kubernetes.io/docs/tasks/access-application-cluster/create-external-load-balancer/#preserving-the-client-source-ip |
| coder.service.loadBalancerIP | string | `""` | The IP address of the LoadBalancer. If not specified, a new IP will be generated each time the load balancer is recreated. It is recommended to manually create a static IP address in your cloud and specify it here in production to avoid accidental IP address changes. |
| coder.service.loadBalancerClass | string | `""` | The class name of the LoadBalancer. See: https://kubernetes.io/docs/concepts/services-networking/service/#load-balancer-class |
| coder.service.annotations | object | `{}` | The service annotations. See: https://kubernetes.io/docs/concepts/services-networking/service/#internal-load-balancer |
| coder.service.httpNodePort | string | `""` | Enabled if coder.service.type is set to NodePort or LoadBalancer. If not set, Kubernetes will allocate a port from the default range, 30000-32767. |
| coder.service.httpsNodePort | string | `""` | Enabled if coder.service.type is set to NodePort or LoadBalancer. If not set, Kubernetes will allocate a port from the default range, 30000-32767. |
| coder.ingress | object | `{"annotations":{},"className":"","enable":false,"host":"","tls":{"enable":false,"secretName":"","wildcardSecretName":""},"wildcardHost":""}` | The Ingress object to expose for Coder. |
| coder.ingress.enable | bool | `false` | Whether to create the Ingress object. If using an Ingress, we recommend not specifying coder.tls.secretNames as the Ingress will handle TLS termination. |
| coder.ingress.className | string | `""` | The name of the Ingress class to use. |
| coder.ingress.host | string | `""` | The hostname to match on. Be sure to also set CODER_ACCESS_URL within coder.env[] |
| coder.ingress.wildcardHost | string | `""` | The wildcard hostname to match on. Should be in the form "*.example.com" or "*-suffix.example.com". If you are using a suffix after the wildcard, the suffix will be stripped from the created ingress to ensure that it is a legal ingress host. Optional if not using applications over subdomains. Be sure to also set CODER_WILDCARD_ACCESS_URL within coder.env[] |
| coder.ingress.annotations | object | `{}` | The ingress annotations. |
| coder.ingress.tls | object | `{"enable":false,"secretName":"","wildcardSecretName":""}` | The TLS configuration to use for the Ingress. |
| coder.ingress.tls.enable | bool | `false` | Whether to enable TLS on the Ingress. |
| coder.ingress.tls.secretName | string | `""` | The name of the TLS secret to use. |
| coder.ingress.tls.wildcardSecretName | string | `""` | The name of the TLS secret to use for the wildcard host. |
| coder.command | list | `["/opt/coder"]` | The command to use when running the Coder container. Used for customizing the location of the `coder` binary in your image. |
| coder.commandArgs | list | `[]` | Set arguments for the entrypoint command of the Coder pod. |
| provisionerDaemon | object | `{"pskSecretName":""}` | Configuration for external provisioner daemons.  This is an Enterprise feature. Contact sales@coder.com. |
| provisionerDaemon.pskSecretName | string | `""` | The name of the Kubernetes secret that contains the Pre-Shared Key (PSK) to use to authenticate external provisioner daemons with Coder.  The secret must be in the same namespace as the Helm deployment, and contain an item called "psk" which contains the pre-shared key. |
| extraTemplates | string | `nil` | Array of extra objects to deploy with the release. Strings are evaluated as a template and can use template expansions and functions. All other objects are used as yaml. |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
# coder-provisioner

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.1.0](https://img.shields.io/badge/AppVersion-0.1.0-informational?style=flat-square)

External provisioner daemon for Coder. This is an Enterprise feature; contact sales@coder.com.

**Homepage:** <https://github.com/coder/coder>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Coder Technologies, Inc. | <support@coder.com> | <https://coder.com/contact> |

## Source Code

* <https://github.com/coder/coder/tree/main/helm/provisioner>

## Requirements

Kubernetes: `>= 1.19.0-0`

| Repository | Name | Version |
|------------|------|---------|
| file://../libcoder | libcoder | 0.1.0 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| coder | object | `{"affinity":{},"annotations":{},"certs":{"secrets":[]},"command":["/opt/coder"],"commandArgs":[],"env":[],"image":{"pullPolicy":"IfNotPresent","pullSecrets":[{"name":"private-registry"}],"repo":"registry1.dso.mil/ironbank/coder/coder","tag":"2.20.3"},"initContainers":[],"labels":{},"lifecycle":{},"nodeSelector":{},"podAnnotations":{},"podLabels":{},"replicaCount":1,"resources":{},"securityContext":{"allowPrivilegeEscalation":false,"readOnlyRootFilesystem":null,"runAsGroup":1000,"runAsNonRoot":true,"runAsUser":1000,"seccompProfile":{"type":"RuntimeDefault"}},"serviceAccount":{"annotations":{},"disableCreate":false,"enableDeployments":true,"name":"coder-provisioner","workspacePerms":true},"tolerations":{},"volumeMounts":[],"volumes":[]}` | Common configuration options. |
| coder.env | list | `[]` | The environment variables to set. These can be used to configure all aspects of Coder provisioner daemon. Please see `coder provisionerd start --help for information about what environment variables can be set. Note: The following environment variables are set by default and cannot be overridden: - CODER_PROMETHEUS_ADDRESS: set to 0.0.0.0:2112 and cannot be changed.   Prometheus must still be enabled by setting CODER_PROMETHEUS_ENABLE.  We will additionally set CODER_URL, if unset, to the cluster service URL. |
| coder.image | object | `{"pullPolicy":"IfNotPresent","pullSecrets":[{"name":"private-registry"}],"repo":"registry1.dso.mil/ironbank/coder/coder","tag":"2.20.3"}` | The image to use for Coder provisioner daemon. |
| coder.image.repo | string | `"registry1.dso.mil/ironbank/coder/coder"` | The repository of the image. |
| coder.image.tag | string | `"2.20.3"` | The tag of the image, defaults to {{.Chart.AppVersion}} if not set. If you're using the chart directly from git, the default app version will not work and you'll need to set this value. The helm chart helpfully fails quickly in this case. |
| coder.image.pullPolicy | string | `"IfNotPresent"` | The pull policy to use for the image. See: https://kubernetes.io/docs/concepts/containers/images/#image-pull-policy |
| coder.image.pullSecrets | list | `[{"name":"private-registry"}]` | The secrets used for pulling the Coder image from a private registry. |
| coder.initContainers | list | `[]` | Init containers for the deployment. See: https://kubernetes.io/docs/concepts/workloads/pods/init-containers/ |
| coder.annotations | object | `{}` | The Deployment annotations. See: https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/ |
| coder.labels | object | `{}` | The Deployment labels. See: https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/ |
| coder.podAnnotations | object | `{}` | The Coder pod annotations. See: https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/ |
| coder.podLabels | object | `{}` | The Coder pod labels. See: https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/ |
| coder.serviceAccount | object | `{"annotations":{},"disableCreate":false,"enableDeployments":true,"name":"coder-provisioner","workspacePerms":true}` | Configuration for the automatically created service account. Creation of the service account cannot be disabled. |
| coder.serviceAccount.workspacePerms | bool | `true` | Whether or not to grant the service account permissions to manage workspaces. This includes permission to manage pods and persistent volume claims in the deployment namespace.  It is recommended to keep this on if you are using Kubernetes templates within Coder. |
| coder.serviceAccount.enableDeployments | bool | `true` | Provides the service account permission to manage Kubernetes deployments. |
| coder.serviceAccount.annotations | object | `{}` | The Coder service account annotations. |
| coder.serviceAccount.name | string | `"coder-provisioner"` | The service account name |
| coder.serviceAccount.disableCreate | bool | `false` | Whether to create the service account or use existing service account. |
| coder.securityContext | object | `{"allowPrivilegeEscalation":false,"readOnlyRootFilesystem":null,"runAsGroup":1000,"runAsNonRoot":true,"runAsUser":1000,"seccompProfile":{"type":"RuntimeDefault"}}` | Fields related to the container's security context (as opposed to the pod). Some fields are also present in the pod security context, in which case these values will take precedence. |
| coder.securityContext.runAsNonRoot | bool | `true` | Requires that the coder container runs as an unprivileged user. If setting runAsUser to 0 (root), this will need to be set to false. |
| coder.securityContext.runAsUser | int | `1000` | Sets the user id of the container. For security reasons, we recommend using a non-root user. |
| coder.securityContext.runAsGroup | int | `1000` | Sets the group id of the container. For security reasons, we recommend using a non-root group. |
| coder.securityContext.readOnlyRootFilesystem | string | `nil` | Mounts the container's root filesystem as read-only. |
| coder.securityContext.seccompProfile | object | `{"type":"RuntimeDefault"}` | Sets the seccomp profile for the coder container. |
| coder.securityContext.allowPrivilegeEscalation | bool | `false` | Controls whether the container can gain additional privileges, such as escalating to root. It is recommended to leave this setting disabled in production. |
| coder.volumes | list | `[]` | A list of extra volumes to add to the Coder provisioner daemon pod. |
| coder.volumeMounts | list | `[]` | A list of extra volume mounts to add to the Coder provisioner daemon pod. |
| coder.replicaCount | int | `1` | The number of Kubernetes deployment replicas. This should only be increased if High Availability is enabled.  This is an Enterprise feature. Contact sales@coder.com. |
| coder.lifecycle | object | `{}` | container lifecycle handlers for the Coder container, allowing for lifecycle events such as postStart and preStop events See: https://kubernetes.io/docs/tasks/configure-pod-container/attach-handler-lifecycle-event/ |
| coder.resources | object | `{}` | The resources to request for Coder. These are optional and are not set by default. |
| coder.certs | object | `{"secrets":[]}` | CA bundles to mount inside the Coder pod. |
| coder.certs.secrets | list | `[]` | A list of CA bundle secrets to mount into the pod. The secrets should exist in the same namespace as the Helm deployment.  The given key in each secret is mounted at `/etc/ssl/certs/{secret_name}.crt`. |
| coder.affinity | object | `{}` | Allows specifying an affinity rule for the deployment. |
| coder.tolerations | object | `{}` | Tolerations for tainted nodes. See: https://kubernetes.io/docs/concepts/configuration/taint-and-toleration/ |
| coder.nodeSelector | object | `{}` | Node labels for constraining coder pods to nodes. See: https://kubernetes.io/docs/concepts/configuration/assign-pod-node/#nodeselector |
| coder.command | list | `["/opt/coder"]` | The command to use when running the container. Used for customizing the location of the `coder` binary in your image. |
| coder.commandArgs | list | `[]` | Set arguments for the entrypoint command of the Coder pod. |
| provisionerDaemon | object | `{"keySecretKey":"key","keySecretName":"","pskSecretName":"coder-provisioner-psk","tags":{},"terminationGracePeriodSeconds":600}` | Provisioner Daemon configuration options |
| provisionerDaemon.pskSecretName | string | `"coder-provisioner-psk"` | The name of the Kubernetes secret that contains the Pre-Shared Key (PSK) to use to authenticate with Coder. The secret must be in the same namespace as the Helm deployment, and contain an item called "psk" which contains the pre-shared key. NOTE: We no longer recommend using PSKs. Please consider using provisioner keys instead. They have a number of benefits, including the ability to rotate them easily. |
| provisionerDaemon.keySecretName | string | `""` | The name of the Kubernetes secret that contains a provisioner key to use to authenticate with Coder. See: https://coder.com/docs/admin/provisioners#authentication NOTE: it is not permitted to specify both provisionerDaemon.keySecretName and provisionerDaemon.pskSecretName. An exception is made for the purposes of backwards-compatibility: if provisionerDaemon.pskSecretName is unchanged from the default value and provisionerDaemon.keySecretName is set, then provisionerDaemon.keySecretName and provisionerDaemon.keySecretKey will take precedence over provisionerDaemon.pskSecretName. |
| provisionerDaemon.keySecretKey | string | `"key"` | The key of the Kubernetes secret specified in provisionerDaemon.keySecretName that contains the provisioner key. Defaults to "key". |
| provisionerDaemon.tags | object | `{}` | If using a PSK, specify the set of provisioner job tags for which this provisioner daemon is responsible. See: https://coder.com/docs/admin/provisioners#provisioner-tags NOTE: it is not permitted to specify both provisionerDaemon.tags and provsionerDaemon.keySecretName. |
| provisionerDaemon.terminationGracePeriodSeconds | int | `600` | Time in seconds that Kubernetes should wait before forcibly terminating the provisioner daemon.  You should set this to be longer than your longest expected build time so that redeployments do not interrupt builds in progress. |
| extraTemplates | string | `nil` | Array of extra objects to deploy with the release. Strings are evaluated as a template and can use template expansions and functions. All other objects are used as yaml. |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
