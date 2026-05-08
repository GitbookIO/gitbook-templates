---
description: Go from sign-up to your first deploy in under five minutes.
icon: bolt
---

# Quickstart

This quickstart gets you to your first deploy as fast as possible. We'll skip most of the configuration — you can refine things later once you have something running.

{% hint style="success" %}
**Estimated time: 5 minutes.** All you need is an account and a project to deploy.
{% endhint %}

## Steps

{% stepper %}
{% step %}
#### Create your workspace

Sign in and create a new workspace. The workspace name appears in URLs and email notifications, so pick something recognisable.

```
yourcompany
```
{% endstep %}

{% step %}
#### Connect a source

Link a repository from your version control provider, or upload a project directly.

{% tabs %}
{% tab title="Repository" %}
Click **Connect repository**, authenticate with your provider, and select the repository to import. The platform will detect your framework automatically.
{% endtab %}

{% tab title="Upload" %}
Drag and drop a project folder, or use the CLI:

```bash
platform deploy ./my-project
```
{% endtab %}

{% tab title="Template" %}
Browse the template gallery and click **Use template**. A new project will be created from the template in your workspace.
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
#### Configure your build

Most projects work with the auto-detected settings. If yours doesn't, override them in **Project settings → Build**.

```yaml
build:
  command: npm run build
  output: dist/
  node: 20
```
{% endstep %}

{% step %}
#### Deploy

Hit **Deploy**. Your project will build and go live at a generated subdomain. You can promote it to production or add a custom domain at any time.

{% hint style="info" %}
First builds typically take 1–3 minutes. Subsequent builds are faster because dependencies are cached.
{% endhint %}
{% endstep %}
{% endstepper %}

## What's next?

You've shipped something — now make it yours.

{% content-ref url="../guides/custom-domains.md" %}
[custom-domains.md](../guides/custom-domains.md)
{% endcontent-ref %}

{% content-ref url="../core-concepts/permissions.md" %}
[permissions.md](../core-concepts/permissions.md)
{% endcontent-ref %}

{% content-ref url="../guides/automations.md" %}
[automations.md](../guides/automations.md)
{% endcontent-ref %}
