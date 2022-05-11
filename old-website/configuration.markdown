---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Configuration
nav_order: 5
permalink: /configuration
has_toc: true
wide: true
---

# Configuration
{: .no_toc }

Kronicle is configured using environment variables.  This page describes the supported environment variables.  The 
environment variables can be used regardless of whether you are running Kronicle on: a) docker-compose, 
b) AWS ECS+Fargate, c) Kubernetes or d) some other form of Docker image based hosting.   


## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}


## Kronicle App Config

This table details the environment variables that can be passed into the Docker container running the Kronicle App.  

| Environment Variable            | Description                                                                                                                                                                                                                | Example Value                                    | Required? |
|---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-----------|
| ANALYTICS_PLAUSIBLE_ENABLED     | Enables an integration with https://plausible.io.  Plausible is a privacy centric, cookieless, low cost web analytics SaaS offering.                                                                                       | true                                             | Optional  |
| ANALYTICS_PLAUSIBLE_DATA_DOMAIN | When the Plausible integration is enabled, this configures the domain name that web traffic will be associated with in Plausible.                                                                                          | demo.kronicle.tech                               | Optional  |
| CLIENT_SIDE_SERVICE_BASE_URL    | Sets the domain name that web browsers can use to access the Kronicle Service.  Both Kronicle App and Kronicle Service need to be accessible from the web browsers of people using Kronicle                                | https://demo.kronicle.tech                       | Mandatory |
| INTRO_TITLE                     | Kronicle App's home page includes intro section.  This controls the title to show for that section                                                                                                                         | organization A's Tech Stack                      | Optional  |
| INTRO_MARKDOWN                  | This controls the main text to show in the intro section on Kronicle App's home page.  It supports full GitHub Flavored Markdown syntax, meaning formatting, hyperlinks, bullet point lists, tables etc. are all supported | Welcome to organization A's instance of Kronicle | Optional  |


## Kronicle Service Config

Kronicle's backend service has a plugin based architecture.  See below for the environment variables that can be used
to configure some of those plugins.


## GitHub Plugin

The GitHub plugin is used to: 

1. Auto-discover GitHub repos containing `/kronicle.yaml` metadata files
2. Clone those repos to analyze their contents

The plugin can find Git repos in three different ways: 

1. Load all repos that a GitHub access token has been granted access to
2. Load all repos under a specific GitHub organization
2. Load all repos under a specific GitHub user account (personal repos)

The three approaches can be mix and matched and the plugin allows multiple access tokens, organizations and users to be
configured.  

These environment variables are used to configure the plugin:

