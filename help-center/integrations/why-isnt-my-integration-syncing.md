---
description: Common reasons your integration stops syncing, and how to fix them.
icon: rotate-exclamation
---

# Why isn't my integration syncing?

If content from a connected app isn't appearing or updating as expected, work through the checks below.

### 1. Check the connection status

Go to **Settings → Integrations** and find the affected integration. If the status shows **Disconnected** or **Error**, click **Reconnect** and follow the prompts to re-authenticate.

### 2. Check your permissions

The account used to connect the integration needs sufficient permissions in the third-party app. For example, connecting a content source requires at least **read access** to the relevant data.

{% hint style="warning" %}
If the account that originally connected the integration has left your organisation or had their permissions changed, the integration will stop working. Reconnect using an account with the correct permissions.
{% endhint %}

### 3. Check for rate limits

Some third-party platforms impose rate limits on API access. If you're syncing large amounts of content or triggering many syncs in quick succession, you may be temporarily throttled. Wait a few minutes and try again.

### 4. Trigger a manual sync

On the integration settings page, click **Sync now** to force an immediate sync rather than waiting for the next scheduled run.

### 5. Review the sync log

Under **Settings → Integrations → \[Integration name] → Logs**, you'll find a record of recent sync attempts and any errors. Error messages here are usually specific enough to identify the problem.

### Still not working?

If none of the above resolves the issue, [contact support](https://example.com/support) with your sync log attached — this helps us diagnose the problem quickly.
