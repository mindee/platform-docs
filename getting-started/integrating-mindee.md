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

To process your document using Mindee, simply send the file using the [REST API](../integrations/api-overview.md).

Make a note of your model's ID for use in the API.

When getting started, we recommend using the [#polling](../integrations/api-overview.md#polling "mention") method which will be quickest.

Here are some code examples, these are self-contained and can be run as-is:

{% tabs %}
{% tab title="Python" %}
{% include "../.gitbook/includes/code-samples/python.md" %}
{% endtab %}

{% tab title="JavaScript" %}
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
{% endtabs %}

## Processing the Results

Once you've sent the file and retrieved the results, you can start extracting the JSON payload.

The model's fields will be in the `fields` object in the returned JSON, in the `response` variable returned from the above step.

Each key in the `fields` object corresponds to the field's `name` in your model configuration.

You'll want to adapt your processing depending on the [type of field](../features/models/data-schema.md#field-types), for example looping over lists.

{% tabs %}
{% tab title="Python" %}
Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

```python
my_simple_field = response["inference"]["fields"]["my_simple_field"]
field_value = my_simple_field["value"]
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

```python
my_list_field = response["inference"]["fields"]["my_list_field"]

# access a value at a given position
field_first_value = my_list_field[0]["value"]

# loop over all values in the list
for list_item in my_list_field:
    item_value = list_item["value"]
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```python
object_field = response["inference"]["fields"]["my_object_field"]
sub_field_value = object_field["sub_field"]["value"]
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```python
object_list_field = response["inference"]["fields"]["my_object_list_field"]

# access an object at a given position
object_item_0 = object_list_field[0]
sub_field_0_value = object_item_0["sub_field"]["value"]

# loop over object lists
for object_item in object_list_field:
  sub_field_value = object_item["sub_field"]["value"]
```
{% endtab %}

{% tab title="JavaScript" %}
Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

```javascript
const mySimpleField = response.inference.fields.my_simple_field;
const fieldValue = mySimpleField.value;
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

```javascript
const myListField = response.inference.fields.my_list_field;

// access a value at a given position
const fieldFirstValue = myListField[0].value;

// loop over all values in the list
for (const listItem of myListField) {
    const itemValue = listItem.value;
}
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```javascript
const objectField = response.inference.fields.my_object_field;
const subFieldValue = objectField.sub_field.value;
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```javascript
const objectListField = response.inference.fields.my_object_list_field;

// access an object at a given position
const objectItem0 = objectListField[0];
const subField0Value = objectItem0.sub_field.value;

// loop over object lists
for (const objectItem of objectListField) {
    const subFieldValue = objectItem.sub_field.value;
}
```
{% endtab %}

{% tab title="Ruby" %}
Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

```ruby
my_simple_field = response["inference"]["fields"]["my_simple_field"]
field_value = my_simple_field["value"]
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

```ruby
my_list_field = response["inference"]["fields"]["my_list_field"]

# access a value at a given position
field_first_value = my_list_field[0]["value"]

# loop over all values in the list
my_list_field.each do |list_item|
  item_value = list_item["value"]
end
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```ruby
object_field = response["inference"]["fields"]["my_object_field"]
sub_field_value = object_field["sub_field"]["value"]
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```ruby
object_list_field = result["inference"]["fields"]["my_object_list_field"]

# access an object at a given position
object_item_0 = object_list_field[0]
sub_field_0_value = object_item_0["sub_field"]["value"]

# loop over object lists
object_list_field.each do |object_item|
  sub_field_value = object_item["sub_field"]["value"]
end
```
{% endtab %}

{% tab title="PHP" %}
Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

```php
$my_simple_field = $response["inference"]["fields"]["my_simple_field"];
$field_value = $my_simple_field["value"];
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

```php
$my_list_field = $response["inference"]["fields"]["my_list_field"];

// access a value at a given position
$field_first_value = $my_list_field[0]["value"];

// loop over all values in the list
foreach ($my_list_field as $list_item) {
    $item_value = $list_item["value"];
}
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```php
$object_field = $response["inference"]["fields"]["my_object_field"];
$sub_field_value = $object_field["sub_field"]["value"];
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```php
$object_list_field = $response["inference"]["fields"]["my_object_list_field"];

// access an object at a given position
$object_item_0 = $object_list_field[0];
$sub_field_0_value = $object_item_0["sub_field"]["value"];

// loop over object lists
foreach ($object_list_field as $object_item) {
    $sub_field_value = $object_item["sub_field"]["value"];
}
```
{% endtab %}

{% tab title=".NET" %}
Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

We need to specify that the field is a `SimpleField` in order to access its `Value`.

```csharp
var mySimpleField = response.Inference.Result.Fields["my_simple_field"];
var fieldValue = mySimpleField.SimpleField.Value;
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

We need to specify that the field is a `ListField` in order to access its `Items`.

```csharp
var myListField = response.Inference.Result.Fields["my_list_field"];

// access a value at a given position
var fieldFirstValue = myListField.ListField.Items[0].SimpleField.Value;

// loop over all values in the list
foreach (var listItem in myListField.ListField.Items)
{
    var itemValue = listItem.SimpleField.Value;
}
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```csharp
var objectField = response.Inference.Fields["my_object_field"];
var subField = objectField.ObjectField.Fields["sub_field"].Value;
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```csharp
objectListField = response.Inference.Fields["my_object_list_field"];

// access an object at a given position
$object_item_0 = $object_list_field.ListField.Items[0];
$sub_field_0_value = $object_item_0.ObjectField.Items["sub_field"].Value;

// loop over object lists
foreach ($object_list_field.ListField.Items as $object_item) {
    $sub_field_value = $object_item.ObjectField.Fields["sub_field"].Value;
}
```
{% endtab %}
{% endtabs %}

