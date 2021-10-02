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

* Each component in your stack - software or infrastructure - has a `Kronicle.yaml` file added to the component’s own Git repo. This keeps the metadata close to the code, meaning it’s easy for engineers to both keep it up-to-date and to read it. Kronicle automatically discovers the `kronicle.yaml` files in all your repos and reloads the data in them every few minutes.  See https://github.com/kronicle-tech/kronicle/blob/main/kronicle.yaml for an example file. 
* Kronicle uses software called `Scanners` that look at the data in your `kronicle.yaml` files and then gather extra data from external sources like your Git repos, traces in [Zipkin](https://zipkin.io), code coverage in SonarQube etc.
* Using the data loaded from `kronicle.yaml` files and data found by `Scanners`, Kronicle automatically creates you a website that show things like all components, components per area, components per team, architectural diagrams, response times per component etc.
* `kronicle.yaml` files also contain metadata for teams, areas of your organisation, component types and platforms. Kronicle visualises this metadata for you, enabling your people to understand not only your tech stack but the people that work on it too.

[Live Demo](https://demo.kronicle.tech){: .btn .btn-green }

[GitHub](https://github.com/kronicle-tech/kronicle){: .btn .btn-purple }
