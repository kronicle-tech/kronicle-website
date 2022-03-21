---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Roadmap
nav_order: 6
permalink: /roadmap
has_toc: false
---

# Roadmap


Here's the short term roadmap for Kronicle: 

| #   | Status      | Roadmap Item                                                                                                                                                                         | Notes                                                                                     |
|-----|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| 1   | Implemented | Add support for finding Git repos on GitLab                                                                                                                                          | Kronicle already supports GitHub and Bitbucket Service but GitLab is not yet supported.   |
| 2   | Implemented | Split the code in [Gradle Scanner](https://github.com/kronicle-tech/kronicle/tree/main/service/src/main/java/tech/kronicle/service/scanners/gradle) into its own independent library |                                                                                           |
| 3   | Implemented | Plugin architecture for Java code                                                                                                                                                    | Use something like [PF4J](https://github.com/pf4j/pf4j) to add plugin support to Kronicle |
| 4   | Implemented | AWS plugin that integrates with AWS X-Ray                                                                                                                                            | Create a plugin to collect component dependencies from AWS X-Ray                          |
| 5   | Implemented | Add support for AWS Resource Groups Tagging API to AWS plugin                                                                                                                        | Create a plugin to collect component dependencies from AWS X-Ray                          |
| 6   | Implemented | Refactor advanced tracing anaylsis code in Zipkin plugin so it can be reused for any other plugins that collect tracing data                                                         | Create a plugin to collect component dependencies from AWS X-Ray                          |
