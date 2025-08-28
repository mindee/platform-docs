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
Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

We need to access the field as a `SimpleField` instance in order to access its `value`.

We also need to specify the type of `value` , the possible types are `String` , `Boolean` , `Double` .\
Notice that these are all classes, not primitives: this is to allow `null` values.

```java
import com.mindee.parsing.v2.field.*;


InferenceFields fields = response.getInference().getResult().getFields();
SimpleField mySimpleField = fields.getSimpleField("my_simple_field");

// Showing a String field example.
// You'll need to choose one of the possible classes:
// String, Double, Boolean
String fieldValue = mySimpleField.getStringValue();
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

We need to specify that the field is a `ListField` in order to access its `SimpleItems`.

For each item in the list, we also need to specify the correct field and value type, as described above.

```java
import com.mindee.parsing.v2.field.*;


InferenceFields fields = response.getInference().getResult().getFields();
ListField myListField = fields.getLisField("my_list_field");

List<SimpleField> myListFieldItems = myListField.getSimpleItems();

// Access a value at a given position
// You'll need to choose one of the possible classes:
// String, Double, Boolean
String fieldFirstValue = myListFieldItems.get(0).getStringValue();

// loop over all values in the list
for (SimpleField listItem : myListFieldItems) {

    // You'll need to choose one of the possible classes:
    // String, Double, Boolean
    String itemValue = listItem.getStringValue();
}
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```java
import com.mindee.parsing.v2.field.*;


InferenceFields fields = response.getInference().getResult().getFields();
ObjectField objectField = fields.getObjectField("my_object_field");

// Useful to separate out the fields mapping for easier access
InferenceFields fieldObjectFields = objectField.getSimpleFields();

// The subfield is handled like any other SimpleField
SimpleField subField = fieldObjectFields.get("sub_field");

// Showing a String field example, other types are: String, Double, Boolean
String itemValue = subField.getStringValue();
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```java
import com.mindee.parsing.v2.field.*;


InferenceFields fields = response.getInference().getResult().getFields();

ListField objectListField = fields.getListField("my_object_list_field");

// Useful to separate out the fields list for easier access
List<ObjectField> objectItems = fieldSimpleList.getObjectItems();

// access an object at a given position
ObjectField objectField0 = objectItems.get(0);
SimpleField subField0 = objectField0.getSimpleField("sub_field");
// Showing a String field example, other types are: String, Double, Boolean
String subField0Value = subField0.getStringValue();

// Loop over the list of Object fields
for (ObjectField itemField : objectItems) {
    // Object sub-fields will always be Simple fields
    HashMap<String, SimpleField> subFields = itemField.getSimpleFields();
    
    // grab a single sub-field
    SimpleField subfield1 = subFields.get("subfield_1");
    
    // Choose the appropriate value type accessor method:
    // String, Double, Boolean
    String subFieldValue = subfield1.getStringValue();
}
```

Depending on your requirements, this can be simplified using various custom methods.
{% endtab %}

{% tab title=".NET" %}
{% include "../../.gitbook/includes/code-samples/process-dotnet.md" %}
{% endtab %}
{% endtabs %}

### Details on Processing

For details on available options and advanced usage, check the following sections:

* [process-the-result.md](process-the-result.md "mention")
