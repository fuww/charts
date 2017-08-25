```shell
helm install --name my-release kadira

helm delete my-release

or the brute-force way:

helm del --purge my-release 

Create cert on Cloudflare
store in tls.crt tls.key

kubectl create secret tls chart-kadira-tls --cert=./tls.cert --key=./tls.key

kubectl get ing

helm upgrade my-release



helm install --name my-kadira kadira
helm del --purge my-kadira 
helm upgrade my-kadira kadira

kubectl describe ing my-kadira-ui

```


# Kadira

[Kadira](https://github.com/meteorhacks/kadira) is a Monitoring system for Meteor.

## TL;DR;

```console
$ helm install incubator/kadira
```

## Introduction

This chart bootstraps a [Kadira](https://github.com/meteorhacks/kadira) deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

It also packages the [MongoDB chart](https://github.com/kubernetes/charts/tree/master/stable/mongodb) which is required for bootstrapping a MongoDB deployment for the database requirements of the Kadira application.

## Prerequisites

- Kubernetes 1.4+ with Beta APIs enabled
- PV provisioner support in the underlying infrastructure

## Installing the Chart

To install the chart with the release name `my-release`:

```console
$ helm install --name my-release incubator/kadira
```

The command deploys Kadira on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Kadira chart and their default values.

### Kadira Engine

| Parameter               | Description                        | Default                                                    |
| ----------------------- | ---------------------------------- | ---------------------------------------------------------- |
| `Engine.Name`           | Kadira Engine name                 | `engine`                                             |
| `Engine.Image`          | Container image name               | `fuww/kadira-engine`                           |
| `Engine.ImageTag`       | Container image tag                | `latest`                                                 |
| `Engine.Replicas`       | k8s deployment replicas            | `1`                                                        |
| `Engine.Component`      | k8s selector key                   | `kadira-engine`                                             |
| `Engine.externalPort`   | k8s service port                   | `11011`                                                     |
| `Engine.ContainerPort`  | Container listening port           | `11011`                                                     |
| `Engine.type`           | Kubernetes Service type            | `NodePort`                                                       |

### Kadira Rma

|       Parameter       |           Description            |                         Default                          |
|-----------------------|----------------------------------|----------------------------------------------------------|
| `Rma.Name`            | Kadira Rma name                | `rma`                                            |
| `Rma.Image`           | Container image name               | `dkoo761/kadira-rma`                           |
| `Rma.ImageTag`        | Container image tag                | `latest`                                                 |
| `Rma.Component`       | k8s selector key                   | `kadira-rma`                                             |
| `Rma.Replicas`        | k8s deployment replicas            | `1`                                                        |

### Kadira Ui

| Parameter                    | Description                        | Default                                                    |
| -----------------------      | ---------------------------------- | ---------------------------------------------------------- |
| `Ui.Name`                | Kadira Ui name                  | `ui`                                             |
| `Ui.Image`               | Container image name               | `vladgolubev/kadira-ui`                           |
| `Ui.ImageTag`            | Container image tag                | `latest`                                                 |
| `Ui.Replicas`            | k8s deployment replicas            | `1`                                                        |
| `Ui.Component`           | k8s selector key                   | `kadira-ui`                                             |
| `Ui.ContainerPort`       | Container listening port           | `4000`                                                     |
| `Ui.externalPort` | k8s service port       | `4000`                                                       |
| `Ui.type`           | Kubernetes Service type            | `NodePort`                                                       |


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
$ helm install --name my-release \
  --set UI.name=mykadiraui,Engine.replicas=3 \
    incubator/kadira
```


Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
$ helm install --name my-release -f values.yaml incubator/kadira
```

> **Tip**: You can use the default [values.yaml](values.yaml)