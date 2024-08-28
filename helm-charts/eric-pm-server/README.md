
## Configuration

The following tables lists the configurable parameters of the PM Server chart and their default values.

Parameter | Description | Default
--------- | ----------- | -------
`affinity.podAntiAffinity` | Define inter-pod anti-affinity policy to kubernetes scheduler. Supported values are "hard" and "soft". | `"hard"`
`annotations` | List of additional key/value pairs of annotations appended to every resource object created within PM Server. | `{}`
`appArmorProfile.eric-pm-configmap-reload.localhostProfile` | The 'localhost' profile requires a profile name to be provided. The name of the local appArmor profile to be used for eric-pm-configmap-reload container. | `""`
`appArmorProfile.eric-pm-configmap-reload.type` | Configuration of AppArmor profile type for eric-pm-configmap-reload container. Supported values are unconfined, runtime/default, localhost and "". | `""`
`appArmorProfile.eric-pm-exporter.localhostProfile` | The 'localhost' profile requires a profile name to be provided. The name of the local appArmor profile to be used for eric-pm-exporter container. | `""`
`appArmorProfile.eric-pm-exporter.type` | Configuration of AppArmor profile type for eric-pm-exporter container. Supported values are unconfined, runtime/default, localhost and "". | `""`
`appArmorProfile.eric-pm-reverseproxy.localhostProfile` | The 'localhost' profile requires a profile name to be provided. The name of the local appArmor profile to be used for eric-pm-reverseproxy container. | `""`
`appArmorProfile.eric-pm-reverseproxy.type` | Configuration of AppArmor profile type for eric-pm-reverseproxy container. Supported values are unconfined, runtime/default, localhost and "". | `""`
`appArmorProfile.eric-pm-server.localhostProfile` | The 'localhost' profile requires a profile name to be provided. The name of the local appArmor profile to be used for eric-pm-server container. | `""`
`appArmorProfile.eric-pm-server.type` | Configuration of AppArmor profile type for eric-pm-server container. Supported values are unconfined, runtime/default, localhost and "". | `""`
`appArmorProfile.logshipper.localhostProfile` | The 'localhost' profile requires a profile name to be provided. The name of the local appArmor profile to be used for logshipper container. | `""`
`appArmorProfile.logshipper.type` | Configuration of AppArmor profile type for logshipper container. Supported values are unconfined, runtime/default, localhost and "". | `""`
`appArmorProfile.localhostProfile` | The 'localhost' profile requires a profile name to be provided. The name of the local appArmor profile to be used. The setting applies to all container when the container specific parameter is omitted. | `""`
`appArmorProfile.type` | Configuration of AppArmor profile type. The setting applies to all container when the container specific parameter is omitted. Supported values are unconfined, runtime/default, localhost and "". | `""`
`config.certm_tls` | TLS configuration for certm. Multiple endpoints can be configured | `[]`
`config.certm_tls.clientCertName` | Same name as used in the CLI action `keystore asymmetric-keys install-asymmetric-key-pkcs12 name <clientKeyName> certificate-name <clientCertName> ...` | `commented out`
`config.certm_tls.clientKeyName` | Same name as used in the CLI action `keystore asymmetric-keys install-asymmetric-key-pkcs12 name <clientKeyName> certificate-name <clientCertName> ...` | `commented out`
`config.certm_tls.name` | Name of the endpoint | `commented out`
`config.certm_tls.trustedCertName` | Same name as used in the CLI action `install-certificate-pem name <trustedCertName> pem ...` | `commented out`
`config.recording_rules` | Define recording rules | `{}`
`config.remote_write` | Define remote write endpoints | `[]`
`global.networkPolicy.enabled` | Global configuration parameter to enable/disable Network Policy for the HTTP(s) and the metrics port of PM Server. Both global and service-level parameters have to be set to `true` for the Network Policy to be deployed. When enabled, the metrics ports of PM Server allow ingress from the PM Bulk Reporter, set via `.Values.security.tls.pmBulkReporter.serviceName`. Services which want to access the HTTP(s) port of PM Service, require the label `eric-pm-service-access: "true"`. | `false`
`global.pullSecret` | PM Server's global registry pull secret  | `commented out`
`global.registry.pullSecret` | (deprecated) PM Server's global registry pull secret  | `commented out`
`global.registry.url`| PM Server's image global registry. |armdocker.rnd.ericsson.se
`global.timezone`| PM Server's timezone setting | `UTC`
`global.security.policyBinding.create` | Creates Pod Security Policy (PSP) | `commented out`
`global.security.policyReferenceMap` | Creates Reference Map for Pod Security Policy (PSP) | `commented out`
`global.security.tls.enabled` | PM Server TLS support | `true`
`global.nodeSelector` | Node labels for PM server pod assignment. | `{}`
`imageCredentials.logshipper.registry.url`| The Log shipper docker image repository | `""`
`imageCredentials.logshipper.registry.imagePullPolicy`| The Log Shipper image pull policy | `""`
`imageCredentials.logshipper.repoPath`| The path to the Log Shipper repository within the above url | `proj-adp-log-released`
`imageCredentials.pullPolicy`| PM Server container images pull Policy. |IfNotPresent
`imageCredentials.pullSecret` | PM Server's registry pull secret  | `commented out`
`imageCredentials.registry.url`| Overrides global registry url. |""
`imageCredentials.repoPath`| PM Server's image path. |proj-common-assets-cd/monitoring/pm
`logShipper.logLevel`| log level of log shipper, when enabled | `warning`
`logShipper.output.logTransformer.host`| Log Shipper, Log transformer host | `eric-log-transformer`
`logShipper.storage.size`| Size of the shared volume | `1Gi`
`logShipper.storage.medium` | Which storage medium to use. Empty defaults to memory based storage. Value Ephemeral is supported to use ephemeral storage | `Memory`
`logShipper.input.files.enabled` | Enable or disable input | `false`
`logShipper.input.files.paths` | List of files to ship relative from logShipper.storage.path. Wildcards are supported, but not recommended to use | `[]`
`networkPolicy.enabled`| Enable creation of NetworkPolicy resources. | `false`
`labels` | List of key/value pairs of labels appended to every resource object created in PM Server. | `{}`
`podDisruptionBudget.minAvailable` | Minimum available pods | 0
`rbac.appMonitoring.configFileCreate`| Create Config file from ConfigMap template for Application Monitoring. | `true`
`rbac.appMonitoring.enabled`| Enables RBAC for single Application Monitoring. | `false`
`resources.eric-pm-configmap-reload.limits.cpu`| The maximum amount of CPU allowed per instance for configmapReload. | `200m`
`resources.eric-pm-configmap-reload.limits.memory`| The maximum amount of memory allowed per instance for configmapReload. | `32Mi`
`resources.eric-pm-configmap-reload.limits.ephemeral-storage`| The maximum amount of ephemeral-storage allowed per instance for configmapReload. | `""`
`resources.eric-pm-configmap-reload.requests.cpu`| The requested amount of CPU per instance for configmapReload. | `100m`
`resources.eric-pm-configmap-reload.requests.memory`| The requested amount of memory per instance for configmapReload. | `8Mi`
`resources.eric-pm-configmap-reload.requests.ephemeral-storage`| The requested amount of ephemeral-storage per instance for configmapReload. | `""`
`resources.eric-pm-exporter.limits.cpu`| The maximum amount of CPU allowed per instance for eric-pm-exporter. | `200m`
`resources.eric-pm-exporter.limits.memory`| The maximum amount of memory allowed per instance for eric-pm-exporter. | `32Mi`
`resources.eric-pm-exporter.limits.ephemeral-storage`| The maximum amount of ephemeral-storage allowed per instance for eric-pm-exporter. | `""`
`resources.eric-pm-exporter.requests.cpu`| The requested amount of CPU per instance for eric-pm-exporter. | `100m`
`resources.eric-pm-exporter.requests.memory`| The requested amount of memory per instance for eric-pm-exporter. | `8Mi`
`resources.eric-pm-exporter.requests.ephemeral-storage`| The requested amount of ephemeral-storage per instance for eric-pm-exporter. | `""`
`resources.logshipper.limits.cpu`| The maximum amount of CPU allowed per instance for logshipper. | `100m`
`resources.logshipper.limits.memory`| The maximum amount of memory allowed per instance for logshipper. | `100Mi`
`resources.logshipper.limits.ephemeral-storage`| The maximum amount of ephemeral-storage allowed per instance for logshipper. | `""`
`resources.logshipper.requests.cpu`| The requested amount of CPU per instance for logshipper. | `50m`
`resources.logshipper.requests.memory`| The requested amount of memory per instance for logshipper. | `50Mi`
`resources.logshipper.requests.ephemeral-storage`| The requested amount of ephemeral-storage per instance for logshipper. | `""`
`resources.eric-pm-reverseproxy.limits.cpu`| The maximum amount of CPU allowed per instance for reverseProxy. | `2`
`resources.eric-pm-reverseproxy.limits.memory`| The maximum amount of memory allowed per instance for reverseProxy. | `64Mi`
`resources.eric-pm-reverseproxy.limits.ephemeral-storage`| The maximum amount of ephemeral-storage allowed per instance for eric-pm-reverseproxy. | `""`
`resources.eric-pm-reverseproxy.requests.cpu`| The requested amount of CPU per instance for reverseProxy. | `100m`
`resources.eric-pm-reverseproxy.requests.memory`| The requested amount of memory per instance for reverseProxy. | `32Mi`
`resources.eric-pm-reverseproxy.requests.ephemeral-storage`| The requested amount of ephemeral-storage per instance for eric-pm-reverseproxy. | `""`
`resources.eric-pm-server.limits.cpu`| The maximum amount of CPU allowed per instance for the PM Service. | `2`
`resources.eric-pm-server.limits.memory`| The maximum amount of memory allowed per instance for the PM Service. | `2048Mi`
`resources.eric-pm-server.limits.ephemeral-storage`| The maximum amount of ephemeral-storage allowed per instance for the PM Service. | `8Gi`
`resources.eric-pm-server.requests.cpu`| The requested amount of CPU per instance for the PM Service. | `250m`
`resources.eric-pm-server.requests.memory`| The requested amount of memory per instance for the PM Service.| `512Mi`
`resources.eric-pm-server.requests.ephemeral-storage`| The requested amount of ephemeral-storage per instance for the PM Service.| `512Mi`
`seccompProfile.eric-pm-configmap-reload.localhostProfile`| The 'Localhost' seccomp profile requires a profile name to be provided. The name of the local seccomp profile to be used for eric-pm-configmap-reload.| `""`
`seccompProfile.eric-pm-configmap-reload.type`| Configuration of seccomp profile type for eric-pm-configmap-reload. It overrides pod level configuration.| `""`
`seccompProfile.eric-pm-exporter.localhostProfile`| The 'Localhost' seccomp profile requires a profile name to be provided. The name of the local seccomp profile to be used for eric-pm-exporter.| `""`
`seccompProfile.eric-pm-exporter.type`| Configuration of seccomp profile type for eric-pm-exporter. It overrides pod level configuration.| `""`
`seccompProfile.eric-pm-reverseproxy.localhostProfile`| The 'Localhost' seccomp profile requires a profile name to be provided. The name of the local seccomp profile to be used for eric-pm-reverseproxy.| `""`
`seccompProfile.eric-pm-reverseproxy.type`| Configuration of seccomp profile type for eric-pm-reverseproxy. It overrides pod level configuration.| `""`
`seccompProfile.eric-pm-server.localhostProfile`| The 'Localhost' seccomp profile requires a profile name to be provided. The name of the local seccomp profile to be used for eric-pm-server.| `""`
`seccompProfile.eric-pm-server.type`| Configuration of seccomp profile type for eric-pm-server. It overrides pod level configuration.| `""`
`seccompProfile.logshipper.localhostProfile`| The 'Localhost' seccomp profile requires a profile name to be provided. The name of the local seccomp profile to be used for logshipper.| `""`
`seccompProfile.logshipper.type`| Configuration of seccomp profile type for logshipper. It overrides pod level configuration.| `""`
`seccompProfile.localhostProfile`| The 'Localhost' seccomp profile requires a profile name to be provided. The name of the local seccomp profile to be used for pod.| `""`
`seccompProfile.type`| Configuration of seccomp profile type for pod. The setting applies to all container when the container specific parameter is omitted.| `""`
`server.baseURL`| The external url at which the server can be accessed. | `""`
`server.configMapOverrideName`| PM Server ConfigMap override where full-name is `{{.Values.server.configMapOverrideName}}` and setting this value will prevent the default server ConfigMap from being generated. | `""`
`server.extraArgs`| Additional PM Server container arguments. | `{}`
`server.extraHostPathMounts`| Additional PM Server hostPath mounts. | `[]`
`server.extraSecretMounts`| Additional PM Server secret mounts. | `[]`
`server.extraConfigmapMounts`| Additional PM Server configmap mounts(for rules), an alpha feature. | []
`serverFiles.prometheus.yml` | PM Server scrape configuration. | `Kubernetes SD Endpoints`
`server.name`| PM Server container name. | `server`
`server.nodeSelector`| To be deprecated soon. Node labels for Prometheus server pod assignment. | `{}`
`server.persistentVolume.accessModes`| PM Server data Persistent Volume access modes. | `[ReadWriteOnce]`
`server.persistentVolume.annotations` | PM Server data Persistent Volume annotations. | `{}`
`server.persistentVolume.enabled`| If true, PM Server will create a Persistent Volume Claim. If set to false, with POD restarts & helm upgrades PM data will be erased/wiped off. | `false`
`server.persistentVolume.mountPath`| PM Server data Persistent Volume mount root path. | `/data`
`server.persistentVolume.size`| PM Server data Persistent Volume size. | `8Gi`
`server.persistentVolume.storageClass` | PM Server data Persistent Volume Storage Class | `commented out`
`server.persistentVolume.storageConnectivity` | The connectivity of the storage, either local or networked. | `networked`
`server.persistentVolume.subPath`| Subdirectory of PM Server data Persistent Volume to mount. | `""`
`server.podAnnotations` | Annotations to be added to PM Server pods. | `{}`
`server.prefixURL`| The prefix url at which the server can be accessed. | `""`
`server.replicaCount`| Desired number of PM Server pods. | `1`
`server.retention`| Determins how long data will be kept on the persistent volume. A time duration can be specified in different units where the most useful in in this case are (h)ours, (d)ays or (w)eeks. The prometheus default is 15d. | `""`
`server.serviceAccountName`| Service account name for server to use. | `default`
`server.service.annotations` | Annotations for PM Server service. | `{}`
`server.service.httpPort`| The PM Server port for clear-text based query traffic. | `9090`
`server.service.httpsPort`| The PM Server port for TLS based query traffic. | `9089`
`server.service.labels` | Labels for PM Server service. | `{}`
`server.tolerations`| Node taints to tolerate (requires Kubernetes >=1.6). | `[]`
`service.endpoints.scrapeTargets.tls.enforced`| This options applies to the default server ConfigMap for application monitoring. The option controls if both cleartext and TLS scrape targets or only TLS scrape targets will be considered for service discovery. Value optional will allow scraping of both cleartext and TLS targets. Value required will restrict scraping to TLS targets only. | `required`
'service.endpoints.reverseproxy.tls.enforced'| The option controls if cleartext and TLS or only TLS is allowed on the PM query interface. Value optional allows both cleartext and TLS. Value required allows only TLS. | `required`
`service.endpoints.reverseproxy.tls.verifyClientCertificate` | It checks whether the client connection toward PM's reverseproxy using TLS requires authentication or not.  Non-authenticated connections will be logged and dropped in case this is enforced as required, otherwise the connection establishment will be granted. By default it is required, otherwise set it as optional. | `required`
`service.endpoints.reverseproxy.tls.certificateAuthorityBackwardCompatibility` | If true, SIP-TLS as CA will be used for query interface. | `false`
`nodeSelector` | Node labels for PM server pod assignment. | `{}`
`updateStrategy.server.type`| PM Server updateStrategy. | `{type: RollingUpdate}`
`securityContext`| Security Context for all containers. | `{}`
`terminationGracePeriodSeconds.server`| PM Server Pod termination grace period. | `300`
`tolerations.eric-pm-server`| The toleration specification for the PM Server pod. If both `tolerations.eric-pm-server` and ``server.tolerations` are set, the values set for `tolerations.eric-pm-server` are used. | `[]`
`topologySpreadConstraints` | TopologySpreadConstraint can be specified to spread PM Server pods among the given topology to achieve high availability and efficient resource utilization.Application deployment engineer can define one or multiple topologySpreadConstraint.| `[]`
`podPriority.eric-pm-server.priorityClassName` | The configuration of the priority class for the PM Server pod(s) assigning importance relative to other pods. | `""`
`probes.server.readinessProbe.initialDelaySeconds` | Delay, in seconds, before Kubernetes starts polling the service for liveness. This value may have to be increased if pod restarts are occurring.| `30`
`probes.server.readinessProbe.periodSeconds` | Interval, in seconds, between readiness probes.| `10`
`probes.server.readinessProbe.timeoutSeconds` | Number of seconds to allow before the probe times out. | `30`
`probes.server.readinessProbe.failureThreshold` | Number of failures before considering the probe to have failed. | `3`
`probes.server.readinessProbe.successThreshold` | Number of successes before considering the probe successful. | `1`
`probes.server.livenessProbe.initialDelaySeconds` | Delay, in seconds, before Kubernetes starts polling the service for liveness. This value may have to be increased if pod restarts are occurring.| `30`
`probes.server.livenessProbe.periodSeconds` | Interval, in seconds, between liveness probes.| `10`
`probes.server.livenessProbe.timeoutSeconds` | Number of seconds to allow before the probe times out. | `15`
`probes.server.livenessProbe.failureThreshold` | Number of failures before considering the probe to have failed. | `3`
`probes.server.livenessProbe.successThreshold` | Number of successes before considering the probe successful. | `1`
`probes.reverseproxy.readinessProbe.initialDelaySeconds` | Delay, in seconds, before Kubernetes starts polling the service for liveness. This value may have to be increased if pod restarts are occurring.| `5`
`probes.reverseproxy.readinessProbe.periodSeconds` | Interval, in seconds, between readiness probes.| `15`
`probes.reverseproxy.readinessProbe.timeoutSeconds` | Number of seconds to allow before the probe times out. | `15`
`probes.reverseproxy.readinessProbe.failureThreshold` | Number of failures before considering the probe to have failed. | `3`
`probes.reverseproxy.readinessProbe.successThreshold` | Number of successes before considering the probe successful. | `1`
`probes.reverseproxy.livenessProbe.initialDelaySeconds` | Delay, in seconds, before Kubernetes starts polling the service for liveness. This value may have to be increased if pod restarts are occurring.| `15`
`probes.reverseproxy.livenessProbe.periodSeconds` | Interval, in seconds, between liveness probes.| `15`
`probes.reverseproxy.livenessProbe.timeoutSeconds` | Number of seconds to allow before the probe times out. | `15`
`probes.reverseproxy.livenessProbe.failureThreshold` | Number of failures before considering the probe to have failed. | `3`
`probes.reverseproxy.livenessProbe.successThreshold` | Number of successes before considering the probe successful. | `1`
`probes.exporter.readinessProbe.initialDelaySeconds` | Delay, in seconds, before Kubernetes starts polling the service for liveness. This value may have to be increased if pod restarts are occurring.| `5`
`probes.exporter.readinessProbe.periodSeconds` | Interval, in seconds, between readiness probes.| `15`
`probes.exporter.readinessProbe.timeoutSeconds` | Number of seconds to allow before the probe times out. | `15`
`probes.exporter.readinessProbe.failureThreshold` | Number of failures before considering the probe to have failed. | `3`
`probes.exporter.readinessProbe.successThreshold` | Number of successes before considering the probe successful. | `1`
`probes.exporter.livenessProbe.initialDelaySeconds` | Delay, in seconds, before Kubernetes starts polling the service for liveness. This value may have to be increased if pod restarts are occurring.| `15`
`probes.exporter.livenessProbe.periodSeconds` | Interval, in seconds, between liveness probes.| `15`
`probes.exporter.livenessProbe.timeoutSeconds` | Number of seconds to allow before the probe times out. | `15`
`probes.exporter.livenessProbe.failureThreshold` | Number of failures before considering the probe to have failed. | `3`
`probes.exporter.livenessProbe.successThreshold` | Number of successes before considering the probe successful. | `1`
`probes.logshipper.livenessProbe.initialDelaySeconds` | Delay, in seconds, before Kubernetes starts polling the service for liveness. This value may have to be increased if pod restarts are occurring.| `1`
`probes.logshipper.livenessProbe.periodSeconds` | Interval, in seconds, between liveness probes.| `10`
`probes.logshipper.livenessProbe.timeoutSeconds` | Number of seconds to allow before the probe times out. | `10`
`probes.logshipper.livenessProbe.failureThreshold` | Number of failures before considering the probe to have failed. | `3`
`probes.logshipper.livenessProbe.successThreshold` | Number of successes before considering the probe successful. | `1`
`probes.configmapreload.readinessProbe.initialDelaySeconds` | Delay, in seconds, before Kubernetes starts polling the service for liveness. This value may have to be increased if pod restarts are occurring.| `30`
`probes.configmapreload.readinessProbe.periodSeconds` | Interval, in seconds, between readiness probes.| `10`
`probes.configmapreload.readinessProbe.timeoutSeconds` | Number of seconds to allow before the probe times out. | `30`
`probes.configmapreload.readinessProbe.failureThreshold` | Number of failures before considering the probe to have failed. | `3`
`probes.configmapreload.readinessProbe.successThreshold` | Number of successes before considering the probe successful. | `1`
`probes.configmapreload.livenessProbe.initialDelaySeconds` | Delay, in seconds, before Kubernetes starts polling the service for liveness. This value may have to be increased if pod restarts are occurring.| `30`
`probes.configmapreload.livenessProbe.periodSeconds` | Interval, in seconds, between liveness probes.| `10`
`probes.configmapreload.livenessProbe.timeoutSeconds` | Number of seconds to allow before the probe times out. | `15`
`probes.configmapreload.livenessProbe.failureThreshold` | Number of failures before considering the probe to have failed. | `3`
`probes.configmapreload.livenessProbe.successThreshold` | Number of successes before considering the probe successful. | `1`
`bandwidth.maxEgressRate` | The maximum rate in megabit-per-second at which traffic can leave the pod (Example: `bandwidth.maxEgressRate: 10M` for 10Mbps) | `""`

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
$ helm install ./eric-pm-server --name my-release \
    --set terminationGracePeriodSeconds.server=360
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
$ helm install ./eric-pm-server --name my-release -f values.yaml
```

