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

public void HandleMindeeResponse(HttpRequest request)
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

## Accessing Fields

Fields are completely dynamic and depend on your model's [data-schema.md](../../models/data-schema.md "mention").

In the client library, you'll have access to the various fields as a mapping type (Python's `dict`, Java's `HashMap`, etc).

Accessing a field is done via its name in the Data Schema.

Each field will be one of the following types:

* A single value, `SimpleField` class.
* A nested object (sub-fields), `ObjectField` class.
* A list or array of fields, `ListField` class.

## Single-Value Field - SimpleField

Basic field type having the `value` attribute.

In addition, the `Simplefield` class has [#confidence](process-the-result.md#confidence "mention") and [#locations](process-the-result.md#locations "mention") attributes.

### `value`

The extracted data value.\
Possible types: string, number (integer or floating-point), boolean.\
All types can be null.

On the platform, you can specify date and classification types.\
These are returned as strings.

For statically-typed languages (C#, Java), the client library will always return a nullable `double` for number values.

{% tabs %}
{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.parsing.v2.field.InferenceFields;
import com.mindee.parsing.v2.field.SimpleField;

InferenceFields fields = response.inference.getResult().getFields();

SimpleField simpleField = fields.get("my_simple_field").getSimpleField();
```

The `value` attribute is an `Object` type under the hood.

You'll need to explicitly declare the type, otherwise the code will likely not compile.\
Take a look at your Data Schema to know which type to declare.

```java
import com.mindee.parsing.v2.field.InferenceFields;

InferenceFields fields = response.inference.getResult().getFields();

// texts, dates, classifications ...
String stringFieldValue = (String) fields.get("string_field").getSimpleField()
    .getValue();

// a JSON float will be a Double
Double floatFieldValue = (Double) fields.get("float_field").getSimpleField()
    .getValue();

// even if the API always returns an integer, the type will be Double
Double intFieldValue = (Double) fields.get("int_field").getSimpleField()
    .getValue();

// booleans
Boolean boolFieldValue = (Boolean) fields.get("bool_field").getSimpleField()
    .getValue();
```

If the wrong type is declared, an exception will be raised, something like this:

```
ClassCast class java.lang.String cannot be cast to class java.lang.Double
```
{% endtab %}

{% tab title=".NET" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```csharp
using Mindee.Parsing.V2.Field;

InferenceFields fields = response.Inference.Result.Fields;

SimpleField mySimpleField = fields["my_simple_field"].SimpleField;
```

The `Value` attribute is a `dynamic` type under the hood.

You should explicitly declare the type, this is recommended for clarity.\
Take a look at your Data Schema to know which type to declare.

```csharp
using Mindee.Parsing.V2.Field;

// texts, dates, classifications ...
string stringFieldValue = fields["string_field"].SimpleField.Value;

// a JSON float will be a Double
Double floatFieldValue = fields["float_field"].SimpleField.Value;

// even if the API always returns an integer, the type will be Double
Double intFieldValue = fields["int_field"].SimpleField.Value;

// booleans
Boolean boolFieldValue = fields["bool_field"].SimpleField.Value;
```

If the wrong type is declared, an exception will be raised, something like this:

```
RuntimeBinderException : Cannot implicitly convert type 'string' to 'double'
```
{% endtab %}
{% endtabs %}

## Nested Object Field - ObjectField

Field having a `fields` attribute which is a hash table (Python's `dict`, Java's `HashMap`, etc) of sub-fields.

In addition, the `ObjectField` class has [#confidence](process-the-result.md#confidence "mention") and [#locations](process-the-result.md#locations "mention") attributes.

### `fields`

Each field can _theoretically_ be of any type (single, multi, list).\
**In practice:** we limit to a single value, meaning no recursive objects nor lists.

Each sub-field will be a [#single-value-field-simplefield](process-the-result.md#single-value-field-simplefield "mention").

## List of Fields - ListField

Field having an `items` attribute which is a list of fields.

In addition, the `ListField` class has a [#confidence](process-the-result.md#confidence "mention") attribute.

### `items`

Each item in the list can _theoretically_ be of any type (single, multi, list).\
**In practice:** we limit items to be either single or multi field, meaning no lists of lists.

Each field in the list will be one of:

* [#single-value-field-simplefield](process-the-result.md#single-value-field-simplefield "mention")
* [#multiple-value-field-objectfield](process-the-result.md#multiple-value-field-objectfield "mention")

There will **not** be a mix of both types in the same list.

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

public void handleFieldConfidence(InferenceResponse response) {
    InferenceFields fields = inference.getResult().getFields();

    FieldConfidence confidence = fields.get("my_simple_field")
        .getSimpleField() // needs adjustment depending on actual field type
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

InferenceFields fields = response.Inference.Result.Fields;

// nullable enum since presence depends on feature activation
FieldConfidence? confidence = fields["my_simple_field"].SimpleField.Confidence;

// compare using the enum `FieldConfidence`
bool isCertain = confidence == FieldConfidence.Certain;
```
{% endtab %}
{% endtabs %}

### `locations`

A list of the field's locations on the document.

The data are only filled if the [polygons-bounding-boxes.md](../../models/polygons-bounding-boxes.md "mention") feature is activated.

It's possible for a single field to have multiple locations, for example when an invoice item spans two pages.

Each location has a page index and a polygon.

{% tabs %}
{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.geometry.Point;
import com.mindee.geometry.Polygon;
import com.mindee.parsing.v2.InferenceResponse;
import com.mindee.parsing.v2.field.FieldLocation;
import com.mindee.parsing.v2.field.InferenceFields;
import java.util.List;

public void handleFieldLocation(InferenceResponse response) {
    InferenceFields fields = response.inference.getResult().getFields();

    List<FieldLocation> locations = fields.get("my_simple_field")
        .getSimpleField() // needs adjustment depending on actual field type
        .getLocations();

    // accessing the polygon
    Polygon polygon = Polygon polygon = locations.get(0).getPolygon();

    // accessing coordinates
    List<Point> coords = polygon.getCoordinates();
    double topX = coords.get(0).getX();

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

InferenceFields fields = response.Inference.Result.Fields;

List<FieldLocation> locations = fields["my_simple_field"].SimpleField.Locations;

// accessing the polygon
Polygon polygon = locations.First().Polygon;

// accessing coordinates: the Polygon class extends List<Point>
double topX = polygon[0].X;

// alternative notation, since the Point class extends List<double>
// double topX = polygon[0][0];

// there are geometry functions available in the Polygon class
Point center = polygon.GetCentroid();

// accessing the page index on which the polygon is
int pageIndex = locations.First().Page;
```
{% endtab %}
{% endtabs %}
