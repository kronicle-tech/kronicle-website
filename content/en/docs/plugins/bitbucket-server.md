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
weight: 230
toc: true
---

Uses the Bitbucket Server's APIs to find Git repos containing a `kroncile.yaml` file.

Only supports self-hosted Bitbucket Server instances and not the cloud version of Bitbucket, which has an incompatible
API.

Environment variables supported by the plugin:

| Environment Variable                            | Description                                                                                                       | Example Value                       | Required? |
|-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|-------------------------------------|-----------|
| PLUGINS_BITBUCKET_SERVER_ENABLED                | Set to "true" to enable the plugin                                                                                | true                                | Optional  |
| PLUGINS_BITBUCKET_SERVER_HOSTS_{index}_BASE_URL | The base URL of a self-hosted Bitbucket Server instance                                                           | https://bitbucketserver.example.com | Optional  |
| PLUGINS_BITBUCKET_SERVER_HOSTS_{index}_USERNAME | Username for calling the Bitbucket Server's API.  The plugin will load all Git repos that this user has access to | some-bitbucket-server-user          | Optional  |
| PLUGINS_BITBUCKET_SERVER_HOSTS_{index}_PASSWORD | The password for the user account                                                                                 | some-bitbucket-server-user-password | Optional  |
