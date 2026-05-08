---
description: Welcome to your team’s developer platform
icon: house
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: false
  outline:
    visible: false
  pagination:
    visible: false
  metadata:
    visible: false
  tags:
    visible: true
---

# Developer Platform

<button type="button" class="button primary" data-action="ask" data-icon="gitbook-assistant">Ask a question...</button>

<button type="button" class="button secondary" data-action="ask" data-query="How do I get started?" data-icon="rocket-launch">Get started</button><button type="button" class="button secondary" data-action="ask" data-query="How do I authenticate with the developer platform?" data-icon="key">Authenticate</button><button type="button" class="button secondary" data-action="ask" data-query="How do I integrate with my stack?" data-icon="code">Integrate</button><button type="button" class="button secondary" data-action="ask" data-query="How do I contribute?" data-icon="code-pull-request">Contribute</button>

&#x20;

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><h4><i class="fa-leaf" style="color:$primary;">:leaf:</i></h4></td><td><strong>No code</strong></td><td>Get started with the developer platform in 5 minutes.</td><td><a href="https://template.gitbook.com/space-product-docs">https://template.gitbook.com/space-product-docs</a></td><td><a href=".gitbook/assets/no-code.jpg">no-code.jpg</a></td></tr><tr><td><h4><i class="fa-server" style="color:$primary;">:server:</i></h4></td><td><strong>Hosted</strong></td><td>Learn more about hosting the developer platform.</td><td><a href="https://template.gitbook.com/space-product-docs">https://template.gitbook.com/space-product-docs</a></td><td><a href=".gitbook/assets/hosted.jpg">hosted.jpg</a></td></tr><tr><td><h4><i class="fa-terminal" style="color:$primary;">:terminal:</i></h4></td><td><strong>API reference</strong></td><td>Browse, test, and implement APIs.</td><td><a href="https://template.gitbook.com/space-api-reference">https://template.gitbook.com/space-api-reference</a></td><td><a href=".gitbook/assets/api-reference.jpg">api-reference.jpg</a></td></tr></tbody></table>

&#x20;

&#x20;

{% columns %}
{% column width="50%" %}
## Get started in minutes

Make your first API call in under 5 minutes.

This quickstart walks through the basic setup: create an account, generate an API key, and send a test request. The examples use the same request in several languages, so you can start with the one that matches your stack.

{% hint style="info" icon="sparkle" %}
**Customize your first request**

Explain what you're building and let AI tweak your quickstart.

<button type="button" class="button primary" data-action="ask" data-icon="gitbook-assistant">What are you building?</button>
{% endhint %}

{% hint style="warning" icon="life-ring" %}
**Need some help?**

Troubleshoot common issues or ask for help.

<details>

<summary>I get a 401 Unauthorized error</summary>

Check that your API key is present and valid.

Make sure you replaced `YOUR_API_KEY` in the example.

Confirm the `Authorization` header uses `Bearer YOUR_API_KEY`.

</details>

<details>

<summary>I get a 400 Bad Request error</summary>

Check your request body first.

Make sure the JSON is valid and the `message` field is included.

Also confirm you send `Content-Type: application/json`.

</details>

<details>

<summary>The request succeeds, but the result is not what I expect</summary>

Start with the sample payload before testing custom input.

Check the response `status` field to confirm whether the request was only queued.

If you change the payload shape, verify the endpoint accepts those fields.

</details>

<details>

<summary>My local example does not run</summary>

Check that your runtime and dependencies are installed.

For JavaScript, install the SDK before running the example.

For Python, make sure `requests` is available in your environment.

</details>

<button type="button" class="button primary" data-action="ask" data-icon="gitbook-assistant">Explain what's happening...</button>
{% endhint %}

With your first request done, use the guides for deeper setup and the API reference for endpoints and parameters.

<a href="https://template.gitbook.com/space-product-docs" class="button primary" data-icon="rocket-launch">Get started</a> <a href="https://template.gitbook.com/space-api-reference" class="button secondary" data-icon="terminal">API reference</a>

&#x20;

&#x20;
{% endcolumn %}

{% column width="50%" %}
{% stepper %}
{% step %}
#### Create your API key

