---
description: >-
  Reference documentation on processing a Classification result using the Mindee
  SDKs.
icon: brain-circuit
---

# Classification Result

{% include "../../.gitbook/includes/this-is-reference-documenta....md" %}

{% include "../../.gitbook/includes/result-response-requirements.md" %}

## Accessing the Classification

A `Classifier` describes the detected class of the entire document.

### `Classifier` Attributes

#### Document Type

The document category assigned to the sub-document. It is always filled.

It is returned as a string and is identical to the value entered on the Mindee platform — case, spaces, and punctuation included.

#### Extraction Response

Optional extraction response associated with the split. This is only filled if extraction chaining is activated for the model.

{% tabs %}
{% tab title="Python" %}
```python
from mindee import ClassificationResponse

def handle_response(response: ClassificationResponse):
    classifier = response.inference.result.classification
```
{% endtab %}

{% tab title="Node.js" %}
```javascript
handleResponse(response) {
  const classification = response.inference.result.classification;
}
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mindee\V2\Product\Classification\ClassificationResponse;

public function handleResponse(SplitResponse $response)
{
    $classification = $response->inference->result->classification;
}
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
def handle_response(response)
  classification = response.inference.result.classification
end
```
{% endtab %}

{% tab title="Java" %}
```java
import com.mindee.v2.product.classification.ClassificationResponse;

public void handleResponse(ClassificationResponse response) {
  var classification = response.getInference().getResult().getClassification();
  
  // Document type identified for this file
  String documentType = crop.getDocumentType();
  System.out.println("Detected type: " + documentType);

  // Optional extraction response, present if extraction chaining was requested
  var extractionResponse = crop.getExtractionResponse();

  if (extractionResponse != null) {
    // Access extracted fields from the split's inference result
    var fields = extractionResponse.getInference().getResult().getFields();
    System.out.println("Extraction fields: " + fields.toString());
  }
}
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using Mindee.V2.Product.Classification;

public void HandleResponse(ClassificationResponse response)
{
    var classification = response.Inference.Result.Classification;
}
```
{% endtab %}
{% endtabs %}

{% include "../../.gitbook/includes/access-chained-extraction.md" %}
