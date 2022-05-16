---
title : "Tutorial"
description: "This tutorial will take you through the steps for running Kronicle locally and getting its features working."
lead: "This tutorial will take you through the steps for running Kronicle locally and getting its features working."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "tutorial"
weight: 1
url: "/tutorial/"
---

## Prerequisites

The following software is needed to follow this tutorial:

1. Git
2. [Docker Desktop](https://www.docker.com/products/docker-desktop/)


## Running Kronicle

Here are the steps to run Kronicle locally:

```shell
$ git clone https://github.com/kronicle-tech/kronicle-docker-compose.git
$ cd kronicle-docker-compose
# Start the `docker-app` and `docker-service` Docker containers.
$ docker-compose up -d
```

It will take a few seconds before the two containers have fully started.  Once they have started, open the following
URL in your browser:

http://localhost:3000/


## Adding a `kronicle.yaml` metadata file to a GitRepo

Open https://github.com/kronicle-tech/kronicle-metadata-repo-template in a browser.  Click the `Use this template`
button in the top right to create a new repo based on the template.


## Point `kronicle-service` at the new repo

Edit the `/kronicle.yaml` file in your clone of the `kronicle-docker-compose` repo.  Replace this line:

```yaml
      PLUGINS_GITHUB_ORGANIZATIONS_0_ACCOUNT_NAME: kronicle-tech
```

with this line:

```yaml
      PLUGINS_GITHUB_ORGANIZATIONS_0_ACCOUNT_NAME: your-github-user-name
```

Restart docker compose:

```yaml
$ docker-compose down
$ docker-compose up -d
```

Once the Kronicle containers have started, open http://localhost:3000/all-components in a browser.  The webpage should
show the `example-component` and `example-detailed-component` components from the `kronicle.yaml` file in your new
repo.

If you make changes to that `kronicle.yaml` file and commit them to the `main` branch, those changes should
show up in the Kronicle UI within the next 15 minutes.


## Next steps

See the [Plugins page](/docs/plugins/) for a list of the plugins that Kronicle supports.  Plugins are enabled and
configured by passing environment variables to the `kronicle-service` container.  See the `docker-compose.yaml` file
in your local clone of the `kronicle-docker-compose` repo to see what environment variables are already passed to the
`kronicle-service` container.

Try finding a Kronicle plugin that looks interesting and try enabling and configuring it.
