---
title : "Get Started"
description: "There are several ways to try Kronicle."
lead: "There are several ways to try Kronicle."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "get-started"
weight: 110
---

## Live Demo

[https://demo.kronicle.tech](https://demo.kronicle.tech) is a real instance of Kronicle running on AWS ECS+Fargate and
it is populated real data from the Kronicle Project.


## Docker Compose

Run Kronicle via Docker Compose.  The
[https://github.com/kronicle-tech/kronicle-docker-compose](https://github.com/kronicle-tech/kronicle-docker-compose)
repo contains a
[docker-compose.yaml](https://github.com/kronicle-tech/kronicle-docker-compose/blob/main/docker-compose.yaml) file
that can be used to run Docker locally.  The
[README.md](https://github.com/kronicle-tech/kronicle-docker-compose/blob/main/README.md) contains more information.


## Deploying to AWS using AWS CDK

The [https://github.com/kronicle-tech/kronicle-cdk-config](https://github.com/kronicle-tech/kronicle-cdk-config) repo
can be used to deploy Kronicle to an AWS account.  It deploys Kronicle to AWS ECS + AWS Fargate.  If you are familiar
with AWS CDK, then this repo is an easy way to deploy Kronicle to AWS.


## Kubernetes

The Kubernetes project provides Helm charts for deploying Kronicle to an existing Kubernetes cluster.  See
[Deploying to Kubernetes](deploying-to-kubernetes) for more information.
