---
title : "Configuration"
description: "Using kronicle.yaml files to add metadata to Kronicle."
lead: "Using kronicle.yaml files to add metadata to Kronicle."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "configuration"
weight: 720
url: "/docs/configuration/"
---


Kronicle is configured using environment variables.  This page describes the supported environment variables.  The
environment variables can be used regardless of whether you are running Kronicle on: a) docker-compose,
b) AWS ECS+Fargate, c) Kubernetes or d) some other form of Docker image based hosting.


## Kronicle App Config

This table details the environment variables that can be passed into the Docker container running the Kronicle App.

| Environment Variable            | Description                                                                                                                                                                                                                | Example Value                                    | Required? |
|---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-----------|
| ANALYTICS_PLAUSIBLE_ENABLED     | Enables an integration with https://plausible.io.  Plausible is a privacy centric, cookieless, low cost web analytics SaaS offering.                                                                                       | true                                             | Optional  |
| ANALYTICS_PLAUSIBLE_DATA_DOMAIN | When the Plausible integration is enabled, this configures the domain name that web traffic will be associated with in Plausible.                                                                                          | demo.kronicle.tech                               | Optional  |
| CLIENT_SIDE_SERVICE_BASE_URL    | Sets the domain name that web browsers can use to access the Kronicle Service.  Both Kronicle App and Kronicle Service need to be accessible from the web browsers of people using Kronicle                                | https://demo.kronicle.tech                       | Mandatory |
| INTRO_TITLE                     | Kronicle App's home page includes intro section.  This controls the title to show for that section                                                                                                                         | organization A's Tech Stack                      | Optional  |
| INTRO_MARKDOWN                  | This controls the main text to show in the intro section on Kronicle App's home page.  It supports full GitHub Flavored Markdown syntax, meaning formatting, hyperlinks, bullet point lists, tables etc. are all supported | Welcome to organization A's instance of Kronicle | Optional  |


## Kronicle Service Config

Kronicle's backend service has a plugin based architecture.  See the individual pages for
[Kronicle's plugins](/docs/plugins/) for the environment variables each plugin supports.
