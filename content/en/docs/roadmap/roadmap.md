---
title: "Roadmap"
description: "Kronicle's short term development roadmap."
lead: "Kronicle's short term development roadmap."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "roadmap"
weight: 701
toc: true
url: "/docs/roadmap/"
---


| #   | Status      | Roadmap Item                                                                                                                                                                         | Notes                                                                                     |
|-----|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| 1   | Implemented | Add support for finding Git repos on GitLab                                                                                                                                          | Kronicle already supports GitHub and Bitbucket Service but GitLab is not yet supported.   |
| 2   | Implemented | Split the code in [Gradle Scanner](https://github.com/kronicle-tech/kronicle/tree/main/service/src/main/java/tech/kronicle/service/scanners/gradle) into its own independent library |                                                                                           |
| 3   | Implemented | Plugin architecture for Java code                                                                                                                                                    | Use something like [PF4J](https://github.com/pf4j/pf4j) to add plugin support to Kronicle |
| 4   | Implemented | AWS plugin that integrates with AWS X-Ray                                                                                                                                            | Create a plugin to collect component dependencies from AWS X-Ray                          |
| 5   | Implemented | Add support for AWS Resource Groups Tagging API to AWS plugin                                                                                                                        |                                                                                           |
| 6   | Implemented | Refactor advanced tracing anaylsis code in Zipkin plugin so it can be reused for any other plugins that collect tracing data                                                         |                                                                                           |
| 7   | Implemented | Hosting GraphQL schema based API documentation                                                                                                                                       |                                                                                           |
