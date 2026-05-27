---
description: Reference documentation on processing a Crop result using the Mindee SDKs.
icon: brain-circuit
---

# Crop Result

{% include "../../.gitbook/includes/this-is-reference-documenta....md" %}

{% include "../../.gitbook/includes/result-response-requirements.md" %}

## Accessing Crop Items

A `CropItem` describes the location of a single detected object.

In this context, an _object_ can be any element to find on a page.

Most users will look for a document type (like a receipt or an ID), but it could really be anything (a photo, a logo, etc).&#x20;

### `CropItem` Attributes

#### Object Type

The category assigned to the object. It is always filled.

It is returned as a string and is identical to the value entered on the Mindee platform — case, spaces, and punctuation included.

Why "Object Type" instead of "Document Type", like for Split and Classification? Because the fundamental technology is different, Crop uses Object Detection algorithms, whereas Split and Classification use variations of classification technology.

#### Location

The location of the object in the document. It contains the following properties:

* Polygon: Coordinates of the object.
* Page: 0-based index of the page the coordinates were found on.

#### Extraction Response

Optional extraction response associated with the split. This is only filled if extraction chaining is activated for the model.

### Iterate Over Crop Items

You'll usually want to iterate over all crop items, since the number of items is dependent on the document. Remember that a document can have multiple pages, and each of its pages can have multiple crop items.

{% tabs %}
{% tab title="Python" %}
```python
from mindee import CropResponse

def handle_response(response: CropResponse):
    crops = response.inference.result.crops
```
{% endtab %}

{% tab title="Node.js" %}
```javascript
handleResponse(response) {
  const crops = response.inference.result.crops;
}
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mindee\V2\Product\Split\CropResponse;

public function handleResponse(CropResponse $response)
{
    $crops = $response->inference->result->crops;
}
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
def handle_response(response)
  crops = response.inference.result.crops
end
```
{% endtab %}

{% tab title="Java" %}
```java
import com.mindee.v2.product.crop.CropResponse;

public void handleResponse(CropResponse response) {
  var crops = response.getInference().getResult().getCrops();
  
  for (var crop : crops) {
    // Object type identified for this crop
    String objectType = crop.getObjectType();
    System.out.println("Detected type: " + objectType);

    // location of the crop
    var location = crop.getLocation();

    // 0-based page index
    var page = location.getPage();

    // polygon object, which includes some useful methods
    var polygon = location.getPolygon();
    var center = polygon.getCentroid();

    System.out.println("On page " + page + ", with center at " + center);

    // Optional extraction response, present if extraction chaining was requested
    var extractionResponse = crop.getExtractionResponse();

    if (extractionResponse != null) {
      // Access extracted fields from the split's inference result
      var fields = extractionResponse.getInference().getResult().getFields();
      System.out.println("Extraction fields: " + fields.toString());
    }
  }
}
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using Mindee.V2.Product.Crop;

public void HandleResponse(CropResponse response)
{
    var crops = response.Inference.Result.Crops;
}
```
{% endtab %}
{% endtabs %}

{% include "../../.gitbook/includes/access-chained-extraction.md" %}
