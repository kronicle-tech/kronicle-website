---
title: "AWS"
description: "A plugin that integrates with AWS's APIs."
lead: "A plugin that integrates with AWS's APIs."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 220
toc: true
---

Features of the AWS plugin:

1. Fetches the high-level details of the AWS managed resources in one or more AWS accounts and adds them to Kronicle's component catalog as components
2. Fetches service dependencies from AWS X-Ray and loads them into Kronicle

Environment variables supported by the plugin:

| Environment Variable                           | Description                                                                              | Example Value              | Required? |
|------------------------------------------------|------------------------------------------------------------------------------------------|----------------------------|-----------|
| PLUGINS_AWS_ENABLED                            | Set to "true" to enable the plugin                                                       | true                       | Optional  |
| PLUGINS_AWS_PROFILES_{index}_ACCESS_KEY_ID     | AWS credentials to use to call AWS APIs on behalf of an AWS account                      | some-aws-access-key-id     | Optional  |
| PLUGINS_AWS_PROFILES_{index}_SECRET_ACCESS_KEY | AWS credentials to use to call AWS APIs on behalf of an AWS account                      | some-aws-secret-access-key | Optional  |
| PLUGINS_AWS_PROFILES_{index}_ENVIRONMENT_ID    | Can be set to any value that represents one of your environments.  Must be in kebab-case | production                 | Mandatory |
| PLUGINS_AWS_PROFILES_{index}_REGIONS_{index}   | One or more AWS regions can be specified for a profile                                   | us-west-1                  | Mandatory |
