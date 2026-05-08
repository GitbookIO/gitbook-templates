---
description: Manage API keys and monitor usage across your workspace.
icon: rectangle-terminal
---

# Managing API keys

API keys allow external tools and automations to interact with your workspace programmatically. Workspace admins can create, view, and revoke keys at any time.

### Creating an API key

Go to **Settings → API → Keys** and click **New API key**. Give the key a descriptive name (e.g. "CI/CD integration" or "Internal dashboard") so you can identify it later.

{% hint style="warning" %}
Copy your key immediately after creation — it won't be shown again. If you lose it, you'll need to revoke and recreate it.
{% endhint %}

### Key permissions

When creating a key, you can scope its permissions:

| Permission | What it allows                           |
| ---------- | ---------------------------------------- |
| **Read**   | Fetch content, settings, and member data |
| **Write**  | Create and update content                |
| **Admin**  | Manage settings, members, and billing    |

Use the minimum permissions necessary for each integration.

### Rotating a key

To rotate a key, create a new one, update your integration to use it, then revoke the old key. There's no automated rotation — this is a manual process.

### Revoking a key

Go to **Settings → API → Keys**, find the key, and click **Revoke**. Revocation is immediate — any requests using that key will fail instantly.

### Monitoring usage

Under **Settings → API → Usage**, you can see request counts per key over the past 30 days. This is useful for spotting unexpected usage or identifying which integrations are most active.
