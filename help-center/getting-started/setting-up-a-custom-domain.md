---
description: Point your own domain or subdomain at your published site.
icon: globe
---

# Setting up a custom domain

By default your site is published at a subdomain of our platform. You can replace this with your own domain (e.g. `docs.yourcompany.com`) on any paid plan.

### Prerequisites

* A paid plan (Pro or above)
* Access to your domain's DNS settings
* A published site

### Steps

{% stepper %}
{% step %}
### Add your domain in settings

Go to **Settings → Publishing → Custom domain** and enter the domain or subdomain you want to use (e.g. `docs.yourcompany.com`). Click **Save**.
{% endstep %}

{% step %}
### Create a CNAME record

In your DNS provider, create a CNAME record pointing your subdomain to the address shown in your settings. Changes can take up to 48 hours to propagate, though usually it's much faster.

```
Type:  CNAME
Name:  docs
Value: sites.example-platform.com
```
{% endstep %}

{% step %}
### Verify and activate

Return to **Settings → Publishing → Custom domain** and click **Verify**. Once verified, SSL is provisioned automatically — this usually takes a few minutes.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Using an apex domain (e.g. `yourcompany.com` without a subdomain)? You'll need to set an ALIAS or ANAME record instead of a CNAME. Not all DNS providers support this — check your provider's documentation.
{% endhint %}

### Troubleshooting

**Verification keeps failing** Make sure there are no conflicting DNS records for the same subdomain. An existing A record will block the CNAME.

**SSL certificate not provisioning** SSL is issued automatically after DNS verification. If it hasn't appeared after 30 minutes, try clicking **Verify** again.

**Site loads but shows an SSL warning** This usually means a cached or old certificate. Try clearing your browser cache, or wait a few more minutes for propagation to complete.
