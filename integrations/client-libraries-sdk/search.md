---
description: Search for resources linked to your organization.
icon: magnifying-glass
---

# Search

Use the generic `search` method in the client to find various resources belonging to your organization.

## Before Starting

You'll need an instance of the [Mindee V2 Client](configure-the-client.md) in order to make search requests.

## Search Models

Search for models within the organization linked to the API key.

All search filters are optional. If no search filters are given, all models belonging to the organization are returned.

{% tabs %}
{% tab title="Python" %}
```python
from mindee.v2.search.models.model_search_response import ModelSearchResponse

model_search_params = ModelSearchParameters(
    # Filter models by partial name match, case-insensitive.
    name="invoice",
    # Filter by an exact model type.
    model_type="extraction",
)

response = client.search(model_search_params)

# print a pretty representation of the response, useful for development
print(str(response))

# access model information
for model in response.models:
    model_id = model.id
```
{% endtab %}

{% tab title="Node.js" %}
```typescript
import { ModelSearch } from "@/v2/search/index.js";

const modelSearchParams = {
  // Filter models by partial name match, case-insensitive.
  name: "invoice",
  // Filter by an exact model type.
  modelType: "extraction"
};

const response = await client.search(ModelSearch, modelSearchParams);

// print a pretty representation of the response, useful for development
console.log(response.toString());

// access model information
for (const model of response.models) {
  const modelId = model.id;
}
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mindee\V2\Search\Models\ModelSearchParameters;
use Mindee\V2\Search\Models\ModelSearchResponse;

$modelSearchParams = new ModelSearchParameters(
    // Filter models by partial name match, case-insensitive.
    name: "invoice",
    // Filter by an exact model type.
    modelType: "extraction",
);

$response = $client->search($modelSearchParams);

// Print a pretty representation of the response, useful for development
print_r($response);

// Access model information
foreach ($response->models as $model) {
    $modelId = $model->id;
}
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'mindee'

model_search_params = Mindee::V2::Search::Models::ModelSearchParameters.new(
    # Filter models by partial name match, case-insensitive.
    name: 'invoice',
    # Filter by an exact model type.
    model_type: 'extraction',
)

response = client.search(model_search_params)

# print a pretty representation of the response, useful for development
puts response.to_s

# access model information
response.models.each do |model|
  model_id = model.id
end
```
{% endtab %}

{% tab title="Java" %}
```java
import com.mindee.v2.search.models.ModelSearchParameters;

var modelSearchParams = new ModelSearchParameters.builder()
    // Filter models by partial name match, case-insensitive.
    .name("invoice")
    // Filter by an exact model type.
    .modelType("extraction")
    .build();

var response = client.search(modelSearchParams);

// print a pretty representation of the response, useful for development
System.out.println(response.toString());

// access model information
for (var model : response.getModels()) {
    String modelId = model.getId();
}
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using Mindee.V2.Search.Models;

var modelSearchParams = new ModelSearchParameters(
    // Filter models by partial name match, case-insensitive.
    name: 'invoice',
    // Filter by an exact model type.
    modelType: 'extraction'
);

var response = await client.SearchAsync(modelSearchParams);

// print a pretty representation of the response, useful for development
Console.WriteLine(response.ToString());

// access model information
foreach (var model in response.Models)
{
    string modelId = model.Id;
}
```
{% endtab %}
{% endtabs %}
