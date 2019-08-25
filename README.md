# Airflow with k8s executor

## Prerequisites

* [`kustomize`](https://kustomize.io) CLI - see [How to install](https://github.com/kubernetes-sigs/kustomize/blob/master/docs/INSTALL.md)

## How to generate k8s objects:

```SHELL
$ kustomize build .
```