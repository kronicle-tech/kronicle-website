---
title: "Datadog"
description: "A plugin that integrates with Datadog."
lead: "A plugin that integrates with Datadog."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 504
toc: true
---

## Features


Fetches service/component dependencies from Datadog's Tracing API.


## Plugin configuration

The following environment variable are passed to the `kronicle-serice` container to configure the plugin


### Example configuration

{{< env-vars
"PLUGINS_DATADOG_ENABLED=true"
"PLUGINS_DATADOG_BASE_URL=https://bitbucketserver1.example.com"
"PLUGINS_DATADOG_API_KEY=some-bitbucket-server-user"
"PLUGINS_DATADOG_APPLICATION_KEY=some-bitbucket-server-user-password"
"PLUGINS_DATADOG_DEPENDENCIES_ENVIRONMENTS_0=staging"
"PLUGINS_DATADOG_DEPENDENCIES_ENVIRONMENTS_1=production" >}}
{{< /env-vars >}}


### Mandatory environment variables

{{< env-vars "PLUGINS_DATADOG_ENABLED=true" >}}
Set to "true" to enable the plugin
{{< /env-vars >}}

{{< env-vars "PLUGINS_DATADOG_BASE_URL=https://api.datadoghq.com" >}}
This is optional.  Specifies the base URL for Datadog's APIs.  Can be used to point at Datadog's EU instance of its APIs
{{< /env-vars >}}

{{< env-vars "PLUGINS_DATADOG_API_KEY=some-api-key" >}}
Datadog API key
{{< /env-vars >}}

{{< env-vars "PLUGINS_DATADOG_APPLICATION_KEY=some-application-key" >}}
Datadog application key
{{< /env-vars >}}

{{< env-vars "PLUGINS_DATADOG_DEPENDENCIES_ENVIRONMENTS_{index}=production" >}}
The names of 1 or more environments configured in Datadog for which service dependencies should be fetched
{{< /env-vars >}}
