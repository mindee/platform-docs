---
description: >-
  Reference documentation on processing result fields of the response using the
  Mindee client libraries.
icon: brain-circuit
---

# Process Result Fields

{% include "../../.gitbook/includes/this-is-reference-documenta....md" %}

## Requirements

You'll need to have a response object as described in the [process-the-response.md](process-the-response.md "mention") section.

## Accessing Result Fields

Fields are completely dynamic and depend on your model's [data-schema.md](../../extraction-models/data-schema.md "mention").

In the client library, you'll have access to the various fields as a key-value mapping type (Python's `dict`, Java's `HashMap`, etc).

Accessing a field is done via its name in the Data Schema.

Each field will be one of the following types:

* A single value, `SimpleField` class.
* A nested object (sub-fields), `ObjectField` class.
* A list or array of fields, `ListField` class.

## `SimpleField` - Single-Value Field

Basic field type having the `value` attribute.\
See the [#value](process-result-fields.md#value "mention") section below.

In addition, the `Simplefield` class has [#confidence](process-result-fields.md#confidence "mention") and [#locations](process-result-fields.md#locations "mention") attributes.

{% tabs %}
{% tab title="Python" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```python
from mindee import InferenceResponse

def handle_response(response: InferenceResponse):
    fields: dict = response.inference.result.fields

    my_simple_field = fields["my_simple_field"]
```
{% endtab %}

{% tab title="Node.js" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```javascript
handleResponse(response) {
  const fields = response.inference.result.fields;

  const simpleField = fields.getSimpleField("my_simple_field");
}
```
{% endtab %}

{% tab title="PHP" %}
Using the `$response` deserialized object from either the polling response or a webhook payload.

```php
use Mindee\Parsing\V2\InferenceResponse;

public function handleResponse(InferenceResponse $response)
{
    $fields = $response->inference->result->fields;

    $simpleField = $fields->getSimpleField('my_simple_field');
}
```
{% endtab %}

{% tab title="Ruby" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```ruby
def handle_response(response)
  fields = response.inference.result.fields

  simple_field = fields.get_simple_field('my_simple_field')
end
```
{% endtab %}

{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.parsing.v2.InferenceResponse;
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
{% tab title="Python" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/python-process-simplefield.md" %}
{% endtab %}

{% tab title="Node.js" %}
The `value` attribute is an `Object` type under the hood.

You should use the explicitly-typed accessors, this is recommended for clarity.\
Take a look at your Data Schema to know which typed accessor to use.

{% include "../../.gitbook/includes/code-samples/javascript-process-simplefield.md" %}

If the wrong accessor type is used, an exception will be thrown, something like this:

```
"Value is not a number"
```
{% endtab %}

{% tab title="PHP" %}
Using the `$response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/php-process-simplefield.md" %}
{% endtab %}

{% tab title="Ruby" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/ruby-process-simplefield.md" %}
{% endtab %}

{% tab title="Java" %}
The `value` attribute is an `Object` type under the hood.

You'll need to explicitly declare the type, otherwise the code will likely not compile.\
Take a look at your Data Schema to know which type to declare.

{% include "../../.gitbook/includes/code-samples/java-process-simplefield.md" %}

If the wrong type method is used, an exception will be thrown, something like this:

```
ClassCast class java.lang.String cannot be cast to class java.lang.Double
```
{% endtab %}

{% tab title=".NET" %}
The `Value` attribute is a `dynamic` type under the hood.

You should explicitly declare the type, this is recommended for clarity.\
Take a look at your Data Schema to know which type to declare.

{% include "../../.gitbook/includes/code-samples/dotnet-process-simplefield.md" %}

If the wrong type is declared, an exception will be raised, something like this:

```
RuntimeBinderException : Cannot implicitly convert type 'string' to 'double'
```
{% endtab %}
{% endtabs %}

## `ObjectField` - Nested Object Field

Field having a `fields` attribute which is a hash table (Python's `dict`, Java's `HashMap`, etc) of sub-fields.\
See the [#fields](process-result-fields.md#fields "mention") section below.

In addition, the `ObjectField` class has [#confidence](process-result-fields.md#confidence "mention") and [#locations](process-result-fields.md#locations "mention") attributes.

{% tabs %}
{% tab title="Python" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```python
from mindee import InferenceResponse

def handle_response(response: InferenceResponse):
    fields: dict = response.inference.result.fields

    object_field = fields["my_object_field"]
```
{% endtab %}

{% tab title="Node.js" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```javascript
handleResponse(response) {
  const fields = response.inference.result.fields;

  const objectField = fields.getObjectField("my_object_field");
}
```
{% endtab %}

{% tab title="PHP" %}
Using the `$response` deserialized object from either the polling response or a webhook payload.

```php
use Mindee\Parsing\V2\InferenceResponse;

public function handleResponse(InferenceResponse $response)
{
    $fields = $response->inference->result->fields;

    $objectField = $fields->getObjectField('my_object_field');
}
```
{% endtab %}

{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.parsing.v2.InferenceResponse;
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

The sub-fields as a key-value mapping type (Python `dict`, Java `HashMap`, etc).

Accessing a sub-field is done via its name in the Data Schema.

Each sub-field will be a [#single-value-field-simplefield](process-result-fields.md#single-value-field-simplefield "mention").

{% tabs %}
{% tab title="Python" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/python-process-objectfield.md" %}
{% endtab %}

{% tab title="Node.js" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/javascript-process-objectfield.md" %}
{% endtab %}

{% tab title="PHP" %}
Using the `$response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/php-process-objectfield.md" %}
{% endtab %}

{% tab title="Ruby" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/ruby-process-objectfield.md" %}
{% endtab %}

{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/java-process-objectfield.md" %}
{% endtab %}

{% tab title=".NET" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/dotnet-process-objectfield.md" %}
{% endtab %}
{% endtabs %}

## `ListField` - List of Fields

Field having an `items` attribute which is a list of fields.\
See the [#items](process-result-fields.md#items "mention") section below.

In addition, the `ListField` class has a [#confidence](process-result-fields.md#confidence "mention") attribute.

{% tabs %}
{% tab title="Python" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```python
from mindee import InferenceResponse

def handle_response(response: InferenceResponse):
    fields: dict = response.inference.result.fields

    my_list_field = fields["my_list_field"]
```
{% endtab %}

{% tab title="Node.js" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```javascript
handleResponse(response) {
  const fields = response.inference.result.fields;

  const listField = fields.getListField("my_list_field");
}
```
{% endtab %}

{% tab title="PHP" %}
Using the `$response` deserialized object from either the polling response or a webhook payload.

```php
use Mindee\Parsing\V2\InferenceResponse;

public function handleResponse(InferenceResponse $response)
{
    $fields = $response->inference->result->fields;
    
    $listField = $fields->getListField('my_list_field');
}
```
{% endtab %}

{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.parsing.v2.InferenceResponse;
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

List of fields as a variable-length array type (Python `list`, JavaScript `Array`, Java `List`, etc).

Each item in the list will be one of:

* [#simplefield-single-value-field](process-result-fields.md#simplefield-single-value-field "mention")
* [#objectfield-nested-object-field](process-result-fields.md#objectfield-nested-object-field "mention")

There will **not** be a mix of both types in the same list.

#### List of `SimpleField`

{% tabs %}
{% tab title="Python" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/python-process-listfield-simplefield.md" %}
{% endtab %}

{% tab title="Node.js" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/javascript-process-listfield-simplefield.md" %}
{% endtab %}

{% tab title="PHP" %}
Using the `$response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/php-process-listfield-simplefield.md" %}
{% endtab %}

{% tab title="Ruby" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/ruby-process-listfield-simplefield.md" %}
{% endtab %}

{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/java-process-listfield-simplefield.md" %}
{% endtab %}

{% tab title=".NET" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/dotnet-process-listfield-simplefield.md" %}
{% endtab %}
{% endtabs %}

#### List of `ObjectField`

{% tabs %}
{% tab title="Python" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/python-process-listfield-objectfield.md" %}
{% endtab %}

{% tab title="Node.js" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/javascript-process-listfield-objectfield.md" %}
{% endtab %}

{% tab title="PHP" %}
Using the `$response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/php-process-listfield-objectfield.md" %}
{% endtab %}

{% tab title="Ruby" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/ruby-process-listfield-objectfield.md" %}
{% endtab %}

{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/java-process-listfield-objectfield.md" %}
{% endtab %}

{% tab title=".NET" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

{% include "../../.gitbook/includes/code-samples/dotnet-process-listfield-objectfield.md" %}
{% endtab %}
{% endtabs %}

## Optional Field Attributes

These field attributes are only filled when their respective features are activated.

The attributes are always present even when not activated.

### `confidence`

The confidence level of the extracted value.

The data are only filled if the [automation-confidence-score.md](../../extraction-models/optional-features/automation-confidence-score.md "mention") feature is activated.

The attribute is always present, in case of Confidence Score not activated, it will always be null.

The attribute value will be one of: `Certain`, `High`, `Medium`, `Low` .

All languages use the appropriate enum type.

{% tabs %}
{% tab title="Python" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```python
from mindee import InferenceResponse
from mindee.parsing.v2.field import FieldConfidence

def handle_response(response: InferenceResponse):
    fields: dict = response.inference.result.fields

    confidence = fields["my_simple_field"].confidence

    # compare using the enum `FieldConfidence`
    is_certain = confidence == FieldConfidence.CERTAIN
    is_lte_medium = confidence <= FieldConfidence.MEDIUM
    is_gte_low = confidence >= FieldConfidence.LOW
```
{% endtab %}

{% tab title="Node.js" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```javascript
handleResponse(response) {
  const fields = response.inference.result.fields;

  const confidence = fields.getSimpleField("my_simple_field")?.confidence

  // compare using the enum `FieldConfidence`
  const isCertain = confidence === FieldConfidence.Certain;
  const isLteMedium = FieldConfidence.lessThanOrEqual(
    confidence, FieldConfidence.Medium
  );
  const isGteLow = FieldConfidence.greaterThanOrEqual(
    confidence, FieldConfidence.Low
  );
}
```
{% endtab %}

{% tab title="PHP" %}
Using the `$response` deserialized object from either the polling response or a webhook payload.

```php
use Mindee\Parsing\V2\InferenceResponse;
use Mindee\Parsing\V2\Field\FieldConfidence;

public function handleResponse(InferenceResponse $response)
{
    $fields = $response->inference->result->fields;

    $confidence = $fields->get('my_simple_field')->confidence;

    // compare using the enum `FieldConfidence`
    $isCertain = $confidence === FieldConfidence::Certain;
    $isLteMedium = $confidence->lessThanOrEqual(FieldConfidence::Medium);
    $isGteLow = $confidence->greaterThanOrEqual(FieldConfidence::Low);
}
```
{% endtab %}

{% tab title="Ruby" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```ruby
def handle_response(response)
  fields = response.inference.result.fields

  confidence = fields["my_simple_field"].confidence

  # compare using the class `FieldConfidence`
  FieldConfidence = Mindee::Parsing::V2::Field::FieldConfidence
  
  is_certain = confidence == FieldConfidence.CERTAIN
  is_lte_medium = confidence <= FieldConfidence.MEDIUM
  is_gte_low = confidence >= FieldConfidence.LOW
end
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
  boolean isCertain = confidence === FieldConfidence.Certain;
  boolean isLteMedium = confidence.lessThanOrEqual(FieldConfidence.Medium);
  boolean isGteLow = confidence.greaterThanOrEqual(FieldConfidence.Low);
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
    // cast to int for relative inequalities
    bool isLteMedium = (int?)confidence <= (int)FieldConfidence.Medium;
    bool isGteLow = (int?)confidence >= (int)FieldConfidence.Low;
}
```
{% endtab %}
{% endtabs %}

### `locations`

A list of the field's locations on the document.

The data are only filled if the [polygons-bounding-boxes.md](../../extraction-models/optional-features/polygons-bounding-boxes.md "mention") feature is activated.

It's possible for a single field to have multiple locations, for example when an invoice item spans two pages.

Each location has a page index and a Polygon.

Page indexes are 0-based, so the first page is `0`.

A Polygon class contains a list of Points, the specific implementation will depend on the language.

Points are listed in clockwise order, where index `0` is top left.

Point X,Y coordinates are normalized floats from 0.0 to 1.0, relative to the page dimensions.

{% tabs %}
{% tab title="Python" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```python
from mindee import InferenceResponse

def handle_response(response: InferenceResponse):
    fields: dict = response.inference.result.fields
    
    locations = fields["my_simple_field"].locations

    # accessing the polygon
    polygon = locations[0].polygon

    # accessing points: the Polygon class extends List[Point]
    top_x = polygon[0].x

    # alternative syntax, since the Point class extends List<float>
    # top_x = polygon[0][0]

    # there are geometry functions available in the Polygon class
    center = polygon.centroid

    # accessing the page index on which the polygon is
    page_index = locations[0].page
```
{% endtab %}

{% tab title="Node.js" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```javascript
handleResponse(response) {
  const fields = response.inference.result.fields;

  const locations = fields.getSimpleField("my_simple_field")?.locations;

  // accessing the polygon
  const polygon = locations![0].polygon!;

  // accessing points: the Polygon class extends Array<Point>
  const topX = polygon[0][0];

  // there are geometry functions available in the Polygon class
  const center = polygon.getCentroid();

  // accessing the page index on which the polygon is
  const pageIndex = locations![0].page!;
}
```
{% endtab %}

{% tab title="PHP" %}
Using the `$response` deserialized object from either the polling response or a webhook payload.

```php
use Mindee\Parsing\V2\InferenceResponse;
use Mindee\Parsing\V2\Field\FieldConfidence;

public function handleResponse(InferenceResponse $response)
{
    $fields = $response->inference->result->fields;

    $locations = $fields->get('my_simple_field')->locations;

    // accessing the polygon
    $polygon = $locations[0]->polygon;
    
    // accessing points:
    $points = $polygon->coordinates;
    $topX = $points[0]->getX();
    // alternative syntax, since the Point class extends Array<float>
    // $topX = $points[0][0]

    // there are geometry functions available in the Polygon class
    $center = $polygon->getCentroid();
    
    // accessing the page index on which the polygon is
    $pageIndex = $locations[0]->page;
}
```
{% endtab %}

{% tab title="Ruby" %}
Using the `$response` deserialized object from either the polling response or a webhook payload.

```ruby
def handle_response(response)
  fields = response.inference.result.fields

  locations = fields.get_simple_field('my_simple_field').locations

  # accessing the polygon
  polygon = locations[0].polygon

  # accessing points:
  top_x = polygon[0].x
  # alternative syntax
  # top_x = polygon[0][0]

  # there are geometry functions available in the Polygon class
  center = polygon.centroid

  # accessing the page index on which the polygon is
  page_index = locations[0].page
end
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
