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

## Features

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

## Plugin configuration

The following environment variable are passed to the `kronicle-serice` container to configure the plugin


### Example configuration

{{< env-vars
"PLUGINS_GITHUB_ENABLED=true"
"# Find all repos that an access token has access to"
"PLUGINS_GITHUB_ACCESS_TOKENS_0_USERNAME=some-github-user"
"PLUGINS_GITHUB_ACCESS_TOKENS_0_VALUE=ghp_1234567890"
"# Find all repos under a GitHub organisation"
"PLUGINS_GITHUB_ORGANIZATIONS_0_ACCOUNT_NAME=some-github-org-name"
"PLUGINS_GITHUB_ORGANIZATIONS_0_ACCESS_TOKEN_USERNAME=some-github-user"
"PLUGINS_GITHUB_ORGANIZATIONS_0_ACCESS_TOKEN_VALUE=ghp_1234567890"
"# Find all repos under a GitHub user"
"PLUGINS_GITHUB_USERS_0_ACCOUNT_NAME=some-github-user"
"PLUGINS_GITHUB_USERS_0_ACCESS_TOKEN_USERNAME=some-github-user"
"PLUGINS_GITHUB_USERS_0_ACCESS_TOKEN_VALUE=ghp_1234567890" >}}
{{< /env-vars >}}


### Mandatory environment variables

{{< env-vars "PLUGINS_GITLAB_ENABLED=true" >}}
Set to "true" to enable the plugin
{{< /env-vars >}}


### Optional environment variables

{{< env-vars "PLUGINS_GITLAB_HOSTS_{index}_BASE_URL=" >}}
The base URL of a GitLab instance.  Can be use used with https://gitlab.com and also a self-hosted GitLab instance
{{< /env-vars >}}

{{< env-vars "PLUGINS_GITLAB_HOSTS_{index}_ACCESS_TOKENS_{index}_VALUE=some-gitlab-access-token" >}}
The access token.  Care should be taken with what permissions are granted on GITLAB for the access token.  If the
access token is granted access to any private repos, regardless of what organization or user owns those private repos,
then Kronicle Service will have access to those private repos too
{{< /env-vars >}}

{{< env-vars "PLUGINS_GITLAB_HOSTS_{index}_GROUPS_{index}_PATH=some-gitlab-group-path" >}}
Path of a GitLab group.  The plugin will load all GitLab repos under this group that the specified access token has
been granted access to
{{< /env-vars >}}

{{< env-vars "PLUGINS_GITLAB_HOSTS_{index}_GROUPS_{index}_ACCESS_TOKEN_VALUE=some-gitlab-access-token" >}}
The access token
{{< /env-vars >}}

{{< env-vars "PLUGINS_GITLAB_HOSTS_{index}_USERS_{index}_USERNAME=some-gitlab-user" >}}
Name of a GitLab group.  The plugin will load all of this user's personal GitLab repos that the specified access token
has been granted access to
{{< /env-vars >}}

{{< env-vars "PLUGINS_GITLAB_HOSTS_{index}_USERS_{index}_ACCESS_TOKEN_VALUE=some-gitlab-access-token" >}}
The access token
{{< /env-vars >}}

{{< env-vars "REPO_FINDERS_IGNORED_REPOS_{index}_URL=https://github.com/kronicle-tech/kronicle-metadata-repo-template.git" >}}
Configures Git repos that Kronicle Service should ignore.  Multiple entries can be configured.  `{index}` should start from zero and be incremented by 1 for each Git repo URL.
{{< /env-vars >}}


### Excluding certain Git repos

This environment variable can be used to prevent Kronicle for loading certain Git repos, regardless of which Kronicle
plugin has found these Git repos:

{{< env-vars
"PLUGINS_GITHUB_ACCESS_TOKENS_0_USERNAME=some-github-user"
"PLUGINS_GITHUB_ACCESS_TOKENS_0_VALUE=ghp_1234567890"
"REPO_FINDERS_IGNORED_REPOS_0_URL=https://github.com/some-github-user/example-repo-1"
"REPO_FINDERS_IGNORED_REPOS_1_URL=https://github.com/some-github-user/example-repo-2" >}}
{{< /env-vars >}}
