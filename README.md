# Airflow with k8s executor

This project is built on top of [Apache Airflow on Kubernetes](https://github.com/apache/airflow/tree/master/scripts/ci/kubernetes). The vision is operating airflow on k8s with:

* [x] k8s executor
* [ ] operatior UX
    * [x] uses [kustomize](https://kustomize.io)
    * [x] separate configuration for dev and production
    * [ ] improves log aggregation - to avoid all pods try to write to a single pvc `airflow-logs`
* security enhancements
    * [x] picks official airflow container image - [`apache/airflow`](https://hub.docker.com/r/apache/airflow)
    * [ ] k8s RBAC
    * [x] security context for all pods
    * [ ] secrets management

## Prerequisites

* [`kustomize`](https://kustomize.io) CLI - see [How to install](https://github.com/kubernetes-sigs/kustomize/blob/master/docs/INSTALL.md)

## How to generate k8s objects:

```SHELL
$ kustomize build dev/
```

## Design

It uses kustomize overlays to separate dev/prod configuration.

* development
    * in `default` namespace
    * service account is binding to clusteradmin
    * dags not in image
    * keeps logs in a pvc
    * uses local postgres db

* production
    * in a given namespace
    * has its own service account and role.
    * dags in custom build image
    * remote logging
    * remote db
    * no secrets in code
