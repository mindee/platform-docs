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

{% tabs %}
{% tab title="Python" %}
```python
from mindee import ClassificationResponse

def handle_response(response: ClassificationResponse):
    classification = response.inference.result.classification
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
import com.mindee.v2.product.classification.ClassificationClassifier;

public void handleResponse(SplitResponse response) {
  var classification = response.getInference().getResult().getClassification();
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
