---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Kronicle
nav_order: 1
permalink: /
---

# Kronicle

Kronicle is an open source platform for development teams and tech organizations to document and visualise: 

1. The components in their tech stack 
2. The teams that own those components.  

Kronicle has a heavy focus on automation, it combines: 

1. Human authored YAML files that are committed to the same repos as the code components they describe
2. Information automatically gathered from places like: package.json and package-lock.json files in codebases, Gradle build scripts, Zipkin, AWS X-Ray etc.


## Live Demo

The easiest way to see Kronicle in action is to try the [Live Demo](https://demo.kronicle.tech). This is a real 
instance of Kronicle running on AWS ECS+Fargate and it is populated with a mix of real data from the Kronicle Project 
together and example data for the fictional "Kronicle Computers".

[Live Demo](https://demo.kronicle.tech){: .btn .btn-blue }


## Running Kronicle

See [Getting Started](/getting-started) for information on running Kronicle locally via docker-compose or deploying it 
to AWS or an existing Kubernetes cluster.  


## Plugins

Kronicle's backend service has a plugin based architecture.  See [Plugins](/plugins)
for a list of those plugins and see [Configuration](/configuration) for info on configuring each of Kronicle's plugins


## Walk-through

See the following screencast for a walkthrough of Kronicle's features:

[Kronicle Walk-through Video](https://youtu.be/xNvoxBmMQdk){: .btn .btn-blue }


## Code

See the following repo for Kronicle's source code:

[Kronicle code on GitHub](https://github.com/kronicle-tech/kronicle){: .btn .btn-blue }
