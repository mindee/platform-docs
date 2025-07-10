---
icon: plug-circle-check
---

# Integrating Mindee

Once you have your model set up, you'll want to start using it!

## API key

Make sure you've created your API Key before continuing.

To create and manage your API keys, go to the "[API Keys](https://app.mindee.com/api-keys)" section on the Mindee Platform.

Click on create API Key, choose a name for this API Key, and validate.

You're now ready to go!

## Sending a File

To process your document using Mindee, simply send the file using the [REST API](../integrations/api-overview/).

Make a note of your model's ID for use in the API.

When getting started, we recommend using the [#polling](../integrations/api-overview/#polling "mention") method which will be quickest (unless you happen to already have access to a public-facing Web server).

Here are some code examples, these are self-contained and can be run as-is:

{% tabs %}
{% tab title="Python" %}
{% include "../.gitbook/includes/code-samples/python.md" %}
{% endtab %}

{% tab title="Node.js" %}
{% include "../.gitbook/includes/code-samples/javascript.md" %}
{% endtab %}

{% tab title="Ruby" %}
{% include "../.gitbook/includes/code-samples/ruby.md" %}
{% endtab %}

{% tab title="PHP" %}
{% include "../.gitbook/includes/code-samples/php.md" %}
{% endtab %}

{% tab title=".NET" %}
{% include "../.gitbook/includes/code-samples/dotnet.md" %}
{% endtab %}

{% tab title="Java" %}
{% include "../.gitbook/includes/code-samples/java.md" %}
{% endtab %}
{% endtabs %}

## Processing the Results

Once you've sent the file and retrieved the results, you can start extracting the JSON payload.

The model's fields will be in the `fields` object in the returned JSON, in the `response` variable returned from the above step.

Each key in the `fields` object corresponds to the field's `name` in your model configuration.

You'll want to adapt your processing depending on the [type of field](../features/models/data-schema.md#field-types), for example looping over lists.

{% tabs %}
{% tab title="Python" %}
{% include "../.gitbook/includes/code-samples/process-python.md" %}
{% endtab %}

{% tab title="Node.js" %}
{% include "../.gitbook/includes/code-samples/process-javascript.md" %}
{% endtab %}

{% tab title="Ruby" %}
{% include "../.gitbook/includes/code-samples/process-ruby.md" %}
{% endtab %}

{% tab title="PHP" %}
{% include "../.gitbook/includes/code-samples/process-php.md" %}
{% endtab %}

{% tab title=".NET" %}
{% include "../.gitbook/includes/code-samples/process-dotnet.md" %}
{% endtab %}

{% tab title="Java" %}
{% include "../.gitbook/includes/code-samples/process-java.md" %}
{% endtab %}
{% endtabs %}
