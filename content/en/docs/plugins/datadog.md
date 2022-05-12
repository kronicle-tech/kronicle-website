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
weight: 240
toc: true
---


Fetches service/component dependencies from Datadog's Tracing API.

The plugin is configured via these environment variables:

| Environment Variable                              | Description                                                                                                              | Example Value             | Required? |
|---------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|---------------------------|-----------|
| PLUGINS_DATADOG_ENABLED                           | Set to "true" to enable the plugin                                                                                       | true                      | Optional  |
| PLUGINS_DATADOG_BASE_URL                          | This is optional.  Specifies the base URL for Datadog's APIs.  Can be used to point at Datadog's EU instance of its APIs | https://api.datadoghq.com | Optional  |
| PLUGINS_DATADOG_API_KEY                           | Datadog API key                                                                                                          | some-api-key              | Optional  |
| PLUGINS_DATADOG_APPLICATION_KEY                   | This is optional.  Specifies the base URL for Datadog's APIs.  Can be used to point at Datadog's EU instance of its APIs | some-application-key      | Optional  |
| PLUGINS_DATADOG_DEPENDENCIES_ENVIRONMENTS_{index} | The names of 1 or more environments configured in Datadog for which service dependencies should be fetched               | production                | Mandatory |
