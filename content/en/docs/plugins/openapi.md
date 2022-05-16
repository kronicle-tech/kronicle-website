---
title: "OpenAPI"
description: "A plugin that fetches OpenAPI specs and uses them to render OpenAPI based API documentation."
lead: "A plugin that fetches OpenAPI specs and uses them to render OpenAPI based API documentation."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 415
toc: true
---

## Features

Finds JSON and YAML format OpenAPI spec files in cloned Git repos and loads those OpenAPI specs into Kronicle.  Can
also download OpenAPI specs from URLs configured in `kronicle.yaml` files.

Any found/download OpenAPI specs are loaded into Kronicle and can be viewed via Kronicle's web UI.


## Adding OpenAPI spec details to a kronicle.yaml metadata file

OpenAPI specs can be set in a `/kronicle.yaml` file in a Git repo:

```yaml
components:
  - id: some-component
    name: Some Component
    type: some-component-type
    repo:
        url: https://git.example.com/some-repo
    # 1 or more GraphQL schemas can be specified
    openApiSpecs:
      - url: https://demo.kronicle.tech/openapi
        description: |
          Example OpenAPI spec served via a URL
      - file: some-dir/example-openapi-spec.yaml
        description: |
          Example OpenAPI spec in the https://git.example.com/some-repo repo
```
