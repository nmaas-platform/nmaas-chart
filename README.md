# nmaas

![Version: 1.2.8](https://img.shields.io/badge/Version-1.2.8-informational?style=flat-square) ![AppVersion: 1.5.4](https://img.shields.io/badge/AppVersion-1.5.4-informational?style=flat-square)

GÉANT Network Management as a Service Helm chart for Kubernetes

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| nmaas-platform | <nmaas-admin@lists.geant.org> | <https://docs.nmaas.eu> |

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://artifactory.software.geant.org/artifactory/nmaas-helm-mirror | postgresql | 10.16.2 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| global.acmeIssuer | bool | `true` | set to no if a wildcard certificate is available |
| global.createIngressResources | bool | `true` |  |
| global.demoDeployment | bool | `false` |  |
| global.helmAccessKeyPrivate | string | `"nmaas-helm-key-private"` |  |
| global.helmAccessKeyPublic | string | `"nmaas-helm-key-public"` |  |
| global.ingressName | string | `"nmaas-ingress"` | prefix for the created ingress objects |
| global.issuerName | string | `"nmaas-issuer"` | name of a cert-manager issuer |
| global.nmaasDomain | string | `"nmaas.example.com"` |  |
| global.registrysecret | string | `"nmaas-registry"` | currently not needed, for future use |
| global.wildcardCertificateName | string | `"wildcard-tls"` |  |
| helm.enabled | bool | `true` |  |
| helm.image.pullPolicy | string | `"Always"` |  |
| helm.image.repository | string | `"artifactory.software.geant.org/nmaas-docker-local/nmaas-helm-3"` |  |
| helm.image.tag | string | `"3.9.3"` |  |
| helm.name | string | `"nmaas-helm"` |  |
| helm.persistence.accessMode | string | `"ReadWriteOnce"` |  |
| helm.persistence.enabled | bool | `true` |  |
| helm.persistence.existingClaim | string | `""` | name of an existing claim to be used. If empty, a new one is provisioned. |
| helm.persistence.size | string | `"1Gi"` |  |
| helm.persistence.storageClass | string | `""` |  |
| helm.port | int | `22` |  |
| helm.properties.users | string | `"helm:1000:1000"` |  |
| helm.serviceAccountName | string | `"nmaas-helm"` |  |
| helm.targetPort | int | `22` |  |
| helm.type | string | `"ClusterIP"` |  |
| janitor.enabled | bool | `true` |  |
| janitor.image.pullPolicy | string | `"IfNotPresent"` |  |
| janitor.image.repository | string | `"artifactory.software.geant.org/nmaas-docker-local/nmaas-janitor"` |  |
| janitor.image.tag | string | `"1.5.3"` |  |
| janitor.name | string | `"nmaas-janitor"` |  |
| janitor.port | int | `5000` |  |
| janitor.properties.gitlabApiUrl | string | `"http://nmaas-gitlab-webservice-default:8181/api/v4"` |  |
| janitor.properties.gitlabToken.literal | string | `""` |  |
| janitor.properties.gitlabToken.secret.key | string | `"secret"` |  |
| janitor.properties.gitlabToken.secret.name | string | `"nmaas-gitlab-janitor-token"` |  |
| janitor.serviceAccountName | string | `"nmaas-janitor"` |  |
| janitor.targetPort | int | `5000` |  |
| janitor.type | string | `"ClusterIP"` |  |
| platform.adminPassword.literal | string | `""` | leave empty to use the existing secret specified below |
| platform.adminPassword.secret.key | string | `"password"` |  |
| platform.adminPassword.secret.name | string | `"nmaas-platform-admin"` | must be created manually if literal is empty |
| platform.apiSecret.literal | string | `""` | leave empty to use existing secret specified below |
| platform.apiSecret.secret.key | string | `"secret"` |  |
| platform.apiSecret.secret.name | string | `"nmaas-api-secret"` | must be created manually if literal is empty |
| platform.enabled | bool | `true` |  |
| platform.image.pullPolicy | string | `"IfNotPresent"` |  |
| platform.image.repository | string | `"artifactory.software.geant.org/nmaas-docker-local/nmaas-platform"` |  |
| platform.image.tag | string | `"1.5.4"` |  |
| platform.ingress.className | string | `""` | defaults to .Values.platform.properties.k8s.ingress.controller.ingressClass if not set |
| platform.initscripts.enabled | bool | `true` |  |
| platform.initscripts.image.pullPolicy | string | `"Always"` |  |
| platform.initscripts.image.repository | string | `"artifactory.software.geant.org/nmaas-docker-local/nmaas-platform-populate"` |  |
| platform.initscripts.image.tag | string | `"v1.5.4"` |  |
| platform.livenessProbe.failureThreshold | int | `10` |  |
| platform.livenessProbe.httpGet.path | string | `"/actuator/health"` |  |
| platform.livenessProbe.httpGet.port | int | `9001` |  |
| platform.livenessProbe.periodSeconds | int | `30` |  |
| platform.livenessProbe.timeoutSeconds | int | `10` |  |
| platform.name | string | `"nmaas-platform"` |  |
| platform.persistence.accessMode | string | `"ReadWriteOnce"` |  |
| platform.persistence.enabled | bool | `true` |  |
| platform.persistence.existingClaim | string | `""` | name of an existing claim to be used. If empty, a new one is provisioned. |
| platform.persistence.size | string | `"1Gi"` |  |
| platform.persistence.storageClass | string | `""` |  |
| platform.port | int | `9001` |  |
| platform.properties.adminEmail | string | `"admin@example.com"` |  |
| platform.properties.apiDocsEnabled | bool | `false` |  |
| platform.properties.appInstanceFailureEmailList | string | `nil` |  |
| platform.properties.autoNamespaceCreationForDomains | bool | `false` | if true nmaas will automatically create the corresponding Kubernetes namespace for each new domain |
| platform.properties.captchaSecret.literal | string | `""` | leave empty to use existing secret specified below |
| platform.properties.captchaSecret.secret.key | string | `"secret"` |  |
| platform.properties.captchaSecret.secret.name | string | `"nmaas-captcha-secret-secret"` |  |
| platform.properties.defaultLanguage | string | `"en"` |  |
| platform.properties.gitlab.host | string | `"nmaas-gitlab-webservice-default"` | replace with service name from GitLab, e.g <MY_GITLAB_RELEASE>-webservice-default |
| platform.properties.gitlab.port | int | `8080` |  |
| platform.properties.helm.address | string | `"nmaas-helm"` |  |
| platform.properties.helm.asyncUpdateCron | string | `"0 0 * * * ?"` |  |
| platform.properties.helm.asyncUpdateEnabled | bool | `true` |  |
| platform.properties.helm.chartsDirectory | string | `"/home/nmaas/charts"` |  |
| platform.properties.helm.enableTls | bool | `true` |  |
| platform.properties.helm.repositoryName | string | `"nmaas"` |  |
| platform.properties.helm.repositoryUrl | string | `"https://artifactory.software.geant.org/artifactory/nmaas-helm"` |  |
| platform.properties.helm.useLocalCharts | bool | `false` |  |
| platform.properties.helm.username | string | `"helm"` |  |
| platform.properties.helm.version | string | `"v3"` |  |
| platform.properties.k8s.deployment.defaultNamespace | string | `"default"` | parameter used only if USE_DEFAULT_NAMESPACE option is set |
| platform.properties.k8s.deployment.defaultStorageClass | string | `nil` | should be left blank if default storage class was defined defined at cluster should be used |
| platform.properties.k8s.deployment.namespaceConfigOption | string | `"USE_DOMAIN_NAMESPACE"` | two options possible: USE_DOMAIN_NAMESPACE or USE_DEFAULT_NAMESPACE |
| platform.properties.k8s.ingress.certificate | object | `{"configOption":"USE_WILDCARD","issuerOrWildcardName":"nmaas-wildcard-secret"}` | TLS certificate related option are mandatory if tlsSupported flag is set to true |
| platform.properties.k8s.ingress.certificate.configOption | string | `"USE_WILDCARD"` | two options possible: USE_WILDCARD or USE_LETSENCRYPT |
| platform.properties.k8s.ingress.certificate.issuerOrWildcardName | string | `"nmaas-wildcard-secret"` | depending on the selected option, either certificate issuer name or name of secret object holding the certificate |
| platform.properties.k8s.ingress.controller.externalServiceDomain | string | `"nmaas.example.com"` | base FQDN for deployed user applications (e.g. nmaas.example.com) |
| platform.properties.k8s.ingress.controller.ingressClass | string | `"nginx"` | ingress class supported by the default ingress controller |
| platform.properties.k8s.ingress.controller.perDomain | bool | `false` | flag indicating if a dedicated ingress controller is deploy in every customer namespace |
| platform.properties.k8s.ingress.controller.publicIngressClass | string | `"public"` | ingress class to be used for services exposed publicly (e.g. without dedicated VPN) |
| platform.properties.k8s.ingress.controller.publicServiceDomain | string | `"public.nmaas.example.com"` | base FQDN for deployed user applications exposed publicly (e.g. public.nmaas.example.com) |
| platform.properties.k8s.ingress.controller.tlsSupported | bool | `true` | flag indicating if ingress controller(s) support TLS |
| platform.properties.maintenance | bool | `false` |  |
| platform.properties.nmaasMetricsEnabled | bool | `true` | expose Prometheus metrics |
| platform.properties.postgresql | object | `{"database":"nmaas","hostname":"nmaas-postgresql","password":{"literal":"","secret":{"key":"secret","name":"nmaas-postgresql-secret"}},"username":"nmaas"}` | only required if an external postgresql instance is used (when postgresql.install is false) |
| platform.properties.postgresql.password.literal | string | `""` | leave empty to use existing secret specified below |
| platform.properties.sendAppInstanceFailureEmails | bool | `false` |  |
| platform.properties.serviceDeploymentCheckInterval | int | `10` |  |
| platform.properties.serviceDeploymentCheckTimeout | int | `600` |  |
| platform.properties.serviceUpgradeCron | string | `"0 0 5 * * ?"` | example "0 0 5 * * ?" - every day at 5:00 AM |
| platform.properties.serviceUpgradeInterval | int | `24` |  |
| platform.properties.serviceUpgradeSummaryCron | string | `"0 0 6 * * ?"` | example "0 0 6 * * ?" - every day at 6:00 AM |
| platform.properties.showDomainRegistrationSelector | bool | `true` |  |
| platform.properties.smtp.from | string | `""` | override default SMTP from value |
| platform.properties.smtp.host | string | `"nmaas-postfix"` |  |
| platform.properties.sso.enabled | bool | `false` |  |
| platform.properties.sso.encryptionSecret.literal | string | `""` | leave empty to use existing secret specified below |
| platform.properties.sso.encryptionSecret.secret.key | string | `"secret"` |  |
| platform.properties.sso.encryptionSecret.secret.name | string | `"nmaas-sp-secret"` | must be created manually if literal is empty |
| platform.properties.sso.timeout | int | `15` |  |
| platform.properties.sso.urlLogin | string | `""` |  |
| platform.properties.sso.urlLogout | string | `""` |  |
| platform.properties.testInstance | bool | `false` |  |
| platform.readinessProbe.failureThreshold | int | `10` |  |
| platform.readinessProbe.httpGet.path | string | `"/actuator/health"` |  |
| platform.readinessProbe.httpGet.port | int | `9001` |  |
| platform.readinessProbe.periodSeconds | int | `15` |  |
| platform.readinessProbe.timeoutSeconds | int | `10` |  |
| platform.startupProbe.failureThreshold | int | `30` |  |
| platform.startupProbe.httpGet.path | string | `"/actuator/health"` |  |
| platform.startupProbe.httpGet.port | int | `9001` |  |
| platform.startupProbe.periodSeconds | int | `15` |  |
| platform.startupProbe.timeoutSeconds | int | `10` |  |
| platform.targetPort | int | `9001` |  |
| platform.tls | bool | `true` |  |
| platform.type | string | `"ClusterIP"` |  |
| portal.enabled | bool | `true` |  |
| portal.image.pullPolicy | string | `"IfNotPresent"` |  |
| portal.image.repository | string | `"artifactory.software.geant.org/nmaas-docker-local/nmaas-portal"` |  |
| portal.image.tag | string | `"1.5.3"` |  |
| portal.ingress.className | string | `""` | defaults to .Values.platform.properties.k8s.ingress.controller.ingressClass if not set |
| portal.name | string | `"nmaas-portal"` |  |
| portal.port | int | `9009` |  |
| portal.properties.captchaKey.literal | string | `""` | empty to use existing secret specified below |
| portal.properties.captchaKey.secret.key | string | `"secret"` |  |
| portal.properties.captchaKey.secret.name | string | `"nmaas-captcha-key-secret"` |  |
| portal.properties.tokenName | string | `"token"` |  |
| portal.targetPort | int | `9009` |  |
| portal.tls | bool | `true` |  |
| portal.type | string | `"ClusterIP"` |  |
| postfix.enabled | bool | `true` |  |
| postfix.image.pullPolicy | string | `"Always"` |  |
| postfix.image.repository | string | `"artifactory.software.geant.org/nmaas-docker-local/nmaas-postfix"` |  |
| postfix.image.tag | string | `"1.2.0"` |  |
| postfix.name | string | `"nmaas-postfix"` |  |
| postfix.port | int | `587` |  |
| postfix.properties.hostname | string | `"mailer.example.com"` |  |
| postfix.properties.smtp | object | `{"fromAddress":"noreply@example.com","host":{"literal":"","secret":{"key":"smtpHost"}},"password":{"literal":"","secret":{"key":"smtpPassword"}},"port":587,"secretName":"nmaas-smtp-secret","username":{"literal":"","secret":{"key":"smtpUsername"}}}` | only required if smtp image is used |
| postfix.properties.smtp.host.literal | string | `""` | leave empty to use existing secret |
| postfix.properties.smtp.password.literal | string | `""` | leave empty to use existing secret |
| postfix.properties.smtp.username.literal | string | `""` | leave empty to use existing secret |
| postfix.type | string | `"ClusterIP"` |  |
| postgresql | object | `{"install":true,"persistence":{"enabled":true,"size":"8Gi"},"postgresqlDatabase":"nmaas","postgresqlPassword":"nmaas","postgresqlUsername":"nmaas"}` | settings for in-cluster postgresql |
| replicaCount | int | `1` |  |
| sp.enabled | bool | `false` |  |
| sp.image.pullPolicy | string | `"Always"` |  |
| sp.image.repository | string | `"artifactory.software.geant.org/nmaas-docker-local/nmaas-sp"` |  |
| sp.image.tag | string | `"1.2.0"` |  |
| sp.ingress.className | string | `""` | defaults to .Values.platform.properties.k8s.ingress.controller.ingressClass if not set |
| sp.name | string | `"nmaas-sp"` |  |
| sp.port | int | `443` |  |
| sp.properties.idp.name | string | `"edugain"` |  |
| sp.properties.idp.uri | string | `"https://login.terena.org/wayf/saml2/idp/metadata.php"` |  |
| sp.properties.idp.userId | string | `"uid"` |  |
| sp.targetPort | int | `80` |  |
| sp.tls | bool | `true` |  |
| sp.type | string | `"ClusterIP"` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
