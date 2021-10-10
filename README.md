# Nebula Graph Studio Helm Chart

## Introduction
This chart bootstraps Nebula Graph Studio deployment on a Kubernetes cluster using the Helm.

## Prerequisites

- Kubernetes 1.14+
- Helm >= 3.2.0

## Install

First, configure the chart repository and update.
```sh
$ helm repo add nebula-graph https://matrixji.github.io/nebula-studio-helm/
$ helm repo update
```

### Install with a default configurations

Assume using release name: `my-studio`

```
$ helm upgrade --install my-studio nebula-graph/nebula-studio
```

### Install with a NodePort for external visit

```
$ helm upgrade --install my-studio --set service.type=NodePort --set service.port=30070 nebula-graph/nebula-studio
```

After success installed, we could visit nebula-studio via http://address-of-node:30070/

## Uninstall

```
$ helm uninstall my-studio
```

## Configuration


| Parameter | Description | Default |
|-----------|-------------|---------|
| replicaCount  | Replica Count for StatefulSet  | 0  |
| image.httpGateway.repository  |  The repository for http grateway's image  | vesoft/nebula-http-gateway  |
| image.nebulaImporter.repository  |  The repository for nebula-importer ateway's image  | vesoft/nebula-importer  |
| image.nebulaStudio.repository  |  The repository for nebula graph studio's image  | vesoft/nebula-graph-studio |
| image.nginx.repository  |  The repository for nginx's image  | nginx  |
| image.httpGateway.tag  |  The tag for http grateway's image  | v2  |
| image.nebulaImporter.tag  |  The tag for nebula-importer ateway's image  | v2  |
| image.nebulaStudio.tag  |  The tag for nebula graph studio's image  | v3  |
| image.nginx.tag  |  The tag for nginx's image  | alpine  |
| service.type  | The service type, should be one of ['NodePort', 'ClusterIP', 'LoadBalancer'] |  ClusterIP  |
| service.port  | The expose port for nebula-graph-studio's web |  7001  |
| resources.httpGateway.limits.cpu  | The cpu limit for http gateway container  | 2  |
| resources.httpGateway.limits.memory  | The memory limit for http gateway container  | 4Gi  |
| resources.httpGateway.requests.cpu  | The cpu request for http gateway container  | 100mi  |
| resources.httpGateway.requests.memory  | The memory request for http gateway container  | 256Mi | 
| resources.nebulaImporter.limits.cpu  | The cpu limit for nebula importer container  | 2  |
| resources.nebulaImporter.limits.memory  | The memory limit for nebula importer container  | 4Gi  |
| resources.nebulaImporter.requests.cpu  | The cpu request for nebula importer container  | 100mi  |
| resources.nebulaImporter.requests.memory  | The memory request for nebula importer container  | 256Mi | 
| resources.nebulaStudio.limits.cpu  | The cpu limit for nebula studio container  | 2  |
| resources.nebulaStudio.limits.memory  | The memory limit for nebula studio container  | 4Gi  |
| resources.nebulaStudio.requests.cpu  | The cpu request for nebula studio container  | 100mi  |
| resources.nebulaStudio.requests.memory  | The memory request for nebula studio container  | 256Mi | 
| resources.nginx.limits.cpu  | The cpu limit for nginx container  | 2  |
| resources.nginx.limits.memory  | The memory limit for nginx container  | 4Gi  |
| resources.nginx.requests.cpu  | The cpu request for nginx container  | 100mi  |
| resources.nginx.requests.memory  | The memory request for nginx container  | 256Mi | 
| persistent.storageClassName  | The storageClassName for PVC if not using default  | ""  |
| persistent.size  | The size for upload-data persistent storage | 5Gi  |

