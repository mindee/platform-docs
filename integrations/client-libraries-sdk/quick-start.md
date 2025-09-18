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
Accessing simple values, using the name of the field in the Data Schema.

We can (should!) specify the type of value, the possible types are `str` , `bool` , `float` .\
Note that all types may be `None`.

{% include "../../.gitbook/includes/code-samples/python-process-simplefield.md" %}

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

{% include "../../.gitbook/includes/code-samples/python-process-listfield-simplefield.md" %}

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

{% include "../../.gitbook/includes/code-samples/python-process-objectfield.md" %}

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

{% include "../../.gitbook/includes/code-samples/python-process-listfield-objectfield.md" %}
{% endtab %}

{% tab title="Node.js" %}
Accessing simple values, using the name of the field in the Data Schema.

We need to access the field as a `SimpleField` instance in order to access its value.

{% include "../../.gitbook/includes/code-samples/javascript-process-simplefield.md" %}

Accessing a list of values, where `my_simple_list_field` is the name of the field in the Model.

We need to specify that the field is a `ListField` in order to access its items.

{% include "../../.gitbook/includes/code-samples/javascript-process-listfield-simplefield.md" %}

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

{% include "../../.gitbook/includes/code-samples/javascript-process-objectfield.md" %}

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

We need to specify that the field is a `ListField` in order to access its items.

{% include "../../.gitbook/includes/code-samples/javascript-process-listfield-objectfield.md" %}
{% endtab %}

{% tab title="PHP" %}
Accessing simple values, using the name of the field in the Data Schema.

We need to access the field as a `SimpleField` instance in order to access its value.

{% include "../../.gitbook/includes/code-samples/php-process-simplefield.md" %}

Accessing a list of values, where `my_simple_list_field` is the name of the field in the Model.

We need to specify that the field is a `ListField` in order to access its items.

{% include "../../.gitbook/includes/code-samples/php-process-listfield-simplefield.md" %}

Accessing an object field, where `my_object_field` is the name of the field in the Model. In this hypothetical case, the object has a sub-field named `sub_field`.

{% include "../../.gitbook/includes/code-samples/php-process-objectfield.md" %}

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

We need to specify that the field is a `ListField` in order to access its items.

{% include "../../.gitbook/includes/code-samples/php-process-listfield-objectfield.md" %}
{% endtab %}

{% tab title="Ruby" %}
Accessing simple values, using the name of the field in the Data Schema.

{% include "../../.gitbook/includes/code-samples/ruby-process-simplefield.md" %}

Accessing a list of values, where `my_simple_list_field` is the name of the field in the Model.

{% include "../../.gitbook/includes/code-samples/ruby-process-listfield-simplefield.md" %}

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

{% include "../../.gitbook/includes/code-samples/ruby-process-objectfield.md" %}

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

{% include "../../.gitbook/includes/code-samples/ruby-process-listfield-objectfield.md" %}
{% endtab %}

{% tab title="Java" %}
Accessing simple values, using the name of the field in the Data Schema.

We need to access the field as a `SimpleField` instance in order to access its value.

We also need to specify the type of value, the possible types are `String` , `Boolean` , `Double` .\
Note that all types may be `null`.

{% include "../../.gitbook/includes/code-samples/java-process-simplefield.md" %}

Accessing a list of simple values, where `my_simple_list_field` is the name of the field in the Model.

We need to specify that the field is a `ListField` in order to access its `SimpleItems`.

For each item in the list, we also need to specify the correct field and value type, as described above.

{% include "../../.gitbook/includes/code-samples/java-process-listfield-simplefield.md" %}

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `subfield_1` .

{% include "../../.gitbook/includes/code-samples/java-process-objectfield.md" %}

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

{% include "../../.gitbook/includes/code-samples/java-process-listfield-objectfield.md" %}

Depending on your requirements, this can be simplified using various custom methods.
{% endtab %}

{% tab title=".NET" %}
Accessing simple values, using the name of the field in the Data Schema.

We need to access the field as a `SimpleField` instance in order to access its value.

We also need to specify the type of value, the possible types are `string` , `Boolean` , `Double` .\
Note that all types may be `null`.

{% include "../../.gitbook/includes/code-samples/dotnet-process-simplefield.md" %}

Accessing a list of simple values, where `my_list_field` is the name of the field in the Model.

We need to specify that the field is a `ListField` in order to access its `SimpleItems`.

{% include "../../.gitbook/includes/code-samples/dotnet-process-listfield-simplefield.md" %}

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

{% include "../../.gitbook/includes/code-samples/dotnet-process-objectfield.md" %}

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

{% include "../../.gitbook/includes/code-samples/dotnet-process-listfield-objectfield.md" %}
{% endtab %}
{% endtabs %}

### Details on Processing

For details on available options and advanced usage, check the following sections:

* [process-the-response.md](process-the-response.md "mention")
