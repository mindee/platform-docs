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

def handle_response(response: CropResponse) -> None:
    crops = response.inference.result.crops

    for crop in crops:
        # Object type identified for this crop
        object_type = crop.object_type
        print(f"Detected type: {object_type}")

        # Location of the crop
        location = crop.location

        # 0-based page index
        page = location.page

        # Polygon object, which includes some useful methods
        polygon = location.polygon
        center = polygon.centroid

        print(f"On page {page}, with center at {center}")

        # Optional extraction response, present if extraction chaining was requested
        extraction_response = crop.extraction_response

        if extraction_response is not None:
            # Access extracted fields from the crop's inference result
            fields = extraction_response.inference.result.fields
            print(f"Extraction fields: {fields}")
```
{% endtab %}

{% tab title="Node.js" %}
```javascript
function handleResponse(response): void {
  const crops = response.inference.result.crops;

  for (const crop of crops) {
    // Object type identified for this crop
    const objectType = crop.objectType;
    console.log(`Detected type: ${objectType}`);

    // Location of the crop
    const location = crop.location;

    // 0-based page index
    const page = location.page;

    // Polygon object, which includes some useful methods
    const polygon = location.polygon;
    const center = polygon.getCentroid();

    console.log(`On page ${page}, with center at ${center}`);

    // Optional extraction response, present if extraction chaining was requested
    const extractionResponse = crop.extractionResponse;

    if (extractionResponse !== undefined) {
      // Access extracted fields from the crop's inference result
      const fields = extractionResponse.inference.result.fields;
      console.log(`Extraction fields: ${fields}`);
    }
  }
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

  crops.each do |crop|
    # Object type identified for this crop
    object_type = crop.object_type
    puts "Detected type: #{object_type}"

    # Location of the crop
    location = crop.location

    # 0-based page index
    page = location.page

    # Polygon object, which includes some useful methods
    polygon = location.polygon
    center = polygon.centroid

    puts "On page #{page}, with center at #{center}"

    # Optional extraction response, present if extraction chaining was requested
    extraction_response = crop.extraction_response

    unless extraction_response.nil?
      # Access extracted fields from the split's inference result
      fields = extraction_response.inference.result.fields
      puts "Extraction fields: #{fields}"
    end
  end
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

    foreach (var crop in crops)
    {
        // Object type identified for this crop
        string objectType = crop.ObjectType;
        Console.WriteLine($"Detected type: {objectType}");

        // Location of the crop
        var location = crop.Location;

        // 0-based page index
        var page = location.Page;

        // Polygon object, which includes some useful methods
        var polygon = location.Polygon;
        var center = polygon.GetCentroid();

        Console.WriteLine($"On page {page}, with center at {center}");

        // Optional extraction response, present if extraction chaining was requested
        var extractionResponse = crop.ExtractionResponse;

        if (extractionResponse != null)
        {
            // Access extracted fields from the crop's inference result
            var fields = extractionResponse.Inference.Result.Fields;
            Console.WriteLine($"Extraction fields: {fields}");
        }
    }
}
```
{% endtab %}
{% endtabs %}

{% include "../../.gitbook/includes/access-chained-extraction.md" %}
