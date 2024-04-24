# znuny

A Helm chart to deploy Znuny on Kubernetes

![Version: 0.1.6](https://img.shields.io/badge/Version-0.1.6-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 6.5.8](https://img.shields.io/badge/AppVersion-6.5.8-informational?style=flat-square)

## Values

### Required

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| config.database.externalSecret | object | `{}` | Define the name of a Kubernetes secret to set the database credentials. If externalSecret is defined, keys "username" and "password" will be ignored. |
| config.database.host | object | `{}` | Set the host of the database. |
| config.database.name | string | `"znuny"` | Set the name of the database. |
| config.database.password | object | `{}` | Set the database password to connect to. Ignored if an externalSecret is defined. |
| config.database.port | int | `5432` | Set the port of the database. |
| config.database.username | object | `{}` | Set the database username to connect to. Ignored if an externalSecret is defined. |

### Extra

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| extraConfigMaps | list | `[]` | Set extras Kubernetes configMaps. |
| extraConfigmapMounts | list | `[]` | Set extras Kubernetes configMaps mounts. |

### Other Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| autoscaling | object | `{"enabled":false,"maxReplicas":3,"minReplicas":1,"targetCPUUtilizationPercentage":20,"targetMemoryUtilizationPercentage":50}` | Set the auto scaling of Znuny. |
| autoscaling.enabled | bool | `false` | Enable the Horizontal pod scaling |
| autoscaling.maxReplicas | int | `3` | Set the miximum of replicas. |
| autoscaling.minReplicas | int | `1` | Set the minimum of replicas. |
| autoscaling.targetCPUUtilizationPercentage | int | `20` | Set the percentage of cpu to trigger the scaling. |
| autoscaling.targetMemoryUtilizationPercentage | int | `50` | Set the percentage of memory to trigger the scaling. |
| config | object | `{"apache":{"domain":{},"rewriteRules":{"externalConfigMap":{},"rules":{}}},"authentications":{"backends":{},"externalSecret":{}},"database":{"externalSecret":{},"host":{},"name":"znuny","password":{},"port":5432,"username":{}},"logs":{"path":"/var/log/znuny"},"mails":{"sendmail":{"enabled":true},"smtp":{"enabled":false,"externalSecret":{},"host":{},"password":{},"port":{},"username":{}}},"users":{"admin":{"externalSecret":{},"password":{},"username":"root@localhost"}}}` | Set Znuny's configurations. |
| config.apache | object | `{"domain":{},"rewriteRules":{"externalConfigMap":{},"rules":{}}}` | Set Apache2 custom configurations. |
| config.apache.domain | object | `{}` | Set a local domain in Apache2 configurations. |
| config.apache.rewriteRules | object | `{"externalConfigMap":{},"rules":{}}` | Set rewrite rules in Apache2 configurations. |
| config.apache.rewriteRules.externalConfigMap | object | `{}` | Define the name of a Kubernetes configMap to set the Apache2 rewrite rules. If externalConfigMap is defined, the key "rules" will be ignored. |
| config.apache.rewriteRules.rules | object | `{}` | Set the rewrite rules to be included. |
| config.authentications | object | `{"backends":{},"externalSecret":{}}` | Set the application authentication backends. |
| config.authentications.backends | object | `{}` | Set the authentications backends configurations as following in a single block. |
| config.authentications.externalSecret | object | `{}` | Define the name of a Kubernetes secret to set the application authentication backends. If externalSecret is defined, the key "backends" will be ignored. |
| config.database | object | `{"externalSecret":{},"host":{},"name":"znuny","password":{},"port":5432,"username":{}}` | Set the connection of the PostgreSQL database. |
| config.logs | object | `{"path":"/var/log/znuny"}` | Set the application logging. |
| config.logs.path | string | `"/var/log/znuny"` | Set a path to Znuny's file logging. The file logging is enabled only if the key "path" is set. |
| config.mails | object | `{"sendmail":{"enabled":true},"smtp":{"enabled":false,"externalSecret":{},"host":{},"password":{},"port":{},"username":{}}}` | Set the application e-mail notifications system. There are two mailing type :   - sendmail: Send mail with the local sendmail module.   - smtp: Connect to an external SMTP server to send mails. Both features can't be activated simultaneously. The feature "sendmail" will be prioritized over "smtp" as long as its "enabled" key is set to true. |
| config.mails.sendmail | object | `{"enabled":true}` | Setting of the local Sendmail module. |
| config.mails.sendmail.enabled | bool | `true` | Enable the Sendmail module. |
| config.mails.smtp | object | `{"enabled":false,"externalSecret":{},"host":{},"password":{},"port":{},"username":{}}` | Setting of the SMTP connection. |
| config.mails.smtp.enabled | bool | `false` | Enable the SMTP connection. |
| config.mails.smtp.externalSecret | object | `{}` | Define the name of a Kubernetes secret to set the SMTP server credentials. If externalSecret is defined, keys "username" and "password" will be ignored. |
| config.mails.smtp.host | object | `{}` | Set the host of the SMTP server |
| config.mails.smtp.password | object | `{}` | Set the SMTP server password to connect to. Ignored if an externalSecret is defined. |
| config.mails.smtp.port | object | `{}` | Set the port of the SMTP server |
| config.mails.smtp.username | object | `{}` | Set the SMTP server username to connect to. Ignored if an externalSecret is defined. |
| config.users | object | `{"admin":{"externalSecret":{},"password":{},"username":"root@localhost"}}` | Set Znuny's local users. |
| config.users.admin | object | `{"externalSecret":{},"password":{},"username":"root@localhost"}` | Setting of the administrator user. |
| config.users.admin.externalSecret | object | `{}` | Define the name of a Kubernetes secret to set the administrator credentials. If externalSecret is defined, keys "username" and "password" will be ignored. |
| config.users.admin.password | object | `{}` | Set the administrator's password. Ignored if an externalSecret is defined. |
| config.users.admin.username | string | `"root@localhost"` | Set the administrator's username. Ignored if an externalSecret is defined. |
| image | object | `{"pullPolicy":"IfNotPresent","pullSecrets":[],"repository":"ghcr.io/fr-bez-aosc/docker-znuny","tag":"6.5.8-0"}` | Set the container image specifications. |
| image.pullPolicy | string | `"IfNotPresent"` | Set the image pull policy. |
| image.pullSecrets | list | `[]` | Set a registry pull secret if a custom image hosted on a private registry is used. The secret must be encoded in base64. |
| image.repository | string | `"ghcr.io/fr-bez-aosc/docker-znuny"` | Set the container image to use. |
| image.tag | string | `"6.5.8-0"` | Set the image tag to use. |
| ingress | object | `{"annotations":{},"domain":{},"enabled":false,"tls":{"enabled":false}}` | Set the Kubernetes ingress specifications. |
| ingress.annotations | object | `{}` | Set annotations to add to the ingress. |
| ingress.domain | object | `{}` | Set the public domain on which Znuny will be exposed. |
| ingress.enabled | bool | `false` | Enable the ingress features. |
| ingress.tls | object | `{"enabled":false}` | Set TLS configurations. |
| ingress.tls.enabled | bool | `false` | Enable TLS support. |
| nameOverride | object | {} | Set a name to override the release name to deploy to. |
| namespaceOverride | object | {} | Set a name to override the namespace name to deploy to. |
| persistentVolumeClaims | object | `{}` | Set persistant volumes. The access mode depend to your CSI |
| pod | object | `{"annotations":{},"deploymentStrategy":"Recreate","labels":{},"replicaCount":1,"resources":{"limits":{"cpu":"2000m","memory":"4096Mi"},"requests":{"cpu":"1000m","memory":"2048Mi"}},"restartPolicy":"Always","securityContext":{}}` | Set Znuny's pod specifications |
| pod.annotations | object | `{}` | Set annotations to add to Znuny's pod. |
| pod.deploymentStrategy | string | `"Recreate"` | Set the deployment strategy. |
| pod.labels | object | `{}` | Set labels to add to Znuny's pod. |
| pod.replicaCount | int | `1` | Set replicas count. |
| pod.resources | object | `{"limits":{"cpu":"2000m","memory":"4096Mi"},"requests":{"cpu":"1000m","memory":"2048Mi"}}` | Set Znuny's container resources. |
| pod.resources.limits | object | `{"cpu":"2000m","memory":"4096Mi"}` | Set Znuny's container limits. |
| pod.resources.limits.cpu | string | `"2000m"` | Set Znuny's container cpu limits. |
| pod.resources.limits.memory | string | `"4096Mi"` | Set Znuny's container memory limits. |
| pod.resources.requests | object | `{"cpu":"1000m","memory":"2048Mi"}` | Set Znuny's container requests. |
| pod.resources.requests.cpu | string | `"1000m"` | Set Znuny's container cpu requests. |
| pod.resources.requests.memory | string | `"2048Mi"` | Set Znuny's container memory requests. |
| pod.restartPolicy | string | `"Always"` | Set the restart policy. |
| pod.securityContext | object | `{}` | Set Znuny's pod security contexts. |
| service | object | `{"port":80,"type":"ClusterIP"}` | Set the Kubernetes services specifications. |
| service.port | int | `80` | Set the service port. |
| service.type | string | `"ClusterIP"` | Set the service type. |
| serviceAccount | object | `{"annotations":{},"create":false,"name":"znuny"}` | Set a service account. |
| serviceAccount.annotations | object | {} | Set annotations to add to the service account. |
| serviceAccount.create | bool | false | Specifies whether a service account should be created. |
| serviceAccount.name | string | "znuny" | Set he name of the service account to use. |