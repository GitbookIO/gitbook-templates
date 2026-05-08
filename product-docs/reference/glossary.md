---
description: Definitions of terms you'll encounter in the docs and dashboard.
icon: bookmark
---

# Glossary

Plain-language definitions of terms used across the platform. Click any entry to expand it.

***

## A — F

<details>

<summary><strong>API key</strong></summary>

A secret token that authenticates requests to the platform's API. Keys are scoped to a workspace and inherit the permissions of whoever created them. See [permissions.md](../core-concepts/permissions.md "mention").

</details>

<details>

<summary><strong>Automation</strong></summary>

A piece of code that runs in response to a trigger — for example, a deploy completing or a comment being posted. See [automations.md](../guides/automations.md "mention").

</details>

<details>

<summary><strong>Build</strong></summary>

The process of turning your source code into deployable output. Each build produces an artefact, which is then promoted to a deploy.

</details>

<details>

<summary><strong>Custom domain</strong></summary>

Your own domain (like `docs.yourcompany.com`) attached to a project, in place of the auto-generated subdomain. See [custom-domains.md](../guides/custom-domains.md "mention").

</details>

<details>

<summary><strong>Deploy</strong></summary>

A live version of your project, served from a URL. Each successful build can be promoted to a deploy. The current production deploy is the one served at your primary URL.

</details>

<details>

<summary><strong>Environment</strong></summary>

The set of variables, secrets, and configuration that applies when your project runs. Most projects have at least two environments: production and preview.

</details>

***

## G — P

<details>

<summary><strong>Guest</strong></summary>

A workspace role that can view published deploys but nothing else. Guests don't count towards your member limit. See [permissions.md](../core-concepts/permissions.md "mention").

</details>

<details>

<summary><strong>Member</strong></summary>

Anyone with access to a workspace. Each member has a role that determines what they can do. Different from a guest, which is a special role that doesn't count towards your member limit.

</details>

<details>

<summary><strong>Preview deploy</strong></summary>

A deploy created automatically for a branch or pull request, served at a unique URL. Used to test changes before they reach production.

</details>

<details>

<summary><strong>Project</strong></summary>

A deployable unit. Each project has its own source, builds, deploys, environment, and domains. Projects are isolated from each other within a workspace. See [workspaces-and-projects.md](../core-concepts/workspaces-and-projects.md "mention").

</details>

***

## R — Z

<details>

<summary><strong>Role</strong></summary>

A workspace-level designation that determines what a member can do. Roles are: Guest, Viewer, Reviewer, Editor, and Admin. See [permissions.md](../core-concepts/permissions.md "mention").

</details>

<details>

<summary><strong>Source</strong></summary>

The repository or upload that produces your project's builds. A project has exactly one source.

</details>

<details>

<summary><strong>SSO</strong></summary>

Single sign-on. Lets your team authenticate with your identity provider (Okta, Azure AD, etc.) instead of platform-specific credentials. Available on Business and Enterprise plans.

</details>

<details>

<summary><strong>Trigger</strong></summary>

The event that starts an automation — for example, `deploy.succeeded` or `webhook.received`. See [automations.md](../guides/automations.md "mention").

</details>

<details>

<summary><strong>Workspace</strong></summary>

The top-level container for a team's work. Owns billing, members, and projects. See [workspaces-and-projects.md](../core-concepts/workspaces-and-projects.md "mention").

</details>

***

{% hint style="info" %}
A term missing? [Suggest it in the community](https://community.example.com/) — we update this glossary regularly.
{% endhint %}
