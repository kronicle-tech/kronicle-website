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
weight: 390
toc: true
---


Calls Zipkin's API endpoints to find dependencies between components/services in your stack.

The plugin uses Zipkin's Trace API endpoint rather than the usual Dependencies API endpoint, in order to gather more
detailed dependencies data from Zipkin.

Kronicle can use a Zipkin server instance to:

1. Find dependencies between components in your stack
2. Calculate response times for your components' endpoints

The plugin is configured via these environment variables:

| Environment Variable    | Description                                                                        | Example Value                          | Required? |
|-------------------------|------------------------------------------------------------------------------------|----------------------------------------|-----------|
| PLUGINS_ZIPKIN_ENABLED  | Set to "true" to enable the plugin                                                 | true                                   | Optional  |
| PLUGINS_ZIPKIN_BASE_URL | This is optional.  Specifies the base URL of a [Zipkin](http://zipkin.io) instance | http://zipkin.zipkin.svc.cluster.local | Optional  |
