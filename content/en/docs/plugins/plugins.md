---
title: "Plugins"
description: "There are a number of plugins for Kronicle."
lead: "The following plugins are available for Kronicle and come bundled in the Docker image for Kronicle's backend service."
date: 2020-11-12T15:22:20+01:00
lastmod: 2020-11-12T15:22:20+01:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 210
toc: true
layout: plugins
url: "/docs/plugins/"
---

## Integration plugins

<div class="row row-cols-1 row-cols-md-2 g-4">
  <div class="col">
    <div class="card" style="border-color: #6c757d; min-height: 20rem;">
      <div class="card-body">
        <div class="text-end">
          <img src="/images/third-party-logos/aws/powered-by-aws-white.png" alt="AWS" width="100">
        </div>
        <h5 class="card-title d-block float-right">
          AWS
        </h5>
        <p class="card-text">Loads tagged AWS resources into the component catalog.  Loads the status of Synthetics Canaries into the environments dashboard.</p>
        <a href="/docs/plugins/aws/" class="btn btn-primary">More info</a>
      </div>
    </div>
  </div>
</div>

## Git hosting and build job plugins

<div class="row row-cols-1 row-cols-md-2 g-4">
  <div class="col">
    <div class="card" style="border-color: #6c757d; min-height: 20rem;">
      <div class="card-body">
        <h5 class="card-title d-block float-right">
          Bitbucket Server
        </h5>
        <p class="card-text">Finds Git repos that contain <b>kronicle.yaml</b> files</p>
        <a href="/docs/plugins/bitbucket-server/" class="btn btn-primary">More info</a>
      </div>
    </div>
  </div>
</div>

## GitHub Plugin

<img src="/images/third-party-logos/github/GitHub_Logo_White.png" width="200">

Uses GitHub's APIs to find Git repos containing a `kroncile.yaml` file.

The plugin can search for Git Repos by:

1. GitHub organisation
2. GitHub user
3. GitHub personal access token

See the [Configuration page](/configuration) for information on how to enable and configure the plugin via environment
variables.


## GitLab Plugin

<img src="/images/third-party-logos/gitlab/gitlab-logo-white-rgb.svg" width="200" height="60">

Uses the APIs of GitLab's platform APIs to find Git repos containing a `kroncile.yaml` file.  Supports
https://gitlab.com and self-hosted GitLab instances.

The plugin can search for Git Repos by:

1. GitLab group
2. GitLab user
3. GitLab access token

See the [Configuration page](/configuration) for information on how to enable and configure the plugin via environment
variables.


## Bitbucket Server Plugin

Uses the Bitbucket Server's APIs to find Git repos containing a `kroncile.yaml` file.

Only supports self-hosted Bitbucket Server instances and not the cloud version of Bitbucket, which has an incompatible
API.

See the [Configuration page](/configuration) for information on how to enable and configure the plugin via environment
variables.


## AWS Plugin

<img src="/images/third-party-logos/aws/powered-by-aws-white.png" width="200" style="margin-top: 15px; margin-bottom: 15px">

Features of the AWS plugin:

1. Fetches the high-level details of the AWS managed resources in one or more AWS accounts and adds them to Kronicle's component catalog as components
2. Fetches service dependencies from AWS X-Ray and loads them into Kronicle

See the [Configuration page](/configuration) for information on how to enable and configure the plugin via environment
variables.


## Git Plugin

<img src="/images/third-party-logos/git/Git-Logo-White.png" width="200" style="margin-top: 15px; margin-bottom: 15px">

Clones Git repos found by the GitHub, GitLab and Bitbucket Server plugins.  Git repo clones are used by other plugins like the OpenAPI and Node.js plugins.

The plugin also summarises the details of committers to Git repos, the age of the Git repos etc.


## Datadog Plugin

Fetches service/component dependencies from Datadog's Tracing API.

See the [Configuration page](/configuration) for information on how to enable and configure the plugin via environment
variables.


## Zipkin Plugin

Calls Zipkin's API endpoints to find dependencies between components/services in your stack.

The plugin uses Zipkin's Trace API endpoint rather than the usual Dependencies API endpoint, in order to gather more
detailed dependencies data from Zipkin.

See the [Configuration page](/configuration) for information on how to enable and configure the plugin via environment
variables.


## Node.js Plugin

Searches cloned Git repos for `package.json` and `package-lock.json` files.  Finds all the NPM packages used by each
Git repo, including the names and versions of those NPM packages.


## Gradle Plugin

Searches cloned Git repos for Gradle build scripts.  Processes those build scripts - without executing them - to
discover all software dependencies of those codebases.


## OpenAPI Plugin

Finds JSON and YAML format OpenAPI spec files in cloned Git repos and loads those OpenAPI specs into Kronicle.  Can
also download OpenAPI specs from URLs configured in `kronicle.yaml` files.

Any found/download OpenAPI specs are loaded into Kronicle and can be viewed via Kronicle's web UI.


## SonarQube Plugin

Uses SonarQube's API to extract metrics for codebases/components.  Supports both the cloud-based SonarCloud and
self-hosted SonarQube instances.

See the [Configuration page](/configuration) for information on how to enable and configure the plugin via environment
variables.


## Key Software Plugin

Takes the details of all the software dependencies found by the Node.js and Gradle plugins and creates a list of
"key software" used by each codebase.  Examples of key software could be Express, Spring Boot, AWS CDK etc and can be
customised via config.

See the [Configuration page](/configuration) for information on how to configure the plugin via environment variables.


## Java Import Plugin

Searches cloned Git repos for all Java import statements.  For each Git repo, creates a list of all the Java types
imported by those import statements.


## Lines of Code Plugin

Counts the number of lines of code by file extension in each Git repo.


## Manual Dependency Plugin

Extracts component/service dependencies from `kronicle.yaml` files and loads them into Kronicle.


## Readme Plugin

Finds and loads `README` files in the root of the cloned Git repos and loads them into Kronicle.


## To Do Plugin

Finds To Do comments like `// TODO:` in cloned Git repos and loads the details into Kronicle.  The details of every
found To Do comment can view viewed in Kronicle's web UI.                                                                                                                                                                                                      |
