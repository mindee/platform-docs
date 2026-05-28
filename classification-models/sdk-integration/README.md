---
description: Integrate a Classification model using the Mindee SDKs.
icon: code
---

# SDK Integration

Use the SDKs to send documents to a Classification model and process classification results.

This section helps you choose the right starting point and move through the full integration flow.

### Choose your path

Start with the page that matches your next step:

* [Classification Quick Start](classification-quick-start.md) ⇒ install a client library, send a file, and get your first result.
* [Classification Result](classification-result.md) ⇒ access the predicted class and optional chained extraction result.
* [Classification Model Overview](../classification.md) ⇒ understand how Classification models assign a class to a document.

### Typical SDK workflow

{% stepper %}
{% step %}
#### Create Your Model

[Create your Classification Model](../classification.md#create-a-classification-model) on the Mindee platform.

Upload some samples to the [live-test.md](../../models/live-test.md "mention") to validate the model.
{% endstep %}

{% step %}
### Install and authenticate

Install the client library for your language.

Prepare your API key and initialize the client.
{% endstep %}

{% step %}
#### Send a document

Set the Classification model's ID and send a file or URL for processing.

Start with polling unless you already use webhooks.
{% endstep %}

{% step %}
#### Process the classification result

Read the predicted class from the response.

Use the returned document type to route the document in your workflow.
{% endstep %}
{% endstepper %}

### Before you start

Have these ready:

* your API key
* your Classification Model's unique ID
* a sample document for testing
* a language choice for the SDK

### What is specific to Classification models

Classification responses describe the class predicted for the whole document.

The classifier looks at all pages in the file before assigning a document type.

Document types are returned exactly as configured on the platform.

If extraction chaining is enabled, the classification result can also include an extraction response.

### Shared SDK building blocks

{% include "../../.gitbook/includes/generic-sdk-integration.md" %}
