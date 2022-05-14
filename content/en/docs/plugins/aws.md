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

## Features

1. Fetches the high-level details of the AWS managed resources in one or more AWS accounts and adds them to Kronicle's component catalog as components
2. Fetches service dependencies from AWS X-Ray and loads them into Kronicle


## Plugin configuration

The following environment variable are passed to the `kronicle-serice` container to configure the plugin


## Example configuration

{{< env-vars
"PLUGINS_AWS_ENABLED=true"
"# Staging"
"PLUGINS_AWS_PROFILES_0_ENVIRONMENT_ID=staging"
"PLUGINS_AWS_PROFILES_0_REGIONS_0=us-west-1"
"PLUGINS_AWS_PROFILES_0_ACCESS_KEY_ID=some-access-key-id"
"PLUGINS_AWS_PROFILES_0_SECRET_ACCESS_KEY=some-secret-access-key"
"# Production"
"PLUGINS_AWS_PROFILES_1_ENVIRONMENT_ID=production"
"PLUGINS_AWS_PROFILES_1_REGIONS_0=us-west-1"
"PLUGINS_AWS_PROFILES_1_REGIONS_1=us-west-2"
"PLUGINS_AWS_PROFILES_1_ACCESS_KEY_ID=some-access-key-id"
"PLUGINS_AWS_PROFILES_1_SECRET_ACCESS_KEY=some-secret-access-key"
>}}


## Mandatory environment variables

{{< env-var name="PLUGINS_AWS_ENABLED" example="true"  >}}
Set to "true" to enable the plugin
{{< /env-var >}}

{{< env-var name="PLUGINS_AWS_PROFILES_{index}_ENVIRONMENT_ID" example="production"  >}}
Can be set to any value that represents one of your environments.  Must be in kebab-case
{{< /env-var >}}

{{< env-var name="PLUGINS_AWS_PROFILES_{index}_REGIONS_{index}" example="us-west-1"  >}}
One or more AWS regions can be specified for a profile
{{< /env-var >}}


## Optional environment variables

{{< env-var name="PLUGINS_AWS_PROFILES_{index}_ACCESS_KEY_ID" example="some-aws-access-key-id"  >}}
AWS credentials to use to call AWS APIs on behalf of an AWS account.  Credentials are not needed if the
kronicle-service container is deployed to an AWS container host like AWS ECS and you want to the same AWS account
the container is running in
{{< /env-var >}}

{{< env-var name="PLUGINS_AWS_PROFILES_{index}_SECRET_ACCESS_KEY" example="some-aws-secret-access-key"  >}}
See description for PLUGINS_AWS_PROFILES_{index}_ACCESS_KEY_ID
{{< /env-var >}}
