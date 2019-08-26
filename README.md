# Airflow with k8s executor

This project is built on top of [Apache Airflow on Kubernetes](https://github.com/apache/airflow/tree/master/scripts/ci/kubernetes). The vision is operating airflow on k8s with:

* [x] k8s executor
* [ ] operatior UX
    * [ ] uses [kustomize](https://kustomize.io)
    * [ ] improves log aggregation
* security enhancements
    * [x] picks official airflow container image - [`apache/airflow`](https://hub.docker.com/r/apache/airflow)
    * [ ] k8s RBAC
    * [ ] security context for all pods
    * [ ] secretx management

## Prerequisites

* [`kustomize`](https://kustomize.io) CLI - see [How to install](https://github.com/kubernetes-sigs/kustomize/blob/master/docs/INSTALL.md)

## How to generate k8s objects:

```SHELL
$ kustomize build .
```