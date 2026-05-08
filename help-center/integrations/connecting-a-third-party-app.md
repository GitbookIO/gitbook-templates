---
description: Connect external tools to bring your content and workflows together.
icon: plug-circle-plus
---

# Connecting a third-party app

Integrations let you pull content in from other platforms, push updates out, or automate parts of your workflow.

### Available integrations

We currently support integrations with the following categories of tools:

* **Version control** — connect your code repositories to sync and trigger workflows
* **Communication** — post notifications and updates to your team's messaging tools
* **Support** — link your helpdesk to surface relevant content for your support team
* **Analytics** — track visitor behaviour on your published sites
* **SSO providers** — authenticate your team via your existing identity provider

For a full list see **Settings → Integrations → Browse**.

### Connecting an integration

{% stepper %}
{% step %}
#### Open the integrations page

Go to **Settings → Integrations** and click **Browse all integrations**.
{% endstep %}

{% step %}
#### Choose an integration

Find the app you want to connect and click **Install**.
{% endstep %}

{% step %}
#### Authenticate

You'll be redirected to the third-party app to grant access. Make sure you're logged in to the correct account before approving.
{% endstep %}

{% step %}
#### Configure

Once connected, you'll be returned to your settings where you can configure sync frequency, which content to include, and any app-specific options.
{% endstep %}
{% endstepper %}

### Managing connected integrations

You can review, reconfigure, or disconnect integrations at any time from **Settings → Integrations → Connected**.

{% hint style="info" %}
Disconnecting an integration does not delete any content that was already synced — it just stops future syncs.
{% endhint %}

### Permissions and access

Integrations run with the permissions of the account used during authentication. We recommend using a service account or bot user where possible, to avoid disruption if an individual user leaves your organisation.
