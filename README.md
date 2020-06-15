# Helm chart for knative serving

[![Latest Version](https://img.shields.io/github/release/softonic/knative-serving-chart.svg)](https://github.com/softonic/knative-serving-chart/releases)
[![Software License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/softonic/knative-serving-chart.svg)](http://isitmaintained.com/project/softonic/knative-serving-chart "Average time to resolve an issue")
![GitHub issues](https://img.shields.io/github/issues-raw/softonic/knative-serving-chart)

# Overview

With this chart you are going to install a serving component of Knative on a Kubernetes cluster. Following the knative-serving documentation.
[Knative install docs](https://knative.dev/docs/install/any-kubernetes-cluster/)

Knative v0.15.0 requires a Kubernetes cluster v1.15 or newer, as well as a compatible kubectl. 

# knative-serving

[Knative Serving for k8s](https://github.com/softonic/knative-serving-chart) - With this chart you are going to install a serving component of Knative on a Kubernetes cluster. Following the knative-serving documentation.

## TL;DR;

```console
$ helm repo add softonic https://charts.softonic.io
$ helm repo update
$ helm install knative-serving softonic/knative-serving -n knative-serving --version=2.0.1
```

## Introduction

This chart deploys  on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes v1.15+
- Istio v1.1
- Cert-Manager

## Installing the Chart

To install the chart with the release name `knative-serving`:

```console
$ helm install knative-serving softonic/knative-serving -n knative-serving --version=2.0.1
```

The command deploys  on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `knative-serving`:

```console
$ helm delete knative-serving -n knative-serving
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the `knative-serving` chart and their default values.

|          Parameter           |                                                      Description                                                       |          Default           |
|------------------------------|------------------------------------------------------------------------------------------------------------------------|----------------------------|
| replicaCount                 |                                                                                                                        | `1`                        |
| core.domain                  |                                                                                                                        | `"sftapi.com"`             |
| istio.externalIngressgateway |                                                                                                                        | `"knative-ingressgateway"` |
| istio.localIngressgateway    |                                                                                                                        | `"cluster-local-gateway"`  |
| istio.namespace              |                                                                                                                        | `"istio-system"`           |
| image.repository             |                                                                                                                        | `nginx`                    |
| image.pullPolicy             |                                                                                                                        | `IfNotPresent`             |
| imagePullSecrets             |                                                                                                                        | `[]`                       |
| nameOverride                 |                                                                                                                        | `""`                       |
| fullnameOverride             |                                                                                                                        | `""`                       |
| serviceAccount.create        | Specifies whether a service account should be created                                                                  | `true`                     |
| serviceAccount.annotations   | Annotations to add to the service account                                                                              | `{}`                       |
| serviceAccount.name          | The name of the service account to use. If not set and create is true, a name is generated using the fullname template | ``                         |
| podSecurityContext           |                                                                                                                        | `{}`                       |
| securityContext              |                                                                                                                        | `{}`                       |
| service.type                 |                                                                                                                        | `ClusterIP`                |
| service.port                 |                                                                                                                        | `80`                       |
| ingress.enabled              |                                                                                                                        | `false`                    |
| ingress.annotations          |                                                                                                                        | `{}`                       |
| ingress.tls                  |                                                                                                                        | `[]`                       |
| resources                    |                                                                                                                        | `{}`                       |
| nodeSelector                 |                                                                                                                        | `{}`                       |
| tolerations                  |                                                                                                                        | `[]`                       |
| affinity                     |                                                                                                                        | `{}`                       |


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example:

```console
$ helm install knative-serving softonic/knative-serving -n knative-serving --version=2.0.1 --set replicaCount=1
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while
installing the chart. For example:

```console
$ helm install knative-serving softonic/knative-serving -n knative-serving --version=2.0.1 --values values.yaml
```
