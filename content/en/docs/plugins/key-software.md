---
title: "Key Software"
description: "A plugin that summarises the key software used by codebases."
lead: "A plugin that summarises the key software used by codebases."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 511
toc: true
---

## Features

Kronicle can detect the software dependencies in nodejs and Gradle codebases.  Typical codebases can contain 10s to
1000s of dependencies.  The Key Software plugin can be used to summarise software dependencies into a list of
"key dependencies".  For example, dependencies like Angular, React, Spring Boot, Micronaut etc. might be "key software"
in a particular tech stack.

## Plugin configuration

The following environment variable are passed to the `kronicle-serice` container to configure the plugin


### Example configuration

{{< env-vars
"PLUGINS_KEY_SOFTWARE_DEFAULT_RULES_ENABLED=true"
"PLUGINS_KEY_SOFTWARE_RULES_0_SOFTWARE_NAME_PATTERN=^io.micronaut:micronaut-bom$"
"PLUGINS_KEY_SOFTWARE_RULES_0_NAME=Micronaut"
"PLUGINS_KEY_SOFTWARE_RULES_1_SOFTWARE_NAME_PATTERN=^core-js$"
"PLUGINS_KEY_SOFTWARE_RULES_1_NAME=core-js" >}}
{{< /env-vars >}}


### Optional environment variables

{{< env-vars "PLUGINS_KEY_SOFTWARE_DEFAULT_RULES_ENABLED=true" >}}
Used to disable Kronicle's built-in key software rules.  See the `key-software:` part of
https://github.com/kronicle-tech/kronicle/blob/main/service/src/main/resources/application.yml for the built-in rules
{{< /env-vars >}}

{{< env-vars "PLUGINS_KEY_SOFTWARE_RULES_{index}_SOFTWARE_NAME_PATTERN=^io.micronaut:micronaut-bom$" >}}
This is used to tell Kronicle about "key software" in your tech stack.  This could be used to configure software like
Gradle, Spring Boot, Micronaut, React, Vue.js etc. as being important software in your tech stack.  You can configure
multiple rules.

The `{index}` in the environment name should start from 0 and be incremented for each rule.

It contains a regular expression to use to match a particular piece of software being used by a component.  For Java
based components, this would a regular expression to make the "groupId:artifactId" of a JAR.  For a node.js based
components, this would be a regular expression to match an npm package name
{{< /env-vars >}}

{{< env-vars "PLUGINS_KEY_SOFTWARE_RULES_{index}_NAME=Micronaut" >}}
This is paired with the SOFTWARE_NAME_PATTERN environment variable.  It configures what name Kronicle should show in
Kronicle App when a piece of software matches the associated SOFTWARE_NAME_PATTERN.
{{< /env-vars >}}
