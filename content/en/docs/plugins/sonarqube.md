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
weight: 360
toc: true
---

Uses SonarQube's API to extract metrics for codebases/components.  Supports both the cloud-based SonarCloud and
self-hosted SonarQube instances.

Kronicle can load metrics like unit test code coverage from SonarQube.  It supports both the cloud and self-hosted
versions of SonarQube.

The plugin can be configured with these environment variables:

| Environment Variable                    | Description                                                                                                                                                                                                                                                                                                                      | Example Value         | Required? |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|-----------|
| PLUGINS_SONARQUBE_ENABLED               | Set to "true" to enable the plugin                                                                                                                                                                                                                                                                                               | true                  | Optional  |
| PLUGINS_SONARQUBE_BASE_URL              | This is optional.  Specifies the base URL of a SonarQube instance to retrieve code coverage metrics from.  It supports both self-hosted instances of SonarQube and also https://sonarcloud.io                                                                                                                                    | https://sonarcloud.io | Optional  |
| PLUGINS_SONARQUBE_ORGANIZATIONS_{index} | This is optional.  Specifies 1 or more SonarQube organizations to retrieve code coverage metrics from.  It specifies the base URL of a SonarQube instance to retrieve code coverage figures from.  Multiple entries can be configured.  `{index}` should start from zero and be incremented by 1 for each SonarQube organization | kronicle-tech         | Optional  |
