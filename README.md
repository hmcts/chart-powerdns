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
| `pdns.api.enabled`         | Should the PowerDNS API be enabled | `yes`
| `pdns.api.key`             | PowerDNS API key | `PowerDNSAPI`
| `pdns.webserver.allowFrom` | PowerDNS webserver allowed IP whitelist |  `0.0.0.0/0`
| `pdns.dnsupdate.enabled`   | Should DNS UPDATE support be enabled | `no` |
| `replicaCount`                 | Number of pdns nodes | `1` |
| `image.repository`         | Image repository | `psitrax/powerdns` |
| `image.tag`                | Image tag. | `4.1.2`|
| `image.pullPolicy`         | Image pull policy | `IfNotPresent` |
| `service.type`             | Kubernetes service type | `ClusterIP` |
| `ingress.enabled`          | Enables Ingress | `false` |
| `ingress.annotations`      | Ingress annotations | `{}` |
| `ingress.path`           | Custom path                       | `/`
| `ingress.hosts`            | Ingress accepted hostnames | `chart-example.local` |
| `ingress.tls`              | Ingress TLS configuration | `[]` |
| `resources`                | CPU/Memory resource limits/requests | `{}` |
| `nodeSelector`             | Node labels for pod assignment | `{}` |
| `tolerations`              | Toleration labels for pod assignment | `[]` |
| `affinity`                 | Affinity settings for pod assignment | `{}` |