| Environment Variable                                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Example Value    | Required? |
|------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|-----------|
| PLUGINS_GITHUB_ENABLED                                     | Set to "true" to enable the plugin                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | true             | Optional  |   
| PLUGINS_GITHUB_ACCESS_TOKENS_{index}_USERNAME              | This is used to configure Kronicle to automatically scan all the Git repos that the specified user account has been granted access to.                                                                                                                                                                                                                                                                                                                                                                                  | some-github-user | Optional  |   
| PLUGINS_GITHUB_ACCESS_TOKENS_{index}_VALUE                 | This setting must be used when the PLUGINS_GITHUB_ACCESS_TOKENS_{index}_USERNAME setting is used.  Care should be taken with what permissions are granted on GitHub for the access token.  If the access token is granted access to any private repos, regardless of what organization or user owns those private repos, then Kronicle Service will have access to those private repos too.                                                                                                                             | ghp_1234567890   | Optional  |   
| PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCOUNT_NAME          | This is used to configure Kronicle to automatically scan all the Git repos owned by a particular organization on GitHub, looking for `kronicle.yaml` files.                                                                                                                                                                                                                                                                                                                                                             | kronicle-tech    | Optional  |
| PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCESS_TOKEN_USERNAME | This is used with the PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCOUNT_NAME setting but it optional.  Without it, Kronicle Service will call the GitHub API anonymously.  The setting contains the username of a GitHub user.  Specifying this setting can be helpful as it enables Kronicle Service to authenticate with the GitHub API, which reduces the rate limiting that the API performs.                                                                                                                            | some-github-user | Optional  |   
| PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCESS_TOKEN_VALUE    | This setting must be used when the PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCESS_TOKEN_USERNAME setting is used.  In contains the GitHub access token (PAT) for the GitHub used specified in the PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCESS_TOKEN_USERNAME setting.  Care should be taken with what permissions are granted on GitHub for the access token.  If the access token is granted access to any of the GitHub organization's private repos, then Kronicle Service will have access to those private repos too. | ghp_1234567890   | Optional  |   
| PLUGINS_GITHUB_USERS_{index}_ACCOUNT_NAME                  | Similar to the PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCOUNT_NAME setting but configures Kronicle Service to retrieve repos for a GutHub user rather han a GitHub organization                                                                                                                                                                                                                                                                                                                                           | some-github-user | Optional  |   
| PLUGINS_GITHUB_USERS_{index}_ACCESS_TOKEN_USERNAME         | Similar to the PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCESS_TOKEN_USERNAME setting.                                                                                                                                                                                                                                                                                                                                                                                                                                      | some-github-user | Optional  |
| PLUGINS_GITHUB_USERS_{index}_ACCESS_TOKEN_VALUE            | Similar to the PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCESS_TOKEN_VALUE setting.  Care should be taken with what permissions are granted on GitHub for the access token.  If the access token is granted access to any of the GitHub user's private repos, then Kronicle Service will have access to those private repos too.                                                                                                                                                                                            | ghp_1234567890   | Optional  |

### Example of granting access to two GitHub organizations

Here is an example of the environment variables needed to configure Kronicle to load all the Git repos for two
independent GitHub organizations:

```shell
PLUGINS_GITHUB_ORGANIZATIONS_0_ACCOUNT_NAME=some-github-organization
PLUGINS_GITHUB_ORGANIZATIONS_0_ACCESS_TOKEN_USERNAME=some-github-user
PLUGINS_GITHUB_ORGANIZATIONS_0_ACCESS_TOKEN_VALUE=gpp_example123

PLUGINS_GITHUB_ORGANIZATIONS_1_ACCOUNT_NAME=another-github-organization
PLUGINS_GITHUB_ORGANIZATIONS_1_ACCESS_TOKEN_USERNAME=another-github-user
PLUGINS_GITHUB_ORGANIZATIONS_1_ACCESS_TOKEN_VALUE=gpp_example456
```

### Example of granting access to a GitHub organization's repos via a GitHub user account

Here is an example of configuring Kronicle to load all Git repos via a `machine` GitHub account.  This approach will 
grant Kronicle access to all the repos that the user account has been _explicitly_ granted access to.  That includes 
access granted directly to the user account and access granted via a GitHub team.

```shell
PLUGINS_GITHUB_ACCESS_TOKENS_0_USERNAME=some-github-user
PLUGINS_GITHUB_ACCESS_TOKENS_0_VALUE=gpp_example123
```


## GitLab Plugin

The GitLab plugin is similar to the GitHub one.  

The plugin can find Git repos in three different ways:

1. Load all repos that a GitLab access token has been granted access to
2. Load all repos under a specific GitLab group
2. Load all repos under a specific GitLab user account (personal repos)

Environment variables supported by the plugin:

