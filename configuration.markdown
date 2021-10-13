---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Configuration
nav_order: 3
permalink: /configuration
has_toc: true
wide: true
---

# Configuration
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Helm Chart

See the [Getting Started] guide for information on the Helm chart provided for Kronicle.  This page details environment
variables that you can add to the Kubernetes containers running Kronicle App and Kronicle Service.  You can pass these
environment variables to the Helm chart like this: 

```shell
$ helm install kronicle kronicle/kronicle -n kronicle --create-namespace --set "app.env.INTRO_TITLE=My custom title" --set "service.env.ZIPKIN_BASE_URL=http://zipkin.zipkin.svc.cluster.local"
```

Multiple environment variables can be passed in for both the app and the service.  


## Kronicle App Config

This table details the environment variables that can be passed into the Docker container running the Kronicle App.  

| Environment Variable | Description | Example Value | Required? | Default Value |
|---|---|---|---|---|---|
| ANALYTICS_PLAUSIBLE_ENABLED | Enables an integration with https://plausible.io.  Plausible is a privacy centric, cookieless, low cost web analytics SaaS offering. | true | Optional | false |
| ANALYTICS_PLAUSIBLE_DATA_DOMAIN | When the Plausible integration is enabled, this configures the domain name that web traffic will be associated with in Plausible. | demo.kronicle.tech | Optional | N/A |
| CLIENT_SIDE_SERVICE_BASE_URL | Sets the domain name that web browsers can use to access the Kronicle Service.  Both Kronicle App and Kronicle Service need to be accessible from the web browsers of people using Kronicle | https://demo.kronicle.tech | Mandatory | N/A |
| INTRO_TITLE | Kronicle App's home page includes intro section.  This controls the title to show for that section | organization A's Tech Stack | Optional | Kronicle |
| INTRO_MARKDOWN | This controls the main text to show in the intro section on Kronicle App's home page.  It supports full GitHub Flavored Markdown syntax, meaning formatting, hyperlinks, bullet point lists, tables etc. are all supported | Welcome to organization A's instance of Kronicle | Optional | N/A |


## Kronicle Service Config

This table details the environment variables that can be passed into the Docker container running the Kronicle Service.

