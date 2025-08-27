---
description: >-
  Reference documentation on processing results using the Mindee client
  libraries.
icon: brain-circuit
---

# Process the Result

{% include "../../.gitbook/includes/this-is-reference-documenta....md" %}

## Requirements

You'll need to have already sent a file or URL as described in the [send-a-file-or-url.md](send-a-file-or-url.md "mention") section.

## Overview

Depending on how you've sent the file, there are two ways of obtaining the result.

If you've sent via polling (or polling and webhook) you'll get the response directly in your method call.

If you've sent only via webhook, you'll receive the response on your Web server.

Here we'll go over how you can best process the results.

## Load From Webhook

If you're using the webhook pattern, you'll need to use the payload sent to your Web server.

Reading the callback data will vary greatly depending on your HTTP server.\
This is therefore beyond the scope of this example.

Regardless of how you access the JSON payload sent by the Mindee servers, loading this data is done by using a LocalResponse class.

Once it is loaded you can access the data in exactly the same way as a polling response.

To verify the HMAC signature, you'll need the Signing Secret from the webhook:

<figure><img src="../../.gitbook/assets/webhook-copy-secret.png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Python" %}
Assuming you're able to get the raw HTTP request via the variable `request` .

```python
from mindee import LocalResponse, InferenceResponse

# Load the JSON string sent by the Mindee webhook POST callback.
local_response = LocalResponse(request.body())

# You can also load the json from a local path.
# local_response = LocalResponse("path/to/my/file.ext")

# Optionally: verify the HMAC signature
# You'll need to get the "X-Signature" custom HTTP header.
hmac_signature = request.headers.get("X-Signature")
is_valid = local_response.is_valid_hmac_signature(
    "obviously-fake-secret-key", hmac_signature
)
if not is_valid:
    raise Error("Bad HMAC signature! Is someone trying to do evil?")

# Deserialize the response into objects
response = local_response.deserialize_response(InferenceResponse)
```
{% endtab %}

{% tab title="Node.js" %}
Assuming you're able to get the raw HTTP request via the variable `request` .

```javascript
async handleMindeeResponse(data, hmacSignature) {
  const localResponse = new mindee.LocalResponse(data);
  await localResponse.init();

  const isValid = localResponse.isValidHmacSignature(
      "obviously-fake-secret-key", hmacSignature
    );
  if (!isValid) {
    throw Error("Bad HMAC signature! Is someone trying to do evil?");
  }
  const response = await localResponse.deserializeResponse(
    mindee.InferenceResponse
  );
}

// Getting the data could look something like this.
// Will vary depending on your implementation.
async handleMindeePost(request, response) {
  let body = "";
  request.on("data", function (data) {
    body += data;
  });
  req.on("end", function () {
    // Optionally: verify the HMAC signature
    // You'll need to get the "X-Signature" custom HTTP header.
    const hmacSignature = request.headers.get("X-Signature");
    
    await handleMindeeResponse(data, hmacSignature);
  });
}
```
{% endtab %}

{% tab title="Java" %}
Assuming you have a Web server instance `myHttpServer` .

```java

// Load the JSON string sent by the Mindee webhook POST callback.
String jsonData = myHttpServer.getPostBodyAsString();
LocalResponse localResponse = new LocalResponse(jsonData);

// Verify the HMAC signature.
// You'll need to get the "X-Signature" custom HTTP header.
String hmacSignature = myHttpServer.getHeader("X-Signature");
boolean isValid = localResponse.isValidHmacSignature(
    "obviously-fake-secret-key", hmacSignature
);
if (!isValid) {
    throw new Exception("Bad HMAC signature! Is someone trying to do evil?");
}

// You can also use a File object as the input.
//LocalResponse localResponse = new LocalResponse(
//    new File("/path/to/file.json"));

// Deserialize the response into objects
InferenceResponse response = localResponse.deserializeResponse(
    InferenceResponse.class
);

// Print a summary of the parsed data
System.out.println(response.getInference().toString());
```
{% endtab %}

{% tab title=".NET" %}
Assuming you're able to get the raw HTTP request via the variable `request` .

