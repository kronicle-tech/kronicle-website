---
title: "Zipkin"
description: "A plugin that fetches service dependencies and other trace data from Zipkin's API."
lead: "A plugin that fetches service dependencies and other trace data from Zipkin's API."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 619
toc: true
---

## Features

Calls Zipkin's API endpoints to find dependencies between components/services in your stack.

The plugin uses Zipkin's Trace API endpoint rather than the usual Dependencies API endpoint, in order to gather more
detailed dependencies data from Zipkin.

Kronicle can use a Zipkin server instance to:

1. Find dependencies between components in your stack
2. Calculate response times for your components' endpoints


## Plugin configuration

The following environment variable are passed to the `kronicle-serice` container to configure the plugin


### Example configuration

{{< env-vars
"PLUGINS_ZIPKIN_ENABLED=true"
"PLUGINS_ZIPKIN_BASE_URL=https://zipkin.example.com" >}}
{{< /env-vars >}}


### Mandatory environment variables

{{< env-vars "PLUGINS_SONARQUBE_ENABLED=true" >}}
Set to "true" to enable the plugin
{{< /env-vars >}}

{{< env-vars "PLUGINS_ZIPKIN_BASE_URL=https://zipkin.example.com" >}}
Specifies the base URL of a [Zipkin](http://zipkin.io) instance
{{< /env-vars >}}
