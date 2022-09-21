---
title: "Auto-generating Diagrams"
description: "Kronicle can auto-generate diagrams for things like Kubernetes resources, AWS resources, AWS X-ray service dependencies etc."
lead: "Kronicle can auto-generate diagrams for things like Kubernetes resources, AWS resources, AWS X-ray service dependencies etc."
date: 2022-09-21T20:00:00+00:00
lastmod: 2022-09-21T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "features"
weight: 202
toc: true
---

Kronicle can auto-generate diagrams for the following:

1. Kubernetes resources
2. AWS resources
3. AWS X-Ray service dependencies

The diagrams that Kronicle generates automatically use the official icons for Kubernetes and AWS resources.

See these examples of auto-generated diagrams in the Live Demo:

| Auto-generated Diagram                                                         | Description                                                                                         |
|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| [https://demo.kronicle.tech/diagrams/structure-production.app.argocd-production](https://demo.kronicle.tech/components?platformId=kubernetes) | Shows the structure of an Argo CD app running on Kubernetes                                         |
| [https://demo.kronicle.tech/diagrams/aws-xray-service-graph-production](https://demo.kronicle.tech/components?platformId=kubernetes)          | Shows the dependencies between services/components that are using AWS X-Ray for distributed tracing |
| [https://demo.kronicle.tech/diagrams/structure-lambda-example-production](https://demo.kronicle.tech/components?platformId=kubernetes)        | Shows the AWS resources belonging to a particular "component"                                       |

See these plugins for more information on auto-generating diagrams:

1. [Kubernetes plugin](/docs/plugins/kubernetes/)
2. [AWS plugin](/docs/plugins/aws/)
