---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Kronicle
nav_order: 1
permalink: /
---

# Kronicle

Kronicle is an open source tool and dashboard for development teams and tech organizations to document and visualise 
the components in their tech stack and teams in their organization.  Kronicle automatically gathers data from the
following systems to supplement the info added to Kronicle manually: 

* Git repos
* Zipkin
* SonarQube


## Live Demo

The easiest way to see Kronicle in action is to try the [Live Demo](https://demo.kronicle.tech). This is a real 
instance of Kronicle running on Kubernetes on AWS and it is populated with a mix of real data from the Kronicle Project 
together with some from the fictional Kronicle Computers online shop.

[Live Demo](https://demo.kronicle.tech){: .btn .btn-green }


## Features

* Each component in your stack - software or infrastructure - has a `Kronicle.yaml` file added to the component’s own Git repo. This keeps the metadata close to the code, meaning it’s easy for engineers to both keep it up-to-date and to read it. Kronicle automatically discovers the `kronicle.yaml` files in all your repos and reloads the data in them every few minutes.  See https://github.com/kronicle-tech/kronicle/blob/main/kronicle.yaml for an example file. 
* Kronicle uses software called `Scanners` that search through the data in your `kronicle.yaml` files and then bring together additional data from external sources like your Git repos, traces in [Zipkin](https://zipkin.io), code coverage in SonarQube etc.
* Using the data loaded from `kronicle.yaml` files and data found by `Scanners`, Kronicle automatically creates a website that visualises all of your components, including all the components per area/team, architectural diagrams, response times per component etc.
* `kronicle.yaml` files also contain metadata for teams, areas of your organization, component types and platforms. Kronicle visualises this metadata for you, enabling your people to understand not only your tech stack but the teams that work on it as well.


## Getting Started

See the Getting Started guide for information on installing Kronicle on your own Kubernetes cluster:

[Getting Started](/getting-started){: .btn .btn-green }


## Code

See the following repo for Kronicle's source code:

[GitHub](https://github.com/kronicle-tech/kronicle){: .btn .btn-green }
