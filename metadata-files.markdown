---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Metadata Files
nav_order: 3
permalink: /metadata-files
has_toc: true
---

# Metadata Files
{: .no_toc }


## Table of Contents
{: .no_toc .text-delta }

1. TOC
   {:toc}


## kronicle.yaml Files for each Codebase 

Kronicle is powered by `kronicle.yaml` files.  When using Kronicle, typically `kronicle.yaml` files are added to the
Git repos for each of an organisation's codebases.  When `kronicle.yaml` file is added to a codebase, the file
describes all the components in that repo.  The codebases could be for single page apps, microservices etc. but they
could also be Infrastructure as Code (IoC) codebases that hold Terraform, CDK etc. config for infrastructure.    

The https://github.com/kronicle-tech/kronicle-metadata-codebase-template repo provides a template for adding a
`kronicle.yaml` file to a codebase repo.  It includes:

| File | Description |
|---|---|
| [README.md](https://github.com/kronicle-tech/kronicle-metadata-codebase-template/blob/main/README.md) | Contains instructions for using the template repo |
| [kronicle.yaml](https://github.com/kronicle-tech/kronicle-metadata-codebase-template/blob/main/kronicle.yaml) | An example `kronicle.yaml` file with lots of comments |
| [build.gradle](https://github.com/kronicle-tech/kronicle-metadata-codebase-template/blob/main/build.gradle) | A fragment of a Gradle build script that adds a validateKronicleMetadata build task that validates the contents of the `kronicle.yaml` file to make sure it contains no errors.  This can be used on a local machine and in a build job on your Continuous Integration (CI) server | 
| [gradle/kronicle-metadata.gradle](https://github.com/kronicle-tech/kronicle-metadata-codebase-template/blob/main/gradle/kronicle-metadata.gradle) | A Gradle include file that's used by the build.gradle file to perform the validation of the `kronicle.yaml` file.  | 


## kronicle.yaml Files for areas and teams

Some types of metadata for Kronicle fit well in codebase `kronicle.yaml` files.  Here's some examples of these types of
metadata:

* An area, which is a section or division of an organisation.  
* A team.  
* Component types.  Each organisation will have its own types of components.  E.g. microservices, databases, queues etc.  These component types are defined in a `kronicle.yaml` file.
* Platform.  Like component types, each organisation will have its own platforms.  E.g. kubernetes, AWS Fargate, AWS managed services, external services etc.  

Typically, dedicated Git repos are created to hold `kronicle.yaml` file(s) for these types of metadata.  The
https://github.com/kronicle-tech/kronicle-metadata-repo-template repo provides a template for creating these sorts of
metadata repos.  The template repo contains:

| File | Description |
|---|---|
| [README.md](https://github.com/kronicle-tech/kronicle-metadata-repo-template/blob/main/README.md) | Contains instructions for using the template repo |
| [kronicle.yaml](https://github.com/kronicle-tech/kronicle-metadata-repo-template/blob/main/kronicle.yaml) | An example `kronicle.yaml` file with lots of comments |
| [build.gradle](https://github.com/kronicle-tech/kronicle-metadata-repo-template/blob/main/build.gradle) | A Gradle build script that includes a validateKronicleMetadata build task for validates the contents of the `kronicle.yaml` file to make sure it contains no errors.  This can be used on a local machine and in a build job on your Continuous Integration (CI) server | 
| [gradle/kronicle-metadata.gradle](https://github.com/kronicle-tech/kronicle-metadata-repo-template/blob/main/gradle/kronicle-metadata.gradle) | A Gradle include file that's used by the build.gradle file to perform the validation of the `kronicle.yaml` file.  | 


## Next Section

The next section of the getting started guide is [Configuration](/configuration).  It provides information on how to
configure Kronicle App and Kronicle Service via environment variables.  Some of those environment variables are used
to enable Kronicle to find and load the `kronicle.yaml` files added to your Git repos.   
