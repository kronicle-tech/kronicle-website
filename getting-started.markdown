---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Getting Started
nav_order: 2
permalink: /getting-started
has_toc: true
---

# Getting Started
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

The easiest way to see Kronicle in action is to try the [Live Demo](https://demo.kronicle.tech).  The Live Demo is real
instance of Kronicle running on Kubernetes on AWS and it is populated with a mix of real data from the Kronicle Project and 
made up data from the fictional Kronicle Computers online shop.  

If you would like to install Kronicle on your own Kubernetes cluster, see the following steps.  

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

You will need to create a couple of Kubernetes ingresses to be able to access Kubernetes from outside your Kubernetes
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

## Configuration

See the [Configuration](/configuration) guide for information on how to configure Kronicle via environment variables.  

