---
title : "Kubernetes"
description: "Deploying to Kubernetes."
lead: "Deploying to Kubernetes."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "deployment"
weight: 1
---


## Requirements

1. Have a [kubeconfig](https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/) file (default location is ~/.kube/config).
2. Have [Helm v3 installed](https://helm.sh/docs/intro/install/).


## Install Kronicle

The following commands will install Kronicle in a Kubernetes namespace called `kronicle` in your default Kubernetes
cluster:

```shell
$ helm repo add kronicle https://charts.kronicle.tech
$ helm repo update
$ helm install kronicle kronicle/kronicle -n kronicle --create-namespace
```


## Kubernetes Ingresses

You will need to create two Kubernetes ingresses to be able to access Kubernetes from outside your Kubernetes
cluster.  One ingress is needed for Kronicle App and one for Kubernetes Service.

Here is an example Kubernetes manifest for creating the ingresses:

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: kronicle-app
  namespace: kronicle
  annotations:
    kubernetes.io/ingress.class: "nginx"
    nginx.ingress.kubernetes.io/force-ssl-redirect: "true"
    nginx.ingress.kubernetes.io/backend-protocol: "HTTP"
spec:
  rules:
    - host: demo.example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: kronicle-app
                port:
                  number: 80
  tls:
    - hosts:
        - demo.example.com
      secretName: kronicle-app-tls
---
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: kronicle-service
  namespace: kronicle
  annotations:
    kubernetes.io/ingress.class: "nginx"
    nginx.ingress.kubernetes.io/force-ssl-redirect: "true"
    nginx.ingress.kubernetes.io/backend-protocol: "HTTP"
spec:
  rules:
    - host: demo-service.example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: kronicle-service
                port:
                  number: 80
  tls:
    - hosts:
        - demo-service.example.com
      secretName: kronicle-service-tls
```
