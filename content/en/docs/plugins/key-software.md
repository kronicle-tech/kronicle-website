---
title: "Key Software"
description: "A plugin that summerises the key software used by codebases."
lead: "A plugin that summerises the key software used by codebases."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 310
toc: true
---


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
