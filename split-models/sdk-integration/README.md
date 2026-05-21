---
description: Integrate a Split model using the Mindee SDKs.
icon: code
---

# SDK Integration

Use the SDKs to send multi-page files to a Split model and process split results.

This section helps you choose the right starting point and move through the full integration flow.

### Choose your path

Start with the page that matches your next step:

* [Split Quick Start](split-quick-start.md) ⇒ install a client library, send a file, and get your first result.
* [Split Result](split-result.md) ⇒ access split ranges, document types, and optional chained extraction results.
* [Split Model Overview](../split.md) ⇒ understand how Split models group pages into logical documents.

### Typical SDK workflow

{% stepper %}
{% step %}
#### Install and authenticate

Install the client library for your language.

Prepare your API key and initialize the client.
{% endstep %}

{% step %}
#### Send a file

Choose your model ID and send a file or URL for processing.

Start with polling unless you already use webhooks.
{% endstep %}

{% step %}
#### Process the split results

Read the list of detected documents from the response.

Use each split's document type and page range in your workflow.
{% endstep %}
{% endstepper %}

### Before you start

Have these ready:

* an API key
* your model ID
* a multi-page sample file for testing
* a language choice for the SDK

### What is specific to Split models

Split responses contain a list of logical documents found in the source file.

Each split includes a document type and a 0-based page range.

Document types are returned exactly as configured on the platform.

If extraction chaining is enabled, each split can also include an extraction response.

### Shared SDK building blocks

{% include "../../.gitbook/includes/generic-sdk-integration.md" %}
