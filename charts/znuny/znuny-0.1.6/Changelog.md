* Rework tree
* Split configurations in dedicated Kubernetes resources
* Implement the ability to externalize database credentials in a kubernetes secrets
* Implement the ability to externalize local users credentials in a kubernetes secrets
* Implement the ability to externalize the smtp server credentials in a kubernetes secrets
* Implement the ability to externalize authentications backends in a kubernetes secrets
* Implement the ability to externalize private container registries secrets in a kubernetes secrets
* Implement the ability to externalize the Apache2 rewrite rules in a kubernetes configMap
* Integration of an automatically-generated default password for the administrator user, if not already configured
* Change the based container image version to 6.5.8
* Rename some resources (deployment, pod, service, ingress)
* Rewrite deployment notes
* Comment the values file
* Rework pod annotations
* Rework pod labels
* Rework container resources
* Implement Security contexts
* Rework autoscaling
* Add timezones
* Add znunu's secure mode
* Add Znuny's configuration overrides mechanism

