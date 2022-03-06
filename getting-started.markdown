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

There are several ways to try Kronicle: 

1. The [Live Demo](https://demo.kronicle.tech).  The Live Demo is real instance of Kronicle running on AWS ECS+Fargate and it is populated with a mix of real data from the Kronicle Project and data for the fictional "Kronicle Computers"
2. Run Kronicle via Docker Compose.  See [https://github.com/kronicle-tech/kronicle-docker-compose](https://github.com/kronicle-tech/kronicle-docker-compose) for information and steps to follow
3. Deploy Kronicle to AWS ECS+Fargate using AWS CDK.  See [https://github.com/kronicle-tech/kronicle-cdk-config](https://github.com/kronicle-tech/kronicle-cdk-config) for more information
4. Deploy Kronicle to an existing Kubernetes cluster.  See [Deploying to Kubernetes](deploying-to-kubernetes) for information


## Next Section

The next section of the getting started guide is [Metadata Files](/metadata-files).  It provides information on how to 
create `kronicle.yaml` files to describe the components in an organisation's tech stack and also to describe the areas
and teams working on and owning those components.