| Environment Variable | Description | Example Value | Required? | Default Value |
|---|---|---|---|---|---|
| REPO_FINDERS_GITHUB_PERSONAL_ACCESS_TOKENS_{index}_USERNAME | This is used to configure Kronicle to automatically scan all the Git repos that the specified user account has been granted access to.  | some-github-user | Optional | N/A |   
| REPO_FINDERS_GITHUB_PERSONAL_ACCESS_TOKENS_{index}_VALUE | This setting must be used when the REPO_FINDERS_GITHUB_PERSONAL_ACCESS_TOKENS_{index}_USERNAME setting is used.  Care should be taken with what permissions are granted on GitHub for the personal access token.  If the personal access token is granted access to any private repos, regardless of what organization or user owns those private repos, then Kronicle Service will have access to those private repos too.  | ghp_1234567890 | Optional | N/A |   
| REPO_FINDERS_GITHUB_ORGANIZATIONS_{index}_ACCOUNT_NAME | This is used to configure Kronicle to automatically scan all the Git repos owned by a particular organization on GitHub, looking for `kronicle.yaml` files.  | kronicle-tech | Optional | N/A |   
| REPO_FINDERS_GITHUB_ORGANIZATIONS_{index}_PERSONAL_ACCESS_TOKEN_USERNAME | This is used with the REPO_FINDERS_GITHUB_ORGANIZATIONS_{index}_ACCOUNT_NAME setting but it optional.  Without it, Kronicle Service will call the GitHub API anonymously.  The setting contains the username of a GitHub user.  Specifying this setting can be helpful as it enables Kronicle Service to authenticate with the GitHub API, which reduces the rate limiting that the API performs.  | some-github-user | Optional | N/A |   
| REPO_FINDERS_GITHUB_ORGANIZATIONS_{index}_PERSONAL_ACCESS_TOKEN_VALUE | This setting must be used when the REPO_FINDERS_GITHUB_ORGANIZATIONS_{index}_PERSONAL_ACCESS_TOKEN_USERNAME setting is used.  In contains the GitHub personal access token (PAT) for the GitHub used specified in the REPO_FINDERS_GITHUB_ORGANIZATIONS_{index}_PERSONAL_ACCESS_TOKEN_USERNAME setting.  Care should be taken with what permissions are granted on GitHub for the personal access token.  If the personal access token is granted access to any of the GitHub organization's private repos, then Kronicle Service will have access to those private repos too.  | ghp_1234567890 | Optional | N/A |   
| REPO_FINDERS_GITHUB_USERS_{index}_ACCOUNT_NAME | Similar to the REPO_FINDERS_GITHUB_ORGANIZATIONS_{index}_ACCOUNT_NAME setting but configures Kronicle Service to retrieve repos for a GutHub user rather han a GitHub organization | some-github-user | Optional | N/A |   
| REPO_FINDERS_GITHUB_USERS_{index}_PERSONAL_ACCESS_TOKEN_USERNAME | Similar to the REPO_FINDERS_GITHUB_ORGANIZATIONS_{index}_PERSONAL_ACCESS_TOKEN_USERNAME setting.  | some-github-user | Optional | N/A |   
| REPO_FINDERS_GITHUB_USERS_{index}_PERSONAL_ACCESS_TOKEN_VALUE | Similar to the REPO_FINDERS_GITHUB_ORGANIZATIONS_{index}_PERSONAL_ACCESS_TOKEN_VALUE setting.  Care should be taken with what permissions are granted on GitHub for the personal access token.  If the personal access token is granted access to any of the GitHub user's private repos, then Kronicle Service will have access to those private repos too.  | ghp_1234567890 | Optional | N/A |   
| REPO_FINDERS_IGNORED_REPOS_{index}_URL | Configures Git repos that Kronicle Service should ignore when searching any supported Git host (e.g. GitHub or Bitbucket Server) for Git repos that contain a `kronicle.yaml` file.  Multiple entries can be configured.  `{index}` should start from zero and be incremented by 1 for each Git repo URL.  | https://github.com/kronicle-tech/kronicle-metadata-repo-template.git | Optional | N/A |   
| KEY_SOFTWARE_RULES_{index}_SOFTWARE_NAME_PATTERN | This is used to tell Kronicle about "key software" in your tech stack.  This could be used to configure software like Gradle, Spring Boot, Micronaut, React, Vue.js etc. as being important software in your tech stack.  You can configure multiple rules.  The `{index}` in the environment name should start from 0 and be incremented for each rule.  Contains a regular expression to use to match a particular piece of software being used by a component.  For Java based components, this would a regular expression to make the "groupId:artifactId" of a JAR.  For a node.js based component, this would be a regular expression to match an npm package name.  See https://github.com/kronicle-tech/kronicle-argocd-config/blob/main/kronicle/values.yaml for some example configuration.  | ^io.micronaut:micronaut-bom$ | Optional | N/A |   
| KEY_SOFTWARE_RULES_{index}_NAME | This is paired with the SOFTWARE_NAME_PATTERN environment variable.  It configures what name Kronicle should show in Kronicle App when a piece of software matches the associated SOFTWARE_NAME_PATTERN.  | Micronaut | Optional | N/A |
| SONARQUBE_BASE_URL | This is optional.  Specifies the base URL of a SonarQube instance to retrieve code coverage metrics from.  It supports both self-hosted instances of SonarQube and also https://sonarcloud.io | https://sonarcloud.io | Optional | N/A |   
| SONARQUBE_ORGANIZATIONS_{index} | This is optional.  Specifies 1 or more SonarQube organizations to retrieve code coverage metrics from.  It specifies the base URL of a SonarQube instance to retrieve code coverage figures from.  Multiple entries can be configured.  `{index}` should start from zero and be incremented by 1 for each SonarQube organization.  | kronicle-tech | Optional | N/A |   
| ZIPKIN_BASE_URL | This is optional.  Specifies the base URL of a [Zipkin](http://zipkin.io) instance.  This instance is used both to record traces for requests to the Kronicle Service and also to query Zipkin to automatically find dependencies between components in your stach and to calculate response times for your components' endpoints.  | http://zipkin.zipkin.svc.cluster.local | Optional | N/A |   
| ZIPKIN_SAMPLE_RATE | The sample rate that Kroncile Service should use when sending traces to Zipkin.  | 0.01 (i.e 1%) | Optional | N/A |   
| OPENAPI_SPEC_CLEAR_EXISTING_SERVERS | Kronicle Service exposes an HTTP service endpoint under `/actuator/openapi`, powered by [Springdoc](https://springdoc.org), that serves the OpenAPI spec for the Kronicle Service.  This setting enables or disables including a `server` entry in that OpenAPI spec for the URL used to access the Kronicle Service.  This setting can be useful when Kronicle Service is behind a Kubernetes ingress and you want to show a custom server URL in the OpenAPI spec. | true | Optional | false |
| OPENAPI_SPEC_SERVERS_{index}_URL | This setting can be used to show a custom `server` entry in the OpenAPI spec served by Kronicle Service on its `/actuator/openapi` service endpoint.  Multiple entries can be configured.  `{index}` should start from zero and be incremented by 1 for each server.  | https://demo-service.kronicle.tech | Optional | N/A |
| OPENAPI_SPEC_SERVERS_{index}_DESCRIPTION | This setting is paired with the OPENAPI_SPEC_SERVERS_{index}_URL setting.  It controls the description to show for a custom server entry in Kronicle Service's OpenAPI spec.  | The demo instance of Kronicle Service | Optional | N/A |

