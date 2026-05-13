---
description: Reference documentation on processing a Crop result using the Mindee SDKs.
icon: brain-circuit
---

# Crop Result

{% include "../../.gitbook/includes/this-is-reference-documenta....md" %}

{% include "../../.gitbook/includes/result-response-requirements.md" %}

## Accessing Crop Items

{% tabs %}
{% tab title="Python" %}
```python
from mindee import CropResponse

def handle_response(response: CropResponse):
    crops: list = response.inference.result.crops
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
