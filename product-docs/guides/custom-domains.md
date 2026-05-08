---
description: >-
  Replace your auto-generated subdomain with your own domain, with automatic
  SSL.
icon: globe
---

# Custom domains

By default, every project is published at a subdomain of the platform. You can replace this with your own domain on any paid plan.

{% hint style="success" %}
SSL certificates are issued automatically once your domain is verified — there's nothing to install or renew yourself.
{% endhint %}

## Before you start

You'll need:

* A paid plan (Pro or above)
* Access to your domain registrar's DNS settings
* A successful deploy of the project you want to attach

## Steps

{% stepper %}
{% step %}
#### Add your domain in the dashboard

Go to **Project settings → Domains** and click **Add domain**. Enter the domain or subdomain you want to use:

```
docs.yourcompany.com
```

The dashboard will show you the DNS record values you need.
{% endstep %}

{% step %}
#### Configure your DNS

Add a CNAME record pointing your subdomain at the platform:

```
Type:  CNAME
Name:  docs
Value: sites.example-platform.com
TTL:   3600
```

For an apex domain (e.g. `yourcompany.com` without a subdomain), you'll need an ALIAS or ANAME record instead — not all DNS providers support these. Check your provider's docs.

{% hint style="info" %}
DNS changes can take up to 48 hours to propagate, but in practice most see them resolve within a few minutes.
{% endhint %}
{% endstep %}

{% step %}
#### Verify and activate

Return to **Project settings → Domains** and click **Verify**. Once verified, the platform will issue an SSL certificate automatically — usually within a couple of minutes.

When verification completes, your domain is live.
{% endstep %}
{% endstepper %}

## Multiple domains per project

You can attach multiple domains to a single project — useful for redirecting old URLs or supporting multiple regions:

```yaml
domains:
  primary: docs.yourcompany.com
  redirects:
    - from: help.yourcompany.com
      to: docs.yourcompany.com
      status: 301
```

## Troubleshooting

<details>

<summary>Verification keeps failing</summary>

Make sure there are no conflicting DNS records for the same subdomain. An existing A record will block the CNAME.

Also check that the value of your CNAME exactly matches the one shown in the dashboard — typos in domain names are very common.

</details>

<details>

<summary>SSL certificate not provisioning</summary>

SSL is issued after DNS verification succeeds. If it hasn't appeared after 30 minutes:

1. Confirm your domain still verifies in the dashboard
2. Check that your DNS provider isn't using CAA records that block our certificate authority
3. Click **Re-verify** to trigger a fresh attempt

</details>

<details>

<summary>Browser shows "Your connection is not private"</summary>

This usually means the certificate hasn't been provisioned yet, or your browser cached an old certificate. Wait a few minutes, then try in an incognito window.

</details>

<details>

<summary>The domain works but redirects break</summary>

Redirect chains often get cached aggressively. Test in an incognito window or with `curl -I` to see what's actually being served, ignoring local cache.

```bash
curl -I https://docs.yourcompany.com
```

</details>

## Removing a domain

To remove a domain, go to **Project settings → Domains**, click the menu next to the domain, and select **Remove**.

{% hint style="warning" %}
Removing a domain stops serving traffic immediately. If you've shared this URL externally, set up a redirect first to avoid breaking inbound links.
{% endhint %}
