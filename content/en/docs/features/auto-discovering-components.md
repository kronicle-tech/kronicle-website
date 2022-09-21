---
title: "Auto-discovering Components"
description: "Kronicle can auto-discover resources in Kubernetes clusters and AWS accounts and load them into its component catalog."
lead: "Kronicle can auto-discover resources in Kubernetes clusters and AWS accounts and load them into its component catalog."
date: 2022-09-21T20:00:00+00:00
lastmod: 2022-09-21T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "features"
weight: 201
toc: true
---

Kronicle can:

1. Auto-discover resources in Kubernetes clusters (e.g. services, deployments, config maps, Argo CD apps etc.) and AWS accounts (Lambda functions, databases, queues, S3 buckets, VPCs etc.)
2. Read metadata directly from those resources, without having to manually add the metadata to Kronicle.  It does this using [Kubernetes resource labels](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) and [AWS resource tags](https://docs.aws.amazon.com/general/latest/gr/aws_tagging.html)
3. Add the discovered resources to its component catalog, including copying the discovered metadata
4. Auto-generate diagrams that show the relationships between resources in Kubernetes/AWS

Examples in the Live Demo:

| URL                                                                                                                                           | Description                                                                            |
|-----------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [https://demo.kronicle.tech/components?platformId=kubernetes](https://demo.kronicle.tech/components?platformId=kubernetes)                    | Kubernetes resources auto-discovered from a demo Kubernetes cluster                    |
| [https://demo.kronicle.tech/components?platformId=aws](https://demo.kronicle.tech/components?platformId=kubernetes)                           | AWS resources auto-discovered from the AWS account hosting the Live Demo               |
| [https://demo.kronicle.tech/diagrams/structure-production.app.argocd-production](https://demo.kronicle.tech/components?platformId=kubernetes) | An auto-generated diagram that shows structure of an Argo CD app running on Kubernetes |
| [https://demo.kronicle.tech/diagrams/structure-lambda-example-production](https://demo.kronicle.tech/components?platformId=kubernetes)        | An auto-generated diagram that the AWS resources belonging to a particular "component" |

Auto-discovery is performed by these plugins:

1. [Kubernetes plugin](/docs/plugins/kubernetes/)
2. [AWS plugin](/docs/plugins/aws/)
