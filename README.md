# Prometheus Operator Demo

This kubernetes manifest is an example of how an app can be deployed into a kubernetes cluster with prometheus monitoring. This makes use of the 
[Prometheus Operator](https://github.com/coreos/prometheus-operator) to assist with configuring Prometheus to discover the applications in kubernetes that should be monitored.

## Pre-requisites

You will need a working kubernetes cluster. [Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/) will work fine.

## Deploy

You must apply `pre-deploy.yaml` before `deploy.yaml` in order to create the *Prometheus* and *ServiceMonitor* custom resources.

```
kubectl apply -f pre-deploy.yaml
kubectl apply -f deploy.yaml
```

Notice that on your first deployment you will see some error messages on the last lines because the CustomResourceDefinitions necessary to deploy a "ServiceMonitor" and "Prometheus" don't
exist until the "prometheus-operator" deployment has completed.

	>λ kubectl apply -f deploy.yaml
	serviceaccount "prometheus" unchanged
	serviceaccount "prometheus-operator" unchanged
	clusterrole.rbac.authorization.k8s.io "prometheus" configured
	clusterrole.rbac.authorization.k8s.io "prometheus-operator" configured
	clusterrolebinding.rbac.authorization.k8s.io "prometheus" configured
	clusterrolebinding.rbac.authorization.k8s.io "prometheus-operator" configured
	deployment.extensions "prometheus-operator" unchanged
	deployment.extensions "example-app" unchanged
	service "example-app" unchanged
	service "prometheus" unchanged
	unable to recognize "deploy.yaml": no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1"
	unable to recognize "deploy.yaml": no matches for kind "Prometheus" in version "monitoring.coreos.com/v1"

## Undeploy

`kubectl delete -f deploy.yaml`