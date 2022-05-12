---
title: "OpenAPI"
description: "A plugin fetches OpenAPI specs and uses them to render OpenAPI based API documentation."
lead: "A plugin fetches OpenAPI specs and uses them to render OpenAPI based API documentation."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 340
toc: true
---

Finds JSON and YAML format OpenAPI spec files in cloned Git repos and loads those OpenAPI specs into Kronicle.  Can
also download OpenAPI specs from URLs configured in `kronicle.yaml` files.

Any found/download OpenAPI specs are loaded into Kronicle and can be viewed via Kronicle's web UI.