| Environment Variable                                           | Description                                                                                                                                                                                                                                                                                                | Example Value            | Required? |
|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|-----------|
| PLUGINS_GITLAB_ENABLED                                         | Set to "true" to enable the plugin                                                                                                                                                                                                                                                                         | true                     | Optional  |   
| PLUGINS_GITLAB_HOSTS_{index}_BASE_URL                          | The base URL of a GitLab instance.  Can be use used with https://gitlab.com and also a self-hosted GitLab instance                                                                                                                                                                                         | some-gitlab-user         | Optional  |   
| PLUGINS_GITLAB_HOSTS_{index}_ACCESS_TOKENS_{index}_VALUE       | The access token.  Care should be taken with what permissions are granted on GITLAB for the access token.  If the access token is granted access to any private repos, regardless of what organization or user owns those private repos, then Kronicle Service will have access to those private repos too | some-gitlab-access-token | Optional  |   
| PLUGINS_GITLAB_HOSTS_{index}_GROUPS_{index}_PATH               | Namepath of a GitLab group.  The plugin will load all GitLab repos under this group that the specified access token has been granted access to                                                                                                                                                             | kronicle-tech            | Optional  |
| PLUGINS_GITLAB_HOSTS_{index}_GROUPS_{index}_ACCESS_TOKEN_VALUE | The access token                                                                                                                                                                                                                                                                                           | some-gitlab-access-token | Optional  |   
| PLUGINS_GITLAB_HOSTS_{index}_USERS_{index}_USERNAME            | Name of a GitLab group.  The plugin will load all of this user's personal GitLab repos that the specified access token has been granted access to                                                                                                                                                          | some-gitlab-user         | Optional  |   
| PLUGINS_GITLAB_HOSTS_{index}_USERS_{index}_ACCESS_TOKEN_VALUE  | The access token                                                                                                                                                                                                                                                                                           | some-gitlab-access-token | Optional  |


## BitBucket Server Plugin

This plugin supports "Bitbucket Server" which is the self-hosted version of Bitbucket.  It is not compatible with the 
cloud version of Bitbucket, which has a very different API to Bitbucket Server.  

Environment variables supported by the plugin:

| Environment Variable                            | Description                                                                                                       | Example Value                       | Required? |
|-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|-------------------------------------|-----------|
| PLUGINS_BITBUCKET_SERVER_ENABLED                | Set to "true" to enable the plugin                                                                                | true                                | Optional  |   
| PLUGINS_BITBUCKET_SERVER_HOSTS_{index}_BASE_URL | The base URL of a self-hosted Bitbucket Server instance                                                           | https://bitbucketserver.example.com | Optional  |   
| PLUGINS_BITBUCKET_SERVER_HOSTS_{index}_USERNAME | Username for calling the Bitbucket Server's API.  The plugin will load all Git repos that this user has access to | some-bitbucket-server-user          | Optional  |   
| PLUGINS_BITBUCKET_SERVER_HOSTS_{index}_PASSWORD | The password for the user account                                                                                 | some-bitbucket-server-user-password | Optional  |


## Excluding certain Git repos

This environment variable can be used to prevent Kronicle for loading certain Git repos, regardless of which Kronicle
plugin has found these Git repos:

| Environment Variable                   | Description                                                                                                                                                                     | Example Value                                                        | Required? |
|----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|-----------|
| REPO_FINDERS_IGNORED_REPOS_{index}_URL | Configures Git repos that Kronicle Service should ignore.  Multiple entries can be configured.  `{index}` should start from zero and be incremented by 1 for each Git repo URL. | https://github.com/kronicle-tech/kronicle-metadata-repo-template.git | Optional  |


## AWS Plugin

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


## Zipkin Plugin

Kronicle can use a Zipkin server instance to:

1. Find dependencies between components in your stack
2. Calculate response times for your components' endpoints

The plugin is configured via this environment variable:

