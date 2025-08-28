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

Currently we have official support for the following platforms:

* **n8n**: [basic support for workflows](n8n-workflows.md)
* **Zapier**: planned, coming soon
* **Make**: planned, coming soon

Don't see support for your favorite platform? [Make a feature request!](https://feedback.mindee.com/?b=682f69c9e2404756e7e68d1c)

## Generic No-Code Integration

You'll need to use HTTP nodes in your workflow that can POST and GET a specified URL.

First, POST a file to the [#post-v2-inferences-enqueue](../api-reference.md#post-v2-inferences-enqueue "mention") route. You'll need you API key and Model ID.

In this POST response, there will be a `polling_url` attribute, save its value.

Wait 3 seconds.

Loop GET requests on the `polling_url` until the response contains a `result_url` .\
**Note**: make sure to configure the node to **not** follow redirections.

Alternatively, loop on the `polling_url` until it redirects to the result.

**Important**: in all cases, wait at least 1 second between each poll.

A GET request to the `result_url` will contain the result payload.
