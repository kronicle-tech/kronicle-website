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
weight: 720
url: "/docs/configuration/"
---


Kronicle is deployed as two Docker containers: This page describes the supported environment variables.  The

1. kronicle-app
2. kronicle-service

Config is passed to both containers via environment variables.


## Kronicle App Config

The `kronicle-app` container hosts Kronicle's web UI.  It is configured via these environment variables:

##### SERVER_SIDE_SERVICE_BASE_URL

**Mandatory:** Yes

**Example value:** `http://localhost:8090`

Sets the base URL that the `kronicle-app` container should use to connect to the HTTP port on the `kronicle-service`
container.

##### ANALYTICS_PLAUSIBLE_ENABLED

**Example value:** `true`

Enables an integration with https://plausible.io for web analytics.  Plausible is a privacy centric, cookieless, low cost web analytics
SaaS offering.

##### ANALYTICS_PLAUSIBLE_DATA_DOMAIN

**Example value:** `demo.kronicle.tech`

When the Plausible integration is enabled, this configures the domain name that web traffic will be associated with in
Plausible.

##### INTRO_TITLE

**Example value:** `Example Company`

Kronicle App's home page includes intro section.  This controls the title to show for that section

##### INTRO_MARKDOWN

**Example value:** `Welcome to Example Company's Kronicle instance`

This controls the main text to show in the intro section on Kronicle App's home page.  It supports full GitHub Flavored
Markdown syntax, meaning formatting, hyperlinks, bullet point lists, tables etc. are all supported


## Kronicle Service Config

Kronicle's backend service has a plugin based architecture.  See the individual pages for
[Kronicle's plugins](/docs/plugins/) for the environment variables each plugin supports.
