---
description: Roles, permissions, and how access flows from workspace to project.
icon: lock
---

# Permissions

Every member of a workspace has a role. The role determines what actions they can perform across the workspace and its projects.

## Roles overview

There are five roles, ordered from least to most privileged:

| Role         | Best for                                                        |
| ------------ | --------------------------------------------------------------- |
| **Guest**    | External stakeholders who only need to see published deploys    |
| **Viewer**   | Internal users who need read-only access to drafts and settings |
| **Editor**   | Builders who actively work on projects                          |
| **Reviewer** | People who comment and approve, but don't push changes          |
| **Admin**    | Workspace owners and team leads                                 |

{% hint style="info" %}
Guests don't count towards your member limit, making them ideal for read-only stakeholders.
{% endhint %}

## Permission matrix

The full breakdown of what each role can do:

| Action                       | Guest | Viewer | Reviewer | Editor | Admin |
| ---------------------------- | :---: | :----: | :------: | :----: | :---: |
| View published deploys       |   ✓   |    ✓   |     ✓    |    ✓   |   ✓   |
| View drafts                  |   —   |    ✓   |     ✓    |    ✓   |   ✓   |
| Comment on deploys           |   —   |    —   |     ✓    |    ✓   |   ✓   |
| Trigger builds               |   —   |    —   |     —    |    ✓   |   ✓   |
| Edit project settings        |   —   |    —   |     —    |    ✓   |   ✓   |
| Manage environment variables |   —   |    —   |     —    |    ✓   |   ✓   |
| Invite members               |   —   |    —   |     —    |    —   |   ✓   |
| Change roles                 |   —   |    —   |     —    |    —   |   ✓   |
| Manage billing               |   —   |    —   |     —    |    —   |   ✓   |
| Delete projects              |   —   |    —   |     —    |    —   |   ✓   |

## How permissions flow

Roles are assigned at the **workspace level** and apply to every project in that workspace. There's no per-project override.

If you need finer-grained access — for example, contractors who should only see one project — create a separate workspace for that work and invite them there.

{% hint style="warning" %}
Per-project roles are a frequently requested feature and are on our [roadmap](https://example.com/roadmap). For now, the workspace boundary is the boundary of access.
{% endhint %}

## Changing someone's role

Workspace admins can change any member's role at any time:

1. Go to **Workspace settings → Members**
2. Find the member and click the role dropdown next to their name
3. Select the new role and confirm

The change takes effect immediately — the member doesn't need to re-authenticate.

## Removing a member

Removing a member revokes their access immediately. Any content they created stays in the workspace.

{% hint style="danger" %}
If you're using SSO, removing a member from your identity provider does **not** automatically remove them from the workspace unless SCIM provisioning is enabled.
{% endhint %}
