---
title : "Configuration"
description: "Configuring Kronicle via environment variables."
lead: "Configuring Kronicle via environment variables."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "configuration"
weight: 401
url: "/docs/configuration/"
---


Kronicle is deployed as two Docker containers: This page describes the supported environment variables.  The

1. kronicle-app
2. kronicle-service

Config is passed to both containers via environment variables.


## Kronicle App Config

The `kronicle-app` container hosts Kronicle's web UI.  It is configured via these environment variables:

### Example configuration

{{< env-vars
"# Connect `kronicle-app` container to `kronicle-service` container"
"SERVER_SIDE_SERVICE_BASE_URL=http://localhost:8090"
"# Configure intro section on Kronicle UI home page"
"INTRO_TITLE=Example Company"
"INTRO_MARKDOWN=Welcome to Example Company's Kronicle instance"
"# Plausible analytics integration"
"ANALYTICS_PLAUSIBLE_ENABLED=true"
"ANALYTICS_PLAUSIBLE_DATA_DOMAIN=demo.kronicle.tech" >}}
{{< /env-vars >}}


### Mandatory environment variables

{{< env-vars "SERVER_SIDE_SERVICE_BASE_URL=http://localhost:8090" >}}
Sets the base URL that the `kronicle-app` container should use to connect to the HTTP port on the `kronicle-service`
container.
{{< /env-vars >}}


### Optional environment variables

{{< env-vars "INTRO_TITLE=Example Company" >}}
Kronicle App's home page has an intro section.  This controls the title to show for that section
{{< /env-vars >}}

{{< env-vars "INTRO_MARKDOWN=Welcome to Example Company's Kronicle instance" >}}
This controls the main text to show in the intro section on Kronicle App's home page.  It supports full GitHub Flavored
Markdown syntax, meaning formatting, hyperlinks, bullet point lists, tables etc. are all supported
{{< /env-vars >}}

{{< env-vars "ANALYTICS_PLAUSIBLE_ENABLED=true" >}}
Enables an integration with https://plausible.io for web analytics.  Plausible is a privacy centric, cookieless, low
cost web analytics SaaS offering.
{{< /env-vars >}}

{{< env-vars "ANALYTICS_PLAUSIBLE_DATA_DOMAIN=demo.kronicle.tech" >}}
When the Plausible integration is enabled, this configures the domain name that web traffic will be associated with in
Plausible.
{{< /env-vars >}}


## Kronicle Service Config

Kronicle's backend service has a plugin based architecture.  See the individual pages for
[Kronicle's plugins](/docs/plugins/) for the environment variables each plugin supports.
