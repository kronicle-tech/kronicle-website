---
title: "GraphQL"
description: "A plugin that fetches GraphQL schemas and uses them to render GraphQL based API documentation."
lead: "A plugin fetches GraphQL schemas and uses them to render GraphQL based API documentation."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 290
toc: true
---

## Features

Fetches GraphQL schemas from URLs and from files in Git repos.  The GraphQL schemas are loaded into
Kronicle and can be viewed via Kronicle's web UI.


## Adding GraphQL schema details to a kronicle.yaml metadata file

GraphQL schemas can be set in a `/kronicle.yaml` file in a Git repo:

```yaml
components:
  - id: some-component
    name: Some Component
    type: some-component-type
    repo:
        url: https://git.example.com/some-repo
    # 1 or more GraphQL schemas can be specified
    graphQlSchemas:
      - url: https://demo.kronicle.tech/graphql
        description: |
          Example GraphQL endpoint URL
      - file: some-dir/example.graphql
        description: |
          Example GraphQL schema in the https://git.example.com/some-repo repo
```
