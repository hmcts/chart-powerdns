# Helm Chart for PowerDNS

* Installs a PowerDNS authoritative nameserver

## TL;DR;

```console
$ git clone https://github.com/hmcts/chart-powerdns
$ cd chart-powerdns
$ helm install .
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
$ helm install --name my-release .
```

## Uninstalling the Chart

To uninstall/delete the my-release deployment:

```console
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.


## Configuration

### PowerDNS

| Parameter                  | Description                         | Default                                                 |
|----------------------------|-------------------------------------|---------------------------------------------------------|
| `replicaCount`             | Number of pdns nodes | `1` |
| `image.repository`         | Image repository | `hmcts/powerdns-auth` |
| `image.tag`                | Image tag. | `4.1.5r2-v0.0.1`|
| `image.pullPolicy`         | Image pull policy | `IfNotPresent` |
| `service.type`             | Kubernetes service type | `ClusterIP` |
| `service.loadBalancerIP`   | Internal balancer IP for DNS service | `nil` |
| `service.annotations`      | DNS service annotations | `{}` |
| `resources.limits.cpu`     | DNS service CPU resource limit | `500m` |
| `resources.limits.memory`  | DNS service memory resource limit | `1024Mi` |
| `resources.requests.cpu`   | DNS service CPU requests | `500m` |
| `resources.requests.memory`| DNS service memory requests | `1024Mi` |
| `environment`              | Environment variables | `see values.yaml` |
| `keyVault.vaultName`       | Keyvault name for use with keyvault-flexvol | `nil` |
| `keyVault.resourceGroup`   | Keyvault resouce group for keyvault | `nil` |
| `keyVault.subscriptionId`  | Keyvault subscription ID | `nil` |
| `keyVault.tenantId`        | Keyvault tenant ID | `nil` |
| `keyVault.secrets.dbUsernameSecret` | The name of the secret in Keyvault for the external DB username | `nil` |
| `keyVault.secrets.dbPasswordSecret` | The name of the secret in Keyvault for the external DB password | `nil` |
| `keyVault.secrets.pdnsApiKeySecret` | The name of the secret in Keyvault for the PowerDNS API key | `nil` |
| `ui.enabled`               | Enable PowerDNS-Admin UI container | `true` |
| `ui.replicaCount`          | number of UI replicas | `1` |
| `ui.image.repository`      | PowerDNS-Admin image | `hmcts/powerdns-admin:latest` |
| `ui.image.pullPolicy`      | PowerDNS-Admin image pull policy| `hmcts/powerdns-admin:latest` |
| `ui.resources.limits.cpu`     | UI CPU resource limit | `500m` |
| `ui.resources.limits.memory`  | UI memory resource limit | `1024Mi` |
| `ui.resources.requests.cpu`   | UI CPU requests | `500m` |
| `ui.resources.requests.memory`| UI memory requests | `128Mi` |
| `ui.environment`           | UI container environment variables | `see values.yaml` |
| `ui.ingress.enabled`       | Enables Ingress | `false` |
| `ui.ingress.annotations`   | Ingress annotations | `kubernetes.io/ingress.class: traefik` |
| `ui.ingress.hostName`      | Ingress hostname | `nil` |
| `ingress.tls`              | Ingress TLS configuration | `false` |
| `postgresql.enabled` | Enable optional PostgreSQL container | `true` |
| `postgresql.postgresqlUsername` | PostgreSQL username | `v` |
| `postgresql.postgresqlPassword` | PostgreSQL password | `pdns` |
| `postgresql.postgresqlDatabase` | PostgreSQL database name | `pdns` |
| `postgresql.initdbScripts.init.sql` | PostgreSQL init script | `CREATE DATABASE "pdns_ui" WITH OWNER = pdns ENCODING = 'UTF-8' CONNECTION LIMIT = -1;` |
| `postgresql.persistence.enabled` | Enable persistence for PostgreSQL container | `false` |
