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


## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}


## Options for trying out Kronicle

There are several ways to try Kronicle.  See the sections below for details.  

## Live Demo

The [Live Demo](https://demo.kronicle.tech) is a real instance of Kronicle running on AWS ECS+Fargate and 
it is populated with a mix of real data from the Kronicle Project and data for the fictional "Kronicle Computers".  

The [homepage of the Live Demo](https://demo.kronicle.tech) contains info on some interesting parts of the demo.  


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


## Next Section

The next section of the getting started guide is [Metadata Files](/metadata-files).  
