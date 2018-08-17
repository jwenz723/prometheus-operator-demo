# Prometheus Operator Demo

This kubernetes manifest is an example of how an app can be deployed into a kubernetes cluster with prometheus monitoring. This makes use of the 
[Prometheus Operator](https://github.com/coreos/prometheus-operator) to assist with configuring Prometheus to discover the applications in kubernetes that should be monitored.

## Pre-requisites

You will need a working kubernetes cluster. [Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/) will work fine.

## Deploy

`kubectl apply -f deploy.yaml`

## Undeploy

`kubectl delete -f deploy.yaml`