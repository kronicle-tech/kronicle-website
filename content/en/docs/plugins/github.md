---
title: "GitHub"
description: "A plugin that integrates with GitHub's APIs."
lead: "A plugin that integrates with GitHub's APIs."
date: 2022-05-11T20:00:00+00:00
lastmod: 2022-05-11T20:00:00+00:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 606
toc: true
---

## Features

The GitHub plugin is used to:

1. Auto-discover GitHub repos containing `/kronicle.yaml` metadata files
2. Clone those repos to analyze their contents

The plugin can find Git repos in three different ways:

1. Load all repos that a GitHub access token has been granted access to
2. Load all repos under a specific GitHub organization
3. Load all repos under a specific GitHub user account (personal repos)

The three approaches can be mix and matched and the plugin allows multiple access tokens, organizations and users to be
configured.


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

{{< env-vars "PLUGINS_GITHUB_ENABLED=true" >}}
Set to "true" to enable the plugin
{{< /env-vars >}}


### Optional environment variables

{{< env-vars "PLUGINS_GITHUB_ACCESS_TOKENS_{index}_USERNAME=some-github-user" >}}
This is used to configure Kronicle to automatically scan all the Git repos that the specified user account has been granted access to.
{{< /env-vars >}}

{{< env-vars "PLUGINS_GITHUB_ACCESS_TOKENS_{index}_VALUE=ghp_1234567890" >}}
This setting must be used when the PLUGINS_GITHUB_ACCESS_TOKENS_{index}_USERNAME setting is used.  Care should be taken with what permissions are granted on GitHub for the access token.  If the access token is granted access to any private repos, regardless of what organization or user owns those private repos, then Kronicle Service will have access to those private repos too.
{{< /env-vars >}}

{{< env-vars "PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCOUNT_NAME=some-github-org-name" >}}
This is used to configure Kronicle to automatically scan all the Git repos owned by a particular organization on GitHub, looking for `kronicle.yaml` files.
{{< /env-vars >}}

{{< env-vars "PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCESS_TOKEN_USERNAME=some-github-user" >}}
This is used with the PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCOUNT_NAME setting but it optional.  Without it, Kronicle Service will call the GitHub API anonymously.  The setting contains the username of a GitHub user.  Specifying this setting can be helpful as it enables Kronicle Service to authenticate with the GitHub API, which reduces the rate limiting that the API performs.
{{< /env-vars >}}

{{< env-vars "PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCESS_TOKEN_VALUE=ghp_1234567890" >}}
This setting must be used when the PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCESS_TOKEN_USERNAME setting is used.  In contains the GitHub access token (PAT) for the GitHub used specified in the PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCESS_TOKEN_USERNAME setting.  Care should be taken with what permissions are granted on GitHub for the access token.  If the access token is granted access to any of the GitHub organization's private repos, then Kronicle Service will have access to those private repos too.
{{< /env-vars >}}

{{< env-vars "PLUGINS_GITHUB_USERS_{index}_ACCOUNT_NAME=some-github-user" >}}
Similar to the PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCOUNT_NAME setting but configures Kronicle Service to retrieve repos for a GutHub user rather han a GitHub organization
{{< /env-vars >}}

{{< env-vars "PLUGINS_GITHUB_USERS_{index}_ACCESS_TOKEN_USERNAME=some-github-user" >}}
Similar to the PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCESS_TOKEN_USERNAME setting.
{{< /env-vars >}}

{{< env-vars "PLUGINS_GITHUB_USERS_{index}_ACCESS_TOKEN_VALUE=ghp_1234567890" >}}
Similar to the PLUGINS_GITHUB_ORGANIZATIONS_{index}_ACCESS_TOKEN_VALUE setting.  Care should be taken with what permissions are granted on GitHub for the access token.  If the access token is granted access to any of the GitHub user's private repos, then Kronicle Service will have access to those private repos too.
{{< /env-vars >}}

{{< env-vars "REPO_FINDERS_IGNORED_REPOS_{index}_URL=https://github.com/kronicle-tech/kronicle-metadata-repo-template.git" >}}
Configures Git repos that Kronicle Service should ignore.  Multiple entries can be configured.  `{index}` should start from zero and be incremented by 1 for each Git repo URL.
{{< /env-vars >}}


### Granting access to two GitHub organizations

Here is an example of the environment variables needed to configure Kronicle to load all the Git repos for two
independent GitHub organizations:

{{< env-vars
"PLUGINS_GITHUB_ORGANIZATIONS_0_ACCOUNT_NAME=some-github-organization"
"PLUGINS_GITHUB_ORGANIZATIONS_0_ACCESS_TOKEN_USERNAME=some-github-user"
"PLUGINS_GITHUB_ORGANIZATIONS_0_ACCESS_TOKEN_VALUE=gpp_example123"
""
"PLUGINS_GITHUB_ORGANIZATIONS_1_ACCOUNT_NAME=another-github-organization"
"PLUGINS_GITHUB_ORGANIZATIONS_1_ACCESS_TOKEN_USERNAME=another-github-user"
"PLUGINS_GITHUB_ORGANIZATIONS_1_ACCESS_TOKEN_VALUE=gpp_example456" >}}
{{< /env-vars >}}


### Granting access to a GitHub organization's repos via a GitHub user account

Here is an example of configuring Kronicle to load all Git repos via a `machine` GitHub account.  This approach will
grant Kronicle access to all the repos that the user account has been _explicitly_ granted access to.  That includes
access granted directly to the user account and access granted via a GitHub team.

{{< env-vars
"PLUGINS_GITHUB_ACCESS_TOKENS_0_USERNAME=some-github-user"
"PLUGINS_GITHUB_ACCESS_TOKENS_0_VALUE=gpp_example123" >}}
{{< /env-vars >}}


### Excluding certain Git repos

This environment variable can be used to prevent Kronicle for loading certain Git repos, regardless of which Kronicle
plugin has found these Git repos:

{{< env-vars
"PLUGINS_GITHUB_ACCESS_TOKENS_0_USERNAME=some-github-user"
"PLUGINS_GITHUB_ACCESS_TOKENS_0_VALUE=gpp_example123"
"REPO_FINDERS_IGNORED_REPOS_0_URL=https://github.com/some-github-user/example-repo-1"
"REPO_FINDERS_IGNORED_REPOS_1_URL=https://github.com/some-github-user/example-repo-2" >}}
{{< /env-vars >}}
