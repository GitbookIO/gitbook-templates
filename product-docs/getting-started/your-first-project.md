---
description: >-
  A guided walkthrough that takes you from an empty workspace to a configured,
  deployed project.
icon: compass
---

# Your first project

This walkthrough goes deeper than the [Quickstart](/broken/pages/d8dde992c3b506ec2b54b125e6aef8f498f18ed3). By the end, you'll have a real project with environment variables, a custom build, and a preview deployment workflow.

{% hint style="info" %}
We'll use a generic web project for this tutorial. The same pattern works for static sites, APIs, and worker services.
{% endhint %}

## 1. Plan your project structure

Before clicking anything, decide how you want to organise your work:

| You have…                  | Use…                                       |
| -------------------------- | ------------------------------------------ |
| One app, one team          | A single project in your default workspace |
| Several related apps       | A workspace with one project per app       |
| Multiple unrelated clients | A separate workspace per client            |

Most people start with the middle option. You can always restructure later.

## 2. Create the project

{% stepper %}
{% step %}
#### From the workspace dashboard

Click **New project**. You'll see three creation options.

{% tabs %}
{% tab title="From a repo" %}
Connect your version control provider and select a repository. The platform detects your framework and pre-fills sensible defaults.
{% endtab %}

{% tab title="From a template" %}
Pick a starting template — blog, dashboard, API, etc. — and the platform creates a new repository for you.
{% endtab %}

{% tab title="Empty project" %}
Skip both and create an empty project. Useful when you want to wire up a custom CLI workflow.
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
#### Name and configure

Give your project a name and choose its visibility.

* **Public** — anyone with the URL can view the deployed site
* **Private** — only invited members can access it
* **Password-protected** — anyone with the URL and password can view it
{% endstep %}

{% step %}
#### Set environment variables

If your project needs API keys, database URLs, or other secrets, add them under **Project settings → Environment**.

```bash
DATABASE_URL=postgres://...
API_TOKEN=...
```

{% hint style="warning" %}
Never commit secrets to your repository. Use environment variables for anything sensitive.
{% endhint %}
{% endstep %}
{% endstepper %}

## 3. Customise your build

The platform auto-detects most frameworks, but you can override the defaults in your project's `platform.yaml`:

```yaml
build:
  command: npm run build
  output: dist/
  node: 20
  install: npm ci

deploy:
  framework: auto
  routes:
    - source: /api/*
      destination: /api/[...path].js
```

Common overrides:

* **`build.command`** — the script that produces your output
* **`build.output`** — the folder containing your built files
* **`build.node`** — the Node.js version to use
* **`deploy.routes`** — custom routing rules

## 4. Set up preview deploys

Preview deploys give every branch and pull request its own live URL. They're enabled by default, but you can fine-tune the behaviour:

```yaml
preview:
  enabled: true
  branches:
    include: ["**"]
    exclude: ["release/*"]
  comments: true
```

When `comments: true`, the platform posts a comment on each pull request with the preview URL.

## 5. Deploy

Push to your main branch (or click **Deploy** manually). The platform will:

1. Clone your repository
2. Install dependencies
3. Run your build command
4. Upload the output
5. Promote to your live URL

{% hint style="success" %}
You'll get a notification when the build completes — by email, Slack, or whatever you configured under [automations.md](../guides/automations.md "mention").
{% endhint %}

## Sample project

If you'd like to skip ahead and see a fully configured project, download our sample:

{% embed url="https://github.com/GitbookIO/gitbook-templates" %}

## Where to go next

Now that you have a working project, you can check out:

{% content-ref url="../guides/custom-domains.md" %}
[custom-domains.md](../guides/custom-domains.md)
{% endcontent-ref %}

{% content-ref url="../guides/automations.md" %}
[automations.md](../guides/automations.md)
{% endcontent-ref %}

{% content-ref url="../core-concepts/permissions.md" %}
[permissions.md](../core-concepts/permissions.md)
{% endcontent-ref %}
