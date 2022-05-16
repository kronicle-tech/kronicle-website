---
title: "Bitbucket Server"
description: "A plugin for Atlassian's Bitbucket Server."
lead: "A plugin for Atlassian's Bitbucket Server."
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

Uses the Bitbucket Server's APIs to find Git repos containing a `kroncile.yaml` file.

Only supports self-hosted Bitbucket Server instances and not the cloud version of Bitbucket, which has an incompatible
API.

## Plugin configuration

The following environment variable are passed to the `kronicle-serice` container to configure the plugin


### Example configuration

{{< env-vars
"PLUGINS_BITBUCKET_SERVER_ENABLED=true"
"PLUGINS_BITBUCKET_SERVER_HOSTS_0_BASE_URL=https://bitbucketserver1.example.com"
"PLUGINS_BITBUCKET_SERVER_HOSTS_0_USERNAME=some-bitbucket-server-user"
"PLUGINS_BITBUCKET_SERVER_HOSTS_0_PASSWORD=some-bitbucket-server-user-password"
"PLUGINS_BITBUCKET_SERVER_HOSTS_1_BASE_URL=https://bitbucketserver2.example.com"
"PLUGINS_BITBUCKET_SERVER_HOSTS_1_USERNAME=some-other-bitbucket-server-user"
"PLUGINS_BITBUCKET_SERVER_HOSTS_1_PASSWORD=some-other-bitbucket-server-user-password" >}}
{{< /env-vars >}}


### Mandatory environment variables

{{< env-vars "PLUGINS_BITBUCKET_SERVER_ENABLED=true" >}}
Set to "true" to enable the plugin
{{< /env-vars >}}

{{< env-vars "PLUGINS_BITBUCKET_SERVER_HOSTS_{index}_BASE_URL=https://bitbucketserver.example.com" >}}
The base URL of a self-hosted Bitbucket Server instance
{{< /env-vars >}}

{{< env-vars "PLUGINS_BITBUCKET_SERVER_HOSTS_{index}_USERNAME=some-bitbucket-server-user" >}}
Username for calling the Bitbucket Server's API.  The plugin will load all Git repos that this user has access to
{{< /env-vars >}}

{{< env-vars "PLUGINS_BITBUCKET_SERVER_HOSTS_{index}_PASSWORD=some-bitbucket-server-user-password" >}}
The password for the user account
{{< /env-vars >}}