```csharp
using Mindee.Parsing.V2;

public void HandleMindeeCallback(HttpRequest request)
{
    LocalResponse localResponse;

    using (var reader = new StreamReader(request.Body))
    {
        localResponse = new LocalResponse(reader.ReadToEnd());
    }
    
    // Verify the HMAC signature.
    // You'll need to get the "X-Signature" custom HTTP header.
    string hmacSignature = request.Headers.get("X-Signature");
    bool isValid = localResponse.IsValidHmacSignature(
         "obviously-fake-secret-key", hmacSignature);
    if (!isValid)
        throw new Exception("Bad HMAC signature! Is someone trying to do evil?");

    // Deserialize the response into objects
    var response = localResponse.DeserializeResponse<InferenceResponse>();
    
    // Print a summary of the parsed data
    System.Console.WriteLine(response.Inference);
}
```
{% endtab %}
{% endtabs %}

## The Inference Object

This is the top-level object in the response.

It contains the following attributes:

* `id` UUID of the inference
* `model` Model used for the inference
* `file` Metadata concerning the file used for the inference
* `result` Result of inference processing, the most important portion of the response.\
  See the [#accessing-result-fields](process-the-result.md#accessing-result-fields "mention") section.

### File Metadata

You can access various metadata concerning the file sent for processing.

{% tabs %}
{% tab title="Python" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```python
from mindee import InferenceResponse
from mindee.parsing.v2 import InferenceFile

def handle_response(response: InferenceResponse):
    inference_file: InferenceFile = response.inference.file

    # various attributes are available, such as:
    filename: str = inference_file.name
    page_count: int = file.page_count
```
{% endtab %}

{% tab title="Node.js" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```javascript
handleResponse(response) {
  const file = response.inference.file;
  
  // various attributes are available, such as:
  const filename = file.name;
  const pageCount = file.pageCount;
}
```
{% endtab %}

{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.parsing.v2.InferenceFile;

public void handleResponse(InferenceResponse response) {
    InferenceFile file = response.inference.getFile();

    // various attributes are available, such as:
    String filename = file.getName();
    int pageCount = file.getPageCount();
}
```
{% endtab %}

{% tab title=".NET" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```csharp
using Mindee.Parsing.V2;

public void HandleResponse(InferenceResponse response)
{
    InferenceFile file = response.Inference.File;

    // various attributes are available, such as:
    string filename = file.Name;
    int pageCount = file.PageCount;
}
```
{% endtab %}
{% endtabs %}

## Accessing Result Fields

Fields are completely dynamic and depend on your model's [data-schema.md](../../models/data-schema.md "mention").

In the client library, you'll have access to the various fields as a key-value mapping type (Python's `dict`, Java's `HashMap`, etc).

Accessing a field is done via its name in the Data Schema.

Each field will be one of the following types:

* A single value, `SimpleField` class.
* A nested object (sub-fields), `ObjectField` class.
* A list or array of fields, `ListField` class.

## Single-Value Field - SimpleField

Basic field type having the `value` attribute.\
See the [#value](process-the-result.md#value "mention") section below.

In addition, the `Simplefield` class has [#confidence](process-the-result.md#confidence "mention") and [#locations](process-the-result.md#locations "mention") attributes.

{% tabs %}
{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.parsing.v2.field.InferenceFields;
import com.mindee.parsing.v2.field.SimpleField;

public void handleResponse(InferenceResponse response) {
    InferenceFields fields = response.inference.getResult().getFields();

    SimpleField simpleField = fields.getSimpleField("my_simple_field");
}
```
{% endtab %}

{% tab title=".NET" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```csharp
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    InferenceFields fields = response.Inference.Result.Fields;

    SimpleField mySimpleField = fields["my_simple_field"].SimpleField;
}
```
{% endtab %}
{% endtabs %}

### `value`

The extracted data value.\
Possible types: string, number (integer or floating-point), boolean.\
All types can be null.

On the platform, you can specify date and classification types.\
These are returned as strings.

For statically-typed languages (C#, Java), the client library will always return a nullable `double` for number values.

{% tabs %}
{% tab title="Java" %}
The `value` attribute is an `Object` type under the hood.

You'll need to explicitly declare the type, otherwise the code will likely not compile.\
Take a look at your Data Schema to know which type to declare.

```java
import com.mindee.parsing.v2.field.InferenceFields;

public void handleResponse(InferenceResponse response) {
    InferenceFields fields = response.inference.getResult().getFields();

    // texts, dates, classifications ...
    String stringFieldValue = fields.getSimpleField("string_field")
        .getStringValue();

    // a JSON float will be a Double
    Double floatFieldValue = fields.getSimpleField("float_field")
        .getDoubleValue();

    // even if the API always returns an integer, the type will be Double
    Double intFieldValue = fields.getSimpleField("int_field")
        .getDoubleValue();

    // booleans
    Boolean boolFieldValue = fields.getSimpleField("bool_field")
        .getBooleanValue();
}
```

If the wrong type method is used, an exception will be raised, something like this:

```
ClassCast class java.lang.String cannot be cast to class java.lang.Double
```
{% endtab %}

{% tab title=".NET" %}
The `Value` attribute is a `dynamic` type under the hood.

You should explicitly declare the type, this is recommended for clarity.\
Take a look at your Data Schema to know which type to declare.

```csharp
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    // texts, dates, classifications ...
    string stringFieldValue = fields["string_field"].SimpleField.Value;

    // a JSON float will be a Double
    Double floatFieldValue = fields["float_field"].SimpleField.Value;

    // even if the API always returns an integer, the type will be Double
    Double intFieldValue = fields["int_field"].SimpleField.Value;

    // booleans
    Boolean boolFieldValue = fields["bool_field"].SimpleField.Value;
}
```

If the wrong type is declared, an exception will be raised, something like this:

```
RuntimeBinderException : Cannot implicitly convert type 'string' to 'double'
```
{% endtab %}
{% endtabs %}

## Nested Object Field - ObjectField

Field having a `fields` attribute which is a hash table (Python's `dict`, Java's `HashMap`, etc) of sub-fields.\
See the [#fields](process-the-result.md#fields "mention") section below.

In addition, the `ObjectField` class has [#confidence](process-the-result.md#confidence "mention") and [#locations](process-the-result.md#locations "mention") attributes.

{% tabs %}
{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.parsing.v2.field.InferenceFields;
import com.mindee.parsing.v2.field.ObjectField;

public void handleResponse(InferenceResponse response) {
    InferenceFields fields = response.inference.getResult().getFields();

    ObjectField objectField = fields.getObjectField("my_object_field");
}
```
{% endtab %}

{% tab title=".NET" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```csharp
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    InferenceFields fields = response.Inference.Result.Fields;

    ObjectField myObjectField = fields["my_object_field"].ObjectField;
}
```
{% endtab %}
{% endtabs %}

### `fields`

The sub-fields as a key-value mapping type (Python's `dict`, Java's `HashMap`, etc).

Accessing a sub-field is done via its name in the Data Schema.

Each sub-field will be a [#single-value-field-simplefield](process-the-result.md#single-value-field-simplefield "mention").

{% tabs %}
{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.parsing.v2.field.InferenceFields;
import com.mindee.parsing.v2.field.ListField;
import com.mindee.parsing.v2.field.ObjectField;
import com.mindee.parsing.v2.field.SimpleField;

public void handleResponse(InferenceResponse response) {
    InferenceFields fields = response.inference.getResult().getFields();

    ObjectField objectField = fields.getObjectField("my_object_field");
    
    HashMap<String, SimpleField> subFields = objectField.getSimpleFields();
    
    // grab a single sub-field
    SimpleField subfield1 = subFields.get("subfield_1");
    
    // loop over sub-fields
    for (Map.Entry<String, SimpleField> entry : subFields.entrySet()) {
        String fieldName = entry.getKey();
        SimpleField subField = entry.getValue();
    }
}
```
{% endtab %}

{% tab title=".NET" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```csharp
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    InferenceFields fields = response.Inference.Result.Fields;

    ObjectField objectField = fields["my_object_field"].ObjectField;

    Dictionary<string, SimpleField> subFields = objectField.SimpleFields;

    // grab a single sub-field
    SimpleField subField1 = subFields["subfield_1"];

    // loop over sub-fields
    foreach (KeyValuePair<string, SimpleField> entry in subFields)
    {
        string fieldName = entry.Key;
        SimpleField subField = entry.Value;
    }
}
```
{% endtab %}
{% endtabs %}

## List of Fields - ListField

Field having an `items` attribute which is a list of fields.\
See the [#items](process-the-result.md#items "mention") section below.

In addition, the `ListField` class has a [#confidence](process-the-result.md#confidence "mention") attribute.

{% tabs %}
{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.parsing.v2.field.InferenceFields;
import com.mindee.parsing.v2.field.ListField;

public void handleResponse(InferenceResponse response) {
    InferenceFields fields = response.inference.getResult().getFields();

    ListField listField = fields.getListField("my_list_field");
}
```
{% endtab %}

{% tab title=".NET" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```csharp
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    InferenceFields fields = response.Inference.Result.Fields;

    ListField myListField = fields["my_list_field"].ListField;
}
```
{% endtab %}
{% endtabs %}

### `items`

Each item in the list can _theoretically_ be of any type (single, multi, list).\
**In practice:** Each field in the list will be one of:

* [#single-value-field-simplefield](process-the-result.md#single-value-field-simplefield "mention")
* [#nested-object-field-objectfield](process-the-result.md#nested-object-field-objectfield "mention")

There will **not** be a mix of both types in the same list.

{% tabs %}
{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.parsing.v2.field.InferenceFields;
import com.mindee.parsing.v2.field.ListField;
import com.mindee.parsing.v2.field.ObjectField;
import com.mindee.parsing.v2.field.SimpleField;

public void handleResponse(InferenceResponse response) {
    InferenceFields fields = response.inference.getResult().getFields();

    //
    // List of Simple fields
    //

    ListField fieldSimpleList = fields.getListField("my_simple_list_field");

    List<SimpleField> simpleItems = fieldSimpleList.getSimpleItems();

    // Loop over the list of Simple fields
    for (SimpleField itemField : simpleItems) {
        // Choose the appropriate value type accessor method:
        // String, Double, Boolean
        String fieldValue = itemField.getStringValue();
    }

    //
    // List of Object fields
    //

    ListField fieldObjectList = fields.getListField("my_object_list_field");

    List<ObjectField> objectItems = listField.getObjectItems();

    // Loop over the list of Object fields
    for (ObjectField itemField : objectItems) {
    
        // Object sub-fields will always be Simple fields
        HashMap<String, SimpleField> subFields = itemField.getSimpleFields();

        // grab a single sub-field
        SimpleField subfield1 = subFields.get("subfield_1");
        
        // Choose the appropriate value type accessor method:
        // String, Double, Boolean
        String subFieldValue = subfield1.getStringValue();

        // loop over sub-fields
        for (Map.Entry<String, SimpleField> entry : subFields.entrySet()) {
            String fieldName = entry.getKey();
            SimpleField subField = entry.getValue();
        }
    }
}
```
{% endtab %}

{% tab title=".NET" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```csharp
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    InferenceFields fields = response.Inference.Result.Fields;

    //
    // List of Simple fields
    //

    ListField fieldSimpleList = fields["my_simple_list_field"].ListField;

    List<SimpleField> simpleItems = fieldSimpleList.SimpleItems;

    // Loop over the list of Simple fields
    foreach (SimpleField itemField in simpleItems)
    {
        // Choose the appropriate value type:
        // string, Double, Boolean
        string fieldValue = itemField.Value;
    }

    //
    // List of Object fields
    //
    
    ListField fieldObjectList = fields["my_simple_list_field"].ListField;
    
    List<ObjectField> objectItems = fieldObjectList.ObjectItems;
    
    // Loop over the list of Object fields
    foreach (ObjectField itemField in objectItems)
    {
        Dictionary<string, SimpleField> subFields = objectField.SimpleFields;
    
        // grab a single sub-field
        SimpleField subField1 = subFields["subfield_1"];
        
        // Choose the appropriate value type:
        // string, Double, Boolean
        string subFieldValue = subField1.Value;
    
        // loop over sub-fields
        foreach (KeyValuePair<string, SimpleField> entry in subFields)
        {
            string fieldName = entry.Key;
            SimpleField subField = entry.Value;
        }
    }
}
```
{% endtab %}
{% endtabs %}

## Optional Field Attributes

These field attributes are only filled when their respective features are activated.

The attributes are always present even when not activated.

### `confidence`

The confidence level of the extracted value.

The data are only filled if the [automation-confidence-score.md](../../models/automation-confidence-score.md "mention") feature is activated.

The attribute is always present, in case of Confidence Score not activated, it will always be null.

The attribute value will be one of: `Certain`, `High`, `Medium`, `Low` .

All languages use the appropriate enum type.

{% tabs %}
{% tab title="Python" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```python
from mindee.parsing.v2.field import FieldConfidence

fields = response.inference.result.fields

confidence = fields["my_simple_field"].confidence

# compare using the enum `FieldConfidence`
is_certain = confidence == FieldConfidence.CERTAIN
```
{% endtab %}

{% tab title="Node.js" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```javascript
fields = response.inference.result.fields;

const confidence = fields.get("my_simple_field")?.confidence

// compare using the enum `FieldConfidence`
const isCertain = confidence === FieldConfidence.Certain;
```
{% endtab %}

{% tab title="PHP" %}
Using the `$response` deserialized object from either the polling response or a webhook payload.

```php
use Mindee\Parsing\V2\Field\FieldConfidence;

$fields = $response->inference->result->fields;

$confidence = $fields->get('my_simple_field')->confidence;

// compare using the enum `FieldConfidence`
$isCertain = $confidence === FieldConfidence::CERTAIN;
```
{% endtab %}

{% tab title="Ruby" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```ruby
fields = response.inference.result.fields

confidence = fields["my_simple_field"].confidence

# compare using the enum `FieldConfidence`
is_certain = confidence == Mindee::Parsing::V2::Field::FieldConfidence.CERTAIN
```
{% endtab %}

{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.parsing.v2.InferenceResponse;
import com.mindee.parsing.v2.field.FieldConfidence;
import com.mindee.parsing.v2.field.InferenceFields;

public void handleResponse(InferenceResponse response) {
    InferenceFields fields = inference.getResult().getFields();

    // choose the appropriate field type accessor method: Simple, Object, List
    FieldConfidence confidence = fields.getSimpleField("my_simple_field")
        .getConfidence();

    // compare using the enum `FieldConfidence`
    boolean isCertain = confidence == FieldConfidence.Certain;
}
```
{% endtab %}

{% tab title=".NET" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```csharp
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    InferenceFields fields = response.Inference.Result.Fields;

    // nullable enum since presence depends on feature activation
    FieldConfidence? confidence = fields["my_simple_field"]
        .SimpleField.Confidence;

    // compare using the enum `FieldConfidence`
    bool isCertain = confidence == FieldConfidence.Certain;
}
```
{% endtab %}
{% endtabs %}

### `locations`

A list of the field's locations on the document.

The data are only filled if the [polygons-bounding-boxes.md](../../models/polygons-bounding-boxes.md "mention") feature is activated.

It's possible for a single field to have multiple locations, for example when an invoice item spans two pages.

Each location has a page index and a Polygon.

Page indexes are 0-based, so the first page is `0`.

A Polygon class contains a list of Points, the specific implementation will depend on the language.

Points are listed in clockwise order, where index `0` is top left.

Point X,Y coordinates are normalized floats from 0.0 to 1.0, relative to the page dimensions.

{% tabs %}
{% tab title="Node.js" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```javascript
fields = response.inference.result.fields;

const locations = fields.get("my_simple_field")?.locations;

// accessing the polygon
const polygon = locations![0].polygon!;

// accessing points: the Polygon class extends Array<Point>
double topX = polygon[0][0];

// accessing the page index on which the polygon is
const pageIndex = locations![0].page!;
```
{% endtab %}

{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.geometry.Point;
import com.mindee.geometry.Polygon;
import com.mindee.parsing.v2.InferenceResponse;
import com.mindee.parsing.v2.field.FieldLocation;
import com.mindee.parsing.v2.field.InferenceFields;
import java.util.List;

public void handleResponse(InferenceResponse response) {
    InferenceFields fields = response.inference.getResult().getFields();

    // choose the appropriate field type accessor method: Simple, Object
    List<FieldLocation> locations = fields.getSimpleField("my_simple_field")
        .getLocations();

    // accessing the polygon
    Polygon polygon = locations.get(0).getPolygon();

    // accessing points
    List<Point> points = polygon.getCoordinates();
    double topX = points.get(0).getX();

    // there are geometry functions available in the Polygon class
    Point center = polygon.getCentroid();

    // accessing the page index on which the polygon is
    int pageIndex = locations.get(0).getPage();
}
```
{% endtab %}

{% tab title=".NET" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```csharp
using Mindee.Parsing.V2.Field;
using Mindee.Geometry;

public void HandleResponse(InferenceResponse response)
{
    InferenceFields fields = response.Inference.Result.Fields;

    List<FieldLocation> locations = fields["my_simple_field"]
        .SimpleField.Locations;

    // accessing the polygon
    Polygon polygon = locations.First().Polygon;

    // accessing points: the Polygon class extends List<Point>
    double topX = polygon[0].X;

    // alternative notation, since the Point class extends List<double>
    // double topX = polygon[0][0];

    // there are geometry functions available in the Polygon class
    Point center = polygon.GetCentroid();

    // accessing the page index on which the polygon is
    int pageIndex = locations.First().Page;
}
```
{% endtab %}
{% endtabs %}
