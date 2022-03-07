---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Plugins
nav_order: 3
permalink: /plugins
has_toc: true
---

# Plugins
{: .no_toc }


## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}


## Kronicle Plugins

The following plugins are available for Kronicle and come bundled in the Docker image for Kronicle's backend service:


## Integration Plugins

| Plugin            | Description                                                                                                                                                                                                                                                               |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GitHub            | Calls GitHub's APIs for Git repos.  Used to auto-discover Git repos hosted on GitHub that contain a `kroncile.yaml` file                                                                                                                                                  |
| GitLab            | Calls GitLab's APIs for Git repos.  Used to auto-discover Git repos hosted on GitLab that contain a `kroncile.yaml` file.  Supports https://gitlab.com and self-hosted GitLab instances                                                                                   |
| Bitbucket Server  | Calls Bitbucket Server's APIs for Git repos.  Used to auto-discover Git repos hosted on Bitbucket Server that contain a `kroncile.yaml` file.  Only supports self-hosted Bitbucket Server instances and not the cloud version of Bitbucket, which has an incompatible API |
| Git               | Clones Git repos found by the GitHub, GitLab and Bitbucket Server plugins.  Git repo clones are used by other plugins like the OpenAPI and Node.js plugins                                                                                                                |
| Datadog           | Calls Datadog's Service Dependencies API endpoint to find dependencies between components/services in your stack                                                                                                                                                          |
| Zipkin            | Calls Zipkin's API endpoints to find dependencies between components/services in your stack                                                                                                                                                                               |
| Node.js           | Searches the cloned Git repos for `package.json` and `package-lock.json` files.  Finds all the NPM packages used by each Git repo, including the names and versions of those NPM packages                                                                                 |
| Gradle            | Searches the cloned Git repos for Gradle build scripts.  Processes those build scripts - without executing them - to discover all software dependencies of those codebases                                                                                                |
| OpenAPI           | Finds JSON and YAML format OpenAPI spec files in cloned Git repos and loads those OpenAPI specs into Kronicle.  Can also download OpenAPI specs from URLs configured in `kronicle.yaml` files                                                                             |
| SonarQube         | Calls the SonarQube's API to extract metrics for codebases/components.  Supports both the cloud-based SonarCloud and self-hosted SonarQube instances                                                                                                                      |


## Other Plugins

| Plugin            | Description                                                                                                                                                                                                                                                  |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Key Software      | Takes the details of all the software dependencies found by the Node.js and Gradle plugins and creates a list of "key software" used by each codebase.  Examples of key software could be Express, Spring Boot, AWS CDK etc and can be customised via config |
| Java Import       | Searches the cloned Git repos for all Java import statements.  For each Git repo, creates a list of all the Java types imported by those import statements                                                                                                   |
| Lines of Code     | Counts the number of lines of code by file extension in each Git repo                                                                                                                                                                                        |
| Manual Dependency | Extracts component/service dependencies from `kronicle.yaml` files                                                                                                                                                                                           |
| Readme            | Finds and loads `README` files in the root of the cloned Git repos                                                                                                                                                                                           |
| To Do             | Finds To Do comments like `// TODO:` in cloned Git repos                                                                                                                                                                                                     |


## Next Section

The next section of the getting started guide is [Configuration](/configuration).  
