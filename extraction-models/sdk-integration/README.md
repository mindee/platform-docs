---
description: Integrate an Extraction model using the Mindee SDKs.
icon: code
---

# SDK Integration

Use the SDKs to send documents to an Extraction model and process dynamic results.

This section helps you choose the right starting point and move through the full integration flow.

### Choose your path

Start with the page that matches your next step:

* [Extraction Quick Start](quick-start.md) ⇒ install a client library, send a file, and get your first result.
* [Extraction Configuration](extraction-configuration.md) ⇒ set model-specific parameters and optional features.
* [Extraction Result Fields](extraction-result.md) ⇒ access dynamic fields and metadata in the SDK response.

### Typical SDK workflow

{% stepper %}
{% step %}
#### Create Your Model

Create your Extraction Model on the Mindee platform.

Upload some samples to the [live-test.md](../../models/live-test.md "mention") to validate the model.
{% endstep %}

{% step %}
#### Install and authenticate

Install the client library for your language.

Prepare your API key and initialize the client.
{% endstep %}

{% step %}
#### Send a document

Choose your model ID and send a file or URL for processing.

Start with polling unless you already use webhooks.
{% endstep %}

{% step %}
#### Process the results

Read extracted values from the response fields.

Handle field types based on your Data Schema.
{% endstep %}
{% endstepper %}

### Before you start

Have these ready:

* an API key
* your Extraction Model's unique ID
* a sample document for testing
* a language choice for the SDK

### What is specific to Extraction models

Extraction responses are dynamic.

Field names come from your model's Data Schema. Field types can be simple values, objects, or lists.

Optional metadata such as confidence scores and locations depends on which features are enabled for the request.

For better results, make sure your schema design is solid before tuning request-time options.

### Shared SDK building blocks

{% include "../../.gitbook/includes/generic-sdk-integration.md" %}