Set up your account, then generate an API key for local testing and your first integration.

<a href="http://app.gitbook.com/join" class="button primary">Sign up</a><a href="http://app.gitbook.com/join" class="button secondary">Log in</a>
{% endstep %}

{% step %}
#### Make your first request

Pick a language below, replace `YOUR_API_KEY`, and run.

{% tabs %}
{% tab title="JavaScript" %}
{% code overflow="wrap" %}
```javascript
// Import the SDK
import ExampleAPI from "example-api";

// Initialize the client
const client = new ExampleAPI({ apiKey: "YOUR_API_KEY" });

// Send your first message
const response = await client.messages.send({
  message: "Hello, world!"
});
```
{% endcode %}
{% endtab %}

{% tab title="Python" %}
{% code overflow="wrap" %}
```python
import requests

response = requests.post(
    "https://api.example.com/messages",
    headers={
        "Authorization": "Bearer YOUR_API_KEY",
        "Content-Type": "application/json",
    },
    json={
        "message": "Hello, world!"
    },
)

print(response.json())
```
{% endcode %}
{% endtab %}

{% tab title="cURL" %}
{% code overflow="wrap" %}
```bash
curl -X POST https://api.example.com/messages \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "message": "Hello, world!"
  }'
```
{% endcode %}
{% endtab %}

{% tab title="Go" %}
{% code overflow="wrap" expandable="true" %}
```go
package main

import (
    "bytes"
    "fmt"
    "io"
    "net/http"
)

func main() {
    body := []byte(`{"message":"Hello, world!"}`)

    req, err := http.NewRequest("POST", "https://api.example.com/messages", bytes.NewBuffer(body))
    if err != nil {
        panic(err)
    }

    req.Header.Set("Authorization", "Bearer YOUR_API_KEY")
    req.Header.Set("Content-Type", "application/json")

    resp, err := http.DefaultClient.Do(req)
    if err != nil {
        panic(err)
    }
    defer resp.Body.Close()

    responseBody, err := io.ReadAll(resp.Body)
    if err != nil {
        panic(err)
    }

    fmt.Println(string(responseBody))
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
#### Parse the response

If the request succeeds, you should get a response like this:

{% code title="response.json" overflow="wrap" %}
```json
{
  "id": "msg_1234567890",
  "message": "Hello, world!",
  "status": "queued",
  "createdAt": "2026-01-01T12:00:00Z"
}
```
{% endcode %}
{% endstep %}
{% endstepper %}
{% endcolumn %}
{% endcolumns %}

&#x20;

&#x20;

{% columns %}
{% column width="50%" %}
<figure><img src="https://gitbookio.github.io/onboarding-template-images/placeholder.png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}

{% column width="50%" valign="middle" %}
## Learn more about the developer platform

Read guides, watch tutorials, and learn more about working with the developer platform and integrating it with your own stack.

<a href="https://template.gitbook.com/space-help-center" class="button primary" data-icon="book-open">Guides</a> <a href="https://template.gitbook.com/space-product-docs" class="button secondary" data-icon="book">Documentation</a>
{% endcolumn %}
{% endcolumns %}

&#x20;

&#x20;

<h2 align="center">Join a community of over 3,000 developers</h2>

<p align="center">Join our Discord community or create your first PR in just a few steps.</p>

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th></th><th></th><th data-hidden data-card-cover data-type="files"></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><h4><i class="fa-discord">:discord:</i></h4></td><td><strong>Discord community</strong></td><td>Join our Discord community to post questions, get help, and share resources with over 3,000 like-minded developers.</td><td><a href="https://www.gitbook.com/" class="button secondary">Join Discord</a></td><td></td><td><a href="https://www.gitbook.com/">https://www.gitbook.com/</a></td></tr><tr><td><h4><i class="fa-github">:github:</i></h4></td><td><strong>GitHub</strong></td><td>Our product is 100% open source and built by developers just like you. Head to our GitHub repository to learn how to submit your first PR.</td><td><a href="https://www.gitbook.com/" class="button secondary">Submit a PR</a></td><td></td><td><a href="https://www.gitbook.com/">https://www.gitbook.com/</a></td></tr></tbody></table>

&#x20;
