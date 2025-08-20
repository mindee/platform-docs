---
description: Quickest way to get started using the client libraries.
icon: rabbit-running
---

# Quick Start

## Installation Instructions

{% include "../../.gitbook/includes/installation-instructions.md" %}

## Send a File and Poll

Make a note of your model's ID for use in the API.

When getting started, we recommend using the polling method which will be quickest (unless you happen to already have access to a public-facing Web server).

Here are basic code examples, these are self-contained and can be run as-is:

{% tabs %}
{% tab title="Python" %}
{% include "../../.gitbook/includes/code-samples/python.md" %}
{% endtab %}

{% tab title="Node.js" %}
{% include "../../.gitbook/includes/code-samples/javascript.md" %}
{% endtab %}

{% tab title="PHP" %}
{% include "../../.gitbook/includes/code-samples/php.md" %}
{% endtab %}

{% tab title="Ruby" %}
{% include "../../.gitbook/includes/code-samples/ruby.md" %}
{% endtab %}

{% tab title="Java" %}
{% include "../../.gitbook/includes/code-samples/java.md" %}
{% endtab %}

{% tab title=".NET" %}
{% include "../../.gitbook/includes/code-samples/dotnet.md" %}
{% endtab %}
{% endtabs %}

### Details on Sending

For details on available options and advanced usage, check the following sections:

* [configure-the-client.md](configure-the-client.md "mention")
* [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
* [send-a-file-or-url.md](send-a-file-or-url.md "mention")

## Processing the Results

Once you've sent the file and retrieved the results, you can start extracting the JSON payload.

The model's fields will be in the `fields` object in the returned JSON, in the `response` variable returned from the above step.

Each key in the `fields` object corresponds to the field's `name` in your model configuration.

You'll want to adapt your processing depending on the [type of field](../../models/data-schema.md#field-types), for example looping over lists.

{% tabs %}
{% tab title="Python" %}
{% include "../../.gitbook/includes/code-samples/process-python.md" %}
{% endtab %}

{% tab title="Node.js" %}
{% include "../../.gitbook/includes/code-samples/process-javascript.md" %}
{% endtab %}

{% tab title="PHP" %}
{% include "../../.gitbook/includes/code-samples/process-php.md" %}
{% endtab %}

{% tab title="Ruby" %}
{% include "../../.gitbook/includes/code-samples/process-ruby.md" %}
{% endtab %}

{% tab title="Java" %}
{% include "../../.gitbook/includes/code-samples/process-java.md" %}
{% endtab %}

{% tab title=".NET" %}
{% include "../../.gitbook/includes/code-samples/process-dotnet.md" %}
{% endtab %}
{% endtabs %}

### Details on Processing

For details on available options and advanced usage, check the following sections:

* [process-the-result.md](process-the-result.md "mention")
