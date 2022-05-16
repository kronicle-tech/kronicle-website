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
weight: 1
toc: true
layout: plugins
url: "/docs/plugins/"
---

## Integration plugins

<div class="row row-cols-1 row-cols-md-2 g-4">

{{< plugin id="aws" name="AWS" img-src="/images/third-party-logos/aws/powered-by-aws-white.png" img-bg-color="#212529" >}}
Loads tagged AWS resources into the component catalog.  Loads the status of Synthetics Canaries into the environments dashboard.
{{< /plugin >}}

{{< plugin id="datadog" name="Datadog" >}}
Fetches service dependencies from Datadog's Tracing API.
{{< /plugin >}}

{{< plugin id="sonarqube" name="SonarQube" img-src="/images/third-party-logos/sonarqube/SonarQube-logo-black.svg" img-bg-color="#fff" >}}
Uses SonarQube's API to extract metrics for codebases/components.  Supports both the cloud-based SonarCloud and
self-hosted SonarQube instances.
{{< /plugin >}}

{{< plugin id="zipkin" name="Zipkin" img-src="/images/third-party-logos/zipkin/zipkin_horizontal_white_bg.svg" >}}
Calls Zipkin's API endpoints to find dependencies between components/services in your stack.  The plugin can also
calculate response times for service endpoints
{{< /plugin >}}

</div>


## Git hosting and build job plugins

<div class="row row-cols-1 row-cols-md-2 g-4">

{{< plugin id="bitbucket-server" name="Bitbucket Server" img-bg-color="#212529" >}}
Uses Bitbucket Server's API to find Git repos containing a <b>kronicle.yaml</b> file
{{< /plugin >}}

{{< plugin id="github" name="GitHub" img-src="/images/third-party-logos/github/GitHub_Logo_White.png" img-bg-color="#212529" >}}
Uses GitHub's APIs to find Git repos containing a `kroncile.yaml` file
{{< /plugin >}}

{{< plugin id="gitlab" name="GitLab" img-src="/images/third-party-logos/gitlab/gitlab-logo-white-rgb.svg" img-bg-color="#212529" >}}
Uses the GitLab platform's APIs to find Git repos containing a `kroncile.yaml` file.  Supports
gitlab.com and self-hosted GitLab instances.
{{< /plugin >}}

</div>


## API documentation plugins

<div class="row row-cols-1 row-cols-md-2 g-4">

{{< plugin id="graphql" name="GraphQL" img-src="/images/third-party-logos/graphql/GraphQL-Logo-Wordmark-Rhodamine.svg" img-bg-color="#fff" >}}
Fetches GraphQL schemas from URLs and from files in Git repos.  The GraphQL schemas are loaded into
Kronicle and can be viewed via Kronicle's web UI.
{{< /plugin >}}

{{< plugin id="openapi" name="OpenAPI" img-src="/images/third-party-logos/openapi/OpenAPI_Pantone-768x204.png" img-bg-color="#fff" >}}
Finds OpenAPI spec files in Git repos and also downloads OpenAPI specs via URLs.  OpenAPI specs are loaded into
Kronicle and can be viewed via Kronicle's web UI.
{{< /plugin >}}

</div>


## Software dependency plugins

<div class="row row-cols-1 row-cols-md-2 g-4">

{{< plugin id="nodejs" name="Node.js" img-src="/images/third-party-logos/nodejs/nodejs-new-pantone-white.svg" img-bg-color="#212529" >}}
Searches cloned Git repos for `package.json` and `package-lock.json` files.  Finds all the NPM packages used by each
Git repo, including the names and versions of those NPM packages.
{{< /plugin >}}

{{< plugin id="gradle" name="Gradle" img-src="/images/third-party-logos/gradle/gradle-elephant-icon-dark-green.svg" img-bg-color="#fff" >}}
Searches cloned Git repos for Gradle build scripts.  Processes those build scripts - without executing them - to
discover all software dependencies of those codebases.
{{< /plugin >}}

</div>


## Codebase plugins

<div class="row row-cols-1 row-cols-md-2 g-4">

{{< plugin id="git" name="Git" img-src="/images/third-party-logos/git/Git-Logo-White.png" img-bg-color="#212529" >}}
Clones Git repos found by the GitHub, GitLab and Bitbucket Server plugins.  Git repo clones are used by other plugins
like the OpenAPI and Node.js plugins.  The plugin also summarises the details of committers to Git repos, the age of
the Git repos etc.
{{< /plugin >}}

{{< plugin id="java-import" name="Java Import" >}}
Searches cloned Git repos for all Java import statements.  For each Git repo, creates a list of all the Java types
imported by those import statements.
{{< /plugin >}}

{{< plugin id="key-software" name="Key Software" >}}
Takes the details of all the software dependencies found by the Node.js and Gradle plugins and creates a list of
"key software" used by each codebase.  Examples of key software could be Express, Spring Boot, AWS CDK etc and can be
customised via config.
{{< /plugin >}}

{{< plugin id="lines-of-code" name="Lines of Code" >}}
Counts the number of lines of code by file extension in each Git repo.
{{< /plugin >}}

{{< plugin id="manual-dependency" name="Manual Dependency" >}}
Extracts component dependencies from `kronicle.yaml` files and loads them into Kronicle.
{{< /plugin >}}

{{< plugin id="readme-plugin" name="Readme Plugin" >}}
Finds and loads `README` files in the root of the cloned Git repos and loads them into Kronicle.
{{< /plugin >}}

{{< plugin id="to-do" name="To Do" >}}
Finds comments like `// TODO:` in cloned Git repos and loads the details into Kronicle, to be viewed via Kronicle's web UI.
{{< /plugin >}}

</div>
