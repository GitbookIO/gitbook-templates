---
description: >-
  React to deploys, comments, and external events with workflows that run on the
  platform.
icon: gear
tags:
  - tag: beta
    primary: true
---

# Automations

Automations let you run code in response to things that happen on the platform — a deploy completing, a comment being posted, or an external webhook firing. They're a flexible way to wire the platform into the rest of your toolchain.

{% hint style="info" %}
Automations run in a managed environment with a 30-second timeout. For long-running work, have your automation enqueue a job in your own infrastructure.
{% endhint %}

## Triggers

Automations start in response to a **trigger**. The platform supports the following:

| Trigger            | Fires when…                                   |
| ------------------ | --------------------------------------------- |
| `deploy.succeeded` | A build completes and goes live               |
| `deploy.failed`    | A build fails                                 |
| `comment.created`  | Someone comments on a deploy preview          |
| `member.invited`   | A new member is invited to the workspace      |
| `domain.verified`  | A custom domain finishes verification         |
| `webhook.received` | An external service POSTs to your inbound URL |
| `schedule`         | On a cron schedule                            |

Each automation has exactly one trigger and one or more actions.

## Writing your first automation

Create a new file under `.platform/automations/` in your project:

{% tabs %}
{% tab title="JavaScript" %}
```javascript
export default {
  trigger: 'deploy.succeeded',
  async run(event, ctx) {
    await ctx.notify('slack', {
      channel: '#deploys',
      message: `${event.project} is live at ${event.url}`
    });
  }
};
```
{% endtab %}

{% tab title="TypeScript" %}
```typescript
import type { Automation, DeployEvent } from '@platform/automations';

export default {
  trigger: 'deploy.succeeded',
  async run(event: DeployEvent, ctx) {
    await ctx.notify('slack', {
      channel: '#deploys',
      message: `${event.project} is live at ${event.url}`
    });
  }
} satisfies Automation;
```
{% endtab %}

{% tab title="Python" %}
```python
from platform_automations import automation, slack

@automation(trigger='deploy.succeeded')
async def notify_deploy(event, ctx):
    await slack.post(
        channel='#deploys',
        message=f"{event.project} is live at {event.url}"
    )
```
{% endtab %}
{% endtabs %}

The file is detected on your next deploy and registered automatically.

## A more useful example

Here's an automation that posts a summary to a chat channel whenever a pull request preview is ready:

```javascript
export default {
  trigger: 'deploy.succeeded',
  filter: (event) => event.environment === 'preview',
  async run(event, ctx) {
    const summary = await ctx.ai.summarise({
      diff: event.diff,
      maxLength: 200
    });

    await ctx.notify('slack', {
      channel: '#previews',
      message: `Preview ready: ${event.url}\n\n${summary}`
    });
  }
};
```

This shows three patterns worth knowing:

* **`filter`** — narrow the events your automation responds to
* **`ctx.ai`** — a built-in helper for AI summarisation
* **`ctx.notify`** — send to any configured notification channel

## Local testing

Test your automations locally before deploying:

{% tabs %}
{% tab title="CLI" %}
```bash
platform automations test deploy.succeeded \
  --fixture fixtures/deploy.json
```
{% endtab %}

{% tab title="Dashboard" %}
Open your automation in the dashboard and click **Test run**. You can paste in any payload or pick a saved fixture.
{% endtab %}
{% endtabs %}

## Scheduling

Use the `schedule` trigger with a cron expression for time-based automations:

```javascript
export default {
  trigger: 'schedule',
  schedule: '0 9 * * 1', // every Monday at 09:00 UTC
  async run(event, ctx) {
    const stats = await ctx.api.deploys.weekly();
    await ctx.notify('email', {
      to: 'team@example.com',
      subject: 'Weekly deploy report',
      body: stats.summary
    });
  }
};
```

{% hint style="warning" %}
Schedule times are always in UTC. Adjust your cron expression accordingly if your team works in a different timezone.
{% endhint %}

## What's next?

{% columns %}
{% column %}
**Common patterns**

* Slack notifications on deploy
* Posting summaries to issue trackers
* Daily/weekly digests
{% endcolumn %}

{% column %}
**Advanced**

* Chaining automations
* Calling external APIs
* Storing state across runs
{% endcolumn %}
{% endcolumns %}
