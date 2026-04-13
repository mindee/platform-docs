---
description: No-Code and Low-Code integration support.
icon: square-share-nodes
---

# No-Code Integrations

## Overview

The Mindee API is well-suited to integrations in no-code and low-code platforms.

It's a relatively simple RESTful API so most tools and platforms can be integrated using HTTP nodes.

## Officially Supported Integrations

We're hard at work providing official integrations for platforms that allow it.

Currently we have support for the following platforms:

* **n8n**: [basic support for workflows](n8n-workflows.md), official support [coming soon](https://github.com/n8n-io/n8n/pull/18986)
* **Zapier**: [officially supported](zapier-zaps.md)
* **Make**: [officially supported](make.com-scenarios.md)

Don't see support for your favorite platform? [Make a feature request!](https://feedback.mindee.com/?b=682f69c9e2404756e7e68d1c)

## Generic No-Code Integration

{% hint style="info" %}
Only use this method if your no-code platform does not have an official integration.
{% endhint %}

You'll need to use HTTP nodes in your workflow that can POST and GET a specified URL.

First, POST as form-data to the [#post-v2-inferences-enqueue](../api-reference/#post-v2-inferences-enqueue "mention") route:

* The Content-Type header must be set to `multipart/form-data`
* The `Authorization` header must have only your API key as the value
* The file or URL to process, one of: `file`, `file_base64`, or `url`
* The Model ID, `model_id`

If your no-code platform doesn't support the `form-data` Content-Type, you may post as `application/json`. In this case you must use `file_base64` or `url` only.

In the response to the POST, there will be a `polling_url` attribute, save its value.

Wait 3 seconds.

Loop GET requests on the `polling_url` until the response contains a `result_url` .\
**Note**: make sure to configure the node to **not** follow redirections.

Alternatively, loop on the `polling_url` until it redirects to the result.

**Important**: in all cases, wait at least 1 second between each poll.

A GET request to the `result_url` will contain the result payload.
