---
title : "Metadata Files"
description: "Using kronicle.yaml files to add metadata to Kronicle."
lead: "Using kronicle.yaml files to add metadata to Kronicle."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "metadata-files"
weight: 701
url: "/docs/metadata-files/"
---


## kronicle.yaml files for each Codebase

Kronicle is powered by `kronicle.yaml` files.  When using Kronicle, typically `kronicle.yaml` files are added to the
Git repos for each of an organisation's codebases.  When `kronicle.yaml` file is added to a codebase, the file
describes all the components in that repo.  The codebases could be for single page apps, microservices etc. but they
could also be Infrastructure as Code (IaC) codebases that hold Terraform, CDK etc. config for infrastructure.

The simplest way to do this is to create a file called `kronicle.yaml` at the root of a repo.  You can use either
of the following files as examples for what you can put in a repo's `kronicle.yaml` file:

1. [https://github.com/kronicle-tech/kronicle-metadata-codebase-template/blob/main/kronicle.yaml](https://github.com/kronicle-tech/kronicle-metadata-codebase-template/blob/main/kronicle.yaml)
2. [https://github.com/kronicle-tech/kronicle/blob/main/kronicle.yaml](https://github.com/kronicle-tech/kronicle/blob/main/kronicle.yaml)


If you want your CI build to validate your `kronicle.yaml` files to make sure they contain no syntax errors, you can
use
[https://github.com/kronicle-tech/kronicle-metadata-codebase-template](https://github.com/kronicle-tech/kronicle-metadata-codebase-template)
as a template for using a Gradle build script to validate the `kronicle.yaml` files.  This is an optional step.  The
`kronicle-metadata-codebase-template` repo includes:

| File                                                                                                                                              | Description                                                                                                                                                                                                                                                                        |
|---------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [README.md](https://github.com/kronicle-tech/kronicle-metadata-codebase-template/blob/main/README.md)                                             | Contains instructions for using the template repo                                                                                                                                                                                                                                  |
| [kronicle.yaml](https://github.com/kronicle-tech/kronicle-metadata-codebase-template/blob/main/kronicle.yaml)                                     | An example `kronicle.yaml` file with lots of comments                                                                                                                                                                                                                              |
| [build.gradle](https://github.com/kronicle-tech/kronicle-metadata-codebase-template/blob/main/build.gradle)                                       | A fragment of a Gradle build script that adds a validateKronicleMetadata build task that validates the contents of the `kronicle.yaml` file to make sure it contains no errors.  This can be used on a local machine and in a build job on your Continuous Integration (CI) server |
| [gradle/kronicle-metadata.gradle](https://github.com/kronicle-tech/kronicle-metadata-codebase-template/blob/main/gradle/kronicle-metadata.gradle) | A Gradle include file that's used by the build.gradle file to perform the validation of the `kronicle.yaml` file.                                                                                                                                                                  |


## kronicle.yaml files for areas and teams

Some types of metadata for Kronicle do nit fit well in codebase `kronicle.yaml` files.  Here's some examples of these
types of metadata:

* An area, which is a section or division of an organisation.
* A team.
* Component types.  Each organisation will have its own types of components.  E.g. microservices, databases, queues etc.  These component types are defined in a `kronicle.yaml` file.
* Platform.  Like component types, each organisation will have its own platforms.  E.g. kubernetes, AWS Fargate, AWS managed services, external services etc.

Typically, dedicated Git repos are created to hold `kronicle.yaml` file(s) for these types of metadata.  The
[https://github.com/kronicle-tech/kronicle-metadata-repo-template](https://github.com/kronicle-tech/kronicle-metadata-repo-template)
repo provides a template for creating these sorts of metadata repos.  The template repo contains:

| File                                                                                                                                          | Description                                                                                                                                                                                                                                                             |
|-----------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [README.md](https://github.com/kronicle-tech/kronicle-metadata-repo-template/blob/main/README.md)                                             | Contains instructions for using the template repo                                                                                                                                                                                                                       |
| [kronicle.yaml](https://github.com/kronicle-tech/kronicle-metadata-repo-template/blob/main/kronicle.yaml)                                     | An example `kronicle.yaml` file with lots of comments                                                                                                                                                                                                                   |
| [build.gradle](https://github.com/kronicle-tech/kronicle-metadata-repo-template/blob/main/build.gradle)                                       | A Gradle build script that includes a validateKronicleMetadata build task for validates the contents of the `kronicle.yaml` file to make sure it contains no errors.  This can be used on a local machine and in a build job on your Continuous Integration (CI) server |
| [gradle/kronicle-metadata.gradle](https://github.com/kronicle-tech/kronicle-metadata-repo-template/blob/main/gradle/kronicle-metadata.gradle) | A Gradle include file that's used by the build.gradle file to perform the validation of the `kronicle.yaml` file.                                                                                                                                                       |


## End of the Guide

This is the end of the getting started guide.  See the [Kronicle Walkthrough](https://youtu.be/xNvoxBmMQdk) video for
a general overview of Kronicle and the [Live Demo](http://demo.kronicle.tech) which is a real instance of Kronicle.
