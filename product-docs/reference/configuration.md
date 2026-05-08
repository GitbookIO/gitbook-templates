---
icon: sliders
---

# Configuration

The `platform.yaml` file at the root of your project controls how it builds and deploys. Most fields are optional — sensible defaults are chosen based on framework auto-detection.

## Build

Settings that control how your project is built.

| Setting         | Type   | Default         | Description                                       |
| --------------- | ------ | --------------- | ------------------------------------------------- |
| `build.command` | string | _auto-detected_ | The shell command that produces your build output |
| `build.output`  | string | _auto-detected_ | The folder containing the built files             |
| `build.install` | string | `npm ci`        | The command to install dependencies               |
| `build.node`    | string | `20`            | The Node.js version to use                        |
| `build.env`     | object | `{}`            | Environment variables available during build      |

Example:

```yaml
build:
  command: npm run build
  output: dist/
  node: 20
  env:
    NODE_OPTIONS: --max-old-space-size=4096
```

## Deploy

Settings that control how your project is deployed and routed.

| Setting            | Type   | Default | Description                                     |
| ------------------ | ------ | ------- | ----------------------------------------------- |
| `deploy.framework` | string | `auto`  | Framework hint (e.g. `next`, `astro`, `static`) |
| `deploy.routes`    | array  | `[]`    | Custom routing rules                            |
| `deploy.headers`   | array  | `[]`    | Custom HTTP headers per path                    |
| `deploy.redirects` | array  | `[]`    | URL redirects                                   |
| `deploy.region`    | string | `auto`  | Preferred deploy region                         |

Example:

```yaml
deploy:
  framework: next
  region: eu-west-1
  routes:
    - source: /api/*
      destination: /api/[...path].js
  headers:
    - path: /*
      headers:
        - key: X-Frame-Options
          value: DENY
```

## Preview

Settings that control preview deploys for branches and pull requests.

| Setting                    | Type    | Default  | Description                                |
| -------------------------- | ------- | -------- | ------------------------------------------ |
| `preview.enabled`          | boolean | `true`   | Whether previews are enabled at all        |
| `preview.branches.include` | array   | `["**"]` | Branch patterns to deploy                  |
| `preview.branches.exclude` | array   | `[]`     | Branch patterns to skip                    |
| `preview.comments`         | boolean | `true`   | Comment on pull requests with preview URLs |
| `preview.password`         | string  | _none_   | Password-protect preview URLs              |

## Notifications

Where to send build and deploy events.

| Setting                | Type   | Default             | Description                        |
| ---------------------- | ------ | ------------------- | ---------------------------------- |
| `notifications.email`  | array  | `[]`                | Email addresses to notify          |
| `notifications.slack`  | object | _none_              | Slack webhook configuration        |
| `notifications.events` | array  | `["deploy.failed"]` | Which events trigger notifications |

Example:

```yaml
notifications:
  events: [deploy.succeeded, deploy.failed]
  slack:
    webhook: https://hooks.example.com/...
    channel: "#deploys"
```

## Plan limits

Limits that apply at the workspace level, by plan:

| Limit                      | Free   | Pro   | Business  | Enterprise |
| -------------------------- | ------ | ----- | --------- | ---------- |
| Active projects            | 3      | 25    | Unlimited | Unlimited  |
| Concurrent builds          | 1      | 3     | 10        | Custom     |
| Build minutes / month      | 500    | 6,000 | 24,000    | Custom     |
| Bandwidth / month          | 100 GB | 1 TB  | 5 TB      | Custom     |
| Team members               | 1      | 10    | 50        | Unlimited  |
| Custom domains per project | 1      | 10    | Unlimited | Unlimited  |

{% hint style="info" %}
Need higher limits than Business offers? [Contact sales](https://gitbook.com/contact) to discuss Enterprise pricing.
{% endhint %}
