---
title: "GitLab"
description: "A plugin that integrates with GitLab's APIs."
lead: "A plugin that integrates with GitLab's APIs."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 270
toc: true
---

Uses the APIs of GitLab's platform APIs to find Git repos containing a `kroncile.yaml` file.  Supports
https://gitlab.com and self-hosted GitLab instances.

The plugin can search for Git Repos by:

1. GitLab group
2. GitLab user
3. GitLab access token

The plugin can find Git repos in three different ways:

1. Load all repos that a GitLab access token has been granted access to
2. Load all repos under a specific GitLab group
2. Load all repos under a specific GitLab user account (personal repos)

Environment variables supported by the plugin:

| Environment Variable                                           | Description                                                                                                                                                                                                                                                                                                | Example Value            | Required? |
|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|-----------|
| PLUGINS_GITLAB_ENABLED                                         | Set to "true" to enable the plugin                                                                                                                                                                                                                                                                         | true                     | Optional  |
| PLUGINS_GITLAB_HOSTS_{index}_BASE_URL                          | The base URL of a GitLab instance.  Can be use used with https://gitlab.com and also a self-hosted GitLab instance                                                                                                                                                                                         | some-gitlab-user         | Optional  |
| PLUGINS_GITLAB_HOSTS_{index}_ACCESS_TOKENS_{index}_VALUE       | The access token.  Care should be taken with what permissions are granted on GITLAB for the access token.  If the access token is granted access to any private repos, regardless of what organization or user owns those private repos, then Kronicle Service will have access to those private repos too | some-gitlab-access-token | Optional  |
| PLUGINS_GITLAB_HOSTS_{index}_GROUPS_{index}_PATH               | Namepath of a GitLab group.  The plugin will load all GitLab repos under this group that the specified access token has been granted access to                                                                                                                                                             | kronicle-tech            | Optional  |
| PLUGINS_GITLAB_HOSTS_{index}_GROUPS_{index}_ACCESS_TOKEN_VALUE | The access token                                                                                                                                                                                                                                                                                           | some-gitlab-access-token | Optional  |
| PLUGINS_GITLAB_HOSTS_{index}_USERS_{index}_USERNAME            | Name of a GitLab group.  The plugin will load all of this user's personal GitLab repos that the specified access token has been granted access to                                                                                                                                                          | some-gitlab-user         | Optional  |
| PLUGINS_GITLAB_HOSTS_{index}_USERS_{index}_ACCESS_TOKEN_VALUE  | The access token                                                                                                                                                                                                                                                                                           | some-gitlab-access-token | Optional  |

## Excluding certain Git repos

This environment variable can be used to prevent Kronicle for loading certain Git repos, regardless of which Kronicle
plugin has found these Git repos:

| Environment Variable                   | Description                                                                                                                                                                     | Example Value                                                        | Required? |
|----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|-----------|
| REPO_FINDERS_IGNORED_REPOS_{index}_URL | Configures Git repos that Kronicle Service should ignore.  Multiple entries can be configured.  `{index}` should start from zero and be incremented by 1 for each Git repo URL. | https://github.com/kronicle-tech/kronicle-metadata-repo-template.git | Optional  |
