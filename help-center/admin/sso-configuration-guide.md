---
description: >-
  Configure single sign-on so your team can log in with your existing identity
  provider.
icon: key
---

# SSO configuration guide

Single sign-on (SSO) lets your team authenticate using your existing identity provider (IdP) rather than a separate password. SSO is available on Business and Enterprise plans.

### Supported providers

We support any SAML 2.0-compatible identity provider, including most enterprise IdPs. Check your provider's documentation for instructions on creating a SAML application.

### Setting up SSO

{% stepper %}
{% step %}
#### Create an application in your IdP

In your identity provider's admin console, create a new SAML application. You'll need the following values from our settings page:

* **ACS URL** (also called the Reply URL or Callback URL)
* **Entity ID** (also called the Audience URI)

These are available under **Settings → Security → SSO**.
{% endstep %}

{% step %}
#### Copy your IdP metadata

From your identity provider, copy the **Metadata URL** or download the **Metadata XML** file.
{% endstep %}

{% step %}
#### Configure SSO in your workspace

Go to **Settings → Security → SSO**, paste your Metadata URL (or upload the XML file), and click **Save**.
{% endstep %}

{% step %}
#### Test the connection

Click **Test SSO** to verify the configuration before enabling it for your whole team. A test login window will open — complete the login and you'll see a success or error message.
{% endstep %}

{% step %}
#### Enable SSO

Once the test passes, toggle **Enforce SSO** to on. All workspace members will now be required to log in via your IdP.
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Make sure you can log in via SSO before enabling enforcement. If SSO breaks after enforcement is on, contact support — we can disable it for you from the backend.
{% endhint %}

### Provisioning and deprovisioning

With SCIM provisioning enabled, users are automatically added to or removed from your workspace when you add or remove them in your IdP. SCIM setup is available under **Settings → Security → SCIM**.
