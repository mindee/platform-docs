---
description: Integrate a Crop model using the Mindee SDKs.
icon: code
---

# SDK Integration

Use the SDKs to send files to a Crop model and process crop results.

This section helps you choose the right starting point and move through the full integration flow.

### Choose your path

Start with the page that matches your next step:

* [Crop Quick Start](crop-quick-start.md) ⇒ install a client library, send a file, and get your first result.
* [Crop Result](crop-result.md) ⇒ access detected items, object types, and optional chained extraction results.
* [Crop Model Overview](../crop.md) ⇒ understand how Crop models detect documents or objects on a page.

### Typical SDK workflow

{% stepper %}
{% step %}
#### Install and authenticate

Install the client library for your language.

Prepare your API key and initialize the client.
{% endstep %}

{% step %}
#### Send a file

Set the Crop model's ID and send a file or URL for processing.

Start with polling unless you already use webhooks.
{% endstep %}

{% step %}
#### Process the crop results

Read the list of detected items from the response.

Use each item's object type, page, and polygon in your workflow.
{% endstep %}
{% endstepper %}

### Before you start

Have these ready:

* an API key
* the Crop model's unique ID
* a sample file for testing
* a language choice for the SDK

### What is specific to Crop models

Crop responses contain a list of detected items found in the source file.

Each item includes an object type and a location.

The location contains a 0-based page index and polygon coordinates.

Object types are returned exactly as configured on the platform.

If extraction chaining is enabled, each crop item can also include an extraction response.

### Shared SDK building blocks

{% include "../../.gitbook/includes/generic-sdk-integration.md" %}
