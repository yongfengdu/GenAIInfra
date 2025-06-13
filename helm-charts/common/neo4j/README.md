# Neo4j Helm Chart

This Helm chart deploys a Neo4j database instance with APOC plugins enabled on Kubernetes.

## Prerequisites

- PV provisioner support in the underlying infrastructure

## Installing the Chart

To install the chart with the release name `my-neo4j`:

```bash
helm install my-neo4j ./neo4j
```

## Configuration

The following table lists the configurable parameters of the Neo4j chart and their default values.

| Parameter | Description | Default |
|-----------|-------------|---------|
| `image.repository` | Neo4j image repository | `neo4j` |
| `image.tag` | Neo4j image tag | `latest` |
| `image.pullPolicy` | Image pull policy | `IfNotPresent` |
| `service.type` | Kubernetes service type | `ClusterIP` |
| `service.ports` | Service ports configuration | See values.yaml |
| `persistence.enabled` | Enable persistence using PVC | `true` |
| `persistence.storageClass` | PVC Storage Class | `""` |
| `persistence.accessMode` | PVC Access Mode | `ReadWriteOnce` |
| `persistence.size` | PVC Storage Request | `10Gi` |
| `env` | Environment variables | See values.yaml |
| `resources` | CPU/Memory resource requests/limits | See values.yaml |

## Persistence

The Neo4j chart mounts a PersistentVolumeClaim and configures persistence for the following directories:
- `/data` - Database files
- `/logs` - Log files
- `/config` - Configuration files
- `/plugins` - Plugin files
- `/var/lib/neo4j/import` - Import directory