| Environment Variable    | Description                                                                        | Example Value                          | Required? |
|-------------------------|------------------------------------------------------------------------------------|----------------------------------------|-----------|
| PLUGINS_ZIPKIN_ENABLED  | Set to "true" to enable the plugin                                                 | true                                   | Optional  |   
| PLUGINS_ZIPKIN_BASE_URL | This is optional.  Specifies the base URL of a [Zipkin](http://zipkin.io) instance | http://zipkin.zipkin.svc.cluster.local | Optional  |   


## Datadog Plugin

This plugin uses Datadog's Service Dependencies API endpoint to find dependencies between components in your stack.  

The plugin is configured via these environment variables:

| Environment Variable                              | Description                                                                                                              | Example Value             | Required? |
|---------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|---------------------------|-----------|
| PLUGINS_DATADOG_ENABLED                           | Set to "true" to enable the plugin                                                                                       | true                      | Optional  |   
| PLUGINS_DATADOG_BASE_URL                          | This is optional.  Specifies the base URL for Datadog's APIs.  Can be used to point at Datadog's EU instance of its APIs | https://api.datadoghq.com | Optional  |   
| PLUGINS_DATADOG_API_KEY                           | Datadog API key                                                                                                          | some-api-key              | Optional  |   
| PLUGINS_DATADOG_APPLICATION_KEY                   | This is optional.  Specifies the base URL for Datadog's APIs.  Can be used to point at Datadog's EU instance of its APIs | some-application-key      | Optional  |   
| PLUGINS_DATADOG_DEPENDENCIES_ENVIRONMENTS_{index} | The names of 1 or more environments configured in Datadog for which service dependencies should be fetched               | production                | Mandatory |   


## SonarQube Plugin

Kronicle can load metrics like unit test code coverage from SonarQube.  It supports both the cloud and self-hosted
versions of SonarQube.

The plugin can be configured with these environment variables:

| Environment Variable                    | Description                                                                                                                                                                                                                                                                                                                      | Example Value         | Required? |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|-----------|
| PLUGINS_SONARQUBE_ENABLED               | Set to "true" to enable the plugin                                                                                                                                                                                                                                                                                               | true                  | Optional  |   
| PLUGINS_SONARQUBE_BASE_URL              | This is optional.  Specifies the base URL of a SonarQube instance to retrieve code coverage metrics from.  It supports both self-hosted instances of SonarQube and also https://sonarcloud.io                                                                                                                                    | https://sonarcloud.io | Optional  |
| PLUGINS_SONARQUBE_ORGANIZATIONS_{index} | This is optional.  Specifies 1 or more SonarQube organizations to retrieve code coverage metrics from.  It specifies the base URL of a SonarQube instance to retrieve code coverage figures from.  Multiple entries can be configured.  `{index}` should start from zero and be incremented by 1 for each SonarQube organization | kronicle-tech         | Optional  |   


## Key Software Plugin

Kronicle can detect the software dependencies in nodejs and Gradle codebases.  Typical codebases can contain 10s to 
1000s of dependencies.  The Key Software plugin can be used to summarise software dependencies into a list of 
"key dependencies".  For example, dependencies like Angular, React, Spring Boot, Micronaut etc. might be "key software"
in a particular tech stack.  

The plugin is configured via these environment variables:

| Environment Variable                                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Example Value                | Required? |
|----------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------|-----------|
| PLUGINS_KEY_SOFTWARE_DEFAULT_RULES_ENABLED               | Used to disable Kronicle's built-in key software rules                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | false                        | Optional  |   
| PLUGINS_KEY_SOFTWARE_RULES_{index}_SOFTWARE_NAME_PATTERN | This is used to tell Kronicle about "key software" in your tech stack.  This could be used to configure software like Gradle, Spring Boot, Micronaut, React, Vue.js etc. as being important software in your tech stack.  You can configure multiple rules.  The `{index}` in the environment name should start from 0 and be incremented for each rule.  Contains a regular expression to use to match a particular piece of software being used by a component.  For Java based components, this would a regular expression to make the "groupId:artifactId" of a JAR.  For a node.js based component, this would be a regular expression to match an npm package name | ^io.micronaut:micronaut-bom$ | Optional  |   
| PLUGINS_KEY_SOFTWARE_RULES_{index}_NAME                  | This is paired with the SOFTWARE_NAME_PATTERN environment variable.  It configures what name Kronicle should show in Kronicle App when a piece of software matches the associated SOFTWARE_NAME_PATTERN.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Micronaut                    | Optional  |


## Next Section

The next section of the getting started guide is [Metadata Files](/metadata-files).
