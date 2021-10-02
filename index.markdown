---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

# Kronicle

Kronicle is an open source tool and dashboard for development teams and tech organisations to document and visualise 
the components in their tech stack and teams in their organisation.  Kronicle automatically gathers data from the
following systems to supplement the info added to Kronicle manually: 

* Git repos
* Zipkin
* SonarQube

Kronicle has the following features:

* Each software or infrastructure component has a `Kronicle.yaml` file added to the component’s own Git repo. This keeps the metadata close to the code, meaning it’s easy for engineers to both keep it up-to-date and to read it. Kronicle automatically discovers the `kronicle.yaml` files in all your repos and reloads the data in them every few minutes
* Kronicle uses software called `Scanners` to use the data from the `kronicle.yaml` files to gather extra data from external sources like the code in your Git repos, traces in Zipkin https://zipkin.io, code coverage in SonarQube etc.
* The `kronicle.yaml` not only contain metadata for components, they also hold metadata for teams, organisational areas (e.g. product & engineering verticals), component types and platforms. This provides Kronicle with a rich set of data that it can process and visualise
* The combined data loaded from `kronicle.yaml` files and data found by `Scanners` is then presented in automated dashboards which show things like all components, components per area, components per team, architectural diagrams, response times per component etc.

[Live Demo](https://demo.kronicle.tech){: .btn .btn-green }

[GitHub](https://github.com/kronicle-tech/kronicle){: .btn .btn-purple }