> **Tip**: You can use the default [values.yaml](values.yaml)

### ConfigMap Files
PM Server is configured through prometheus.yml. This file (and any others listed in `serverFiles`) will be mounted into the `server` pod.

### Enabling RBAC for Service Accounts
PM server needs proper access rights in the Kubernetes cluster to be able to scrape all the PM providers listed in the configuration file.
Below are the steps to achive this with cluster role, service account and cluster role binding.

1. Create a ClusterRole to monitor

Here is an example:

```
$ cat server-clusterrole.yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  labels:
  name: "eric-pm-server-staging"
rules:
  - apiGroups:
      - ""
    resources:
      - nodes
      - nodes/proxy
      - services
      - endpoints
      - pods
      - ingresses
    verbs:
      - get
      - list
      - watch
  - apiGroups:
      - ""
    resources:
      - configmaps
    verbs:
      - get
  - apiGroups:
      - "extensions"
    resources:
      - ingresses/status
      - ingresses
    verbs:
      - get
      - list
      - watch
  - nonResourceURLs:
      - "/metrics"
    verbs:
      - get
```

```
$ kubectl  apply -f server-clusterrole.yaml
clusterrole "eric-pm-server-staging" configured
```
2. Create a Service Account

Below is an example of creating a service account named "monitoring" in the namespace "staging".
```
$ kubectl create sa monitoring --namespace staging
serviceaccount "monitoring" created
```
> **Tip** One must deploy the PM server in the same namespace in which the service account is created.
So in this case PM server should be deployed in staging namespace.

3. Create a ClusterRoleBinding

Below is an example of creating a cluster role binding named "eric-pm-server-staging" connecting the
cluster role "eric-pm-server-staging" with service account "monitoring" in the namespace "staging".
```
$ kubectl create clusterrolebinding eric-pm-server-staging \
  --clusterrole=eric-pm-server-staging --serviceaccount=staging:monitoring
clusterrolebinding "eric-pm-server-staging" created
```

### How to configure Pod Priority Class parameter
The priorityClassName needs to refer to an already existing priority class, otherwise the pod(s) will be rejected. With the default value of an empty string, no priorityClass will be specified and the pod(s) will be assigned the default pod priority class.
