---
title: "SonarQube"
description: "A plugins that fetches metrics like code coverage for codebases from SonarQube's API."
lead: "A plugins that fetches metrics like code coverage for codebases from SonarQube's API."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
toc: true
---

## Features

Uses SonarQube's API to extract metrics for codebases/components.  Supports both the cloud-based SonarCloud and
self-hosted SonarQube instances.

Kronicle can load metrics like unit test code coverage from SonarQube.  It supports both the cloud and self-hosted
versions of SonarQube.


## Plugin configuration

The following environment variable are passed to the `kronicle-serice` container to configure the plugin


### Example configuration

{{< env-vars
"PLUGINS_SONARQUBE_ENABLED=true"
"PLUGINS_SONARQUBE_BASE_URL=https://sonarcloud.io"
"PLUGINS_SONARQUBE_ORGANIZATIONS_0=some-sonarqube-org"
"PLUGINS_SONARQUBE_ORGANIZATIONS_1=another-sonarqube-org" >}}
{{< /env-vars >}}


### Mandatory environment variables

{{< env-vars "PLUGINS_SONARQUBE_ENABLED=true" >}}
Set to "true" to enable the plugin
{{< /env-vars >}}


### Optional environment variables

{{< env-vars "PLUGINS_SONARQUBE_BASE_URL=https://sonarcloud.io" >}}
This is optional.  Specifies the base URL of a SonarQube instance to retrieve code coverage metrics from.  It supports
both self-hosted instances of SonarQube and also https://sonarcloud.io
{{< /env-vars >}}

{{< env-vars "PLUGINS_SONARQUBE_ORGANIZATIONS_{index}=some-sonarqube-org" >}}
This is optional.  Specifies 1 or more SonarQube organizations to retrieve code coverage metrics from.  Multiple
entries can be configured.  `{index}` should start from zero and be incremented by 1 for each SonarQube organization
{{< /env-vars >}}
