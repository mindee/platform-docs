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

search_params = ModelSearchParameters(
    # Filter models by partial name match, case-insensitive.
    name="invoice",
    # Filter by an exact model type.
    model_type="extraction",
)

response = client.search(search_params)

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

const searchParams = {
  // Filter models by partial name match, case-insensitive.
  name: "invoice",
  // Filter by an exact model type.
  modelType: "extraction"
};

const response = await client.search(ModelSearch, searchParams);

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

$searchParams = new ModelSearchParameters(
    // Filter models by partial name match, case-insensitive.
    name: "invoice",
    // Filter by an exact model type.
    modelType: "extraction",
);

$response = $client->search($searchParams);

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

search_params = Mindee::V2::Search::Models::ModelSearchParameters.new(
    # Filter models by partial name match, case-insensitive.
    name: 'invoice',
    # Filter by an exact model type.
    model_type: 'extraction',
)

response = client.search(search_params)

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

var searchParams = new ModelSearchParameters.builder()
    // Filter models by partial name match, case-insensitive.
    .name("invoice")
    // Filter by an exact model type.
    .modelType("extraction")
    .build();

var response = client.search(searchParams);

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

var searchParams = new ModelSearchParameters(
    // Filter models by partial name match, case-insensitive.
    name: 'invoice',
    // Filter by an exact model type.
    modelType: 'extraction'
);

var response = await client.SearchAsync(searchParams);

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

## Search RAG Documents

Search for RAG documents within the organization linked to the API key.

The model ID is required, search filters are optional. If no search filters are given, all documents linked to the model are returned.

{% tabs %}
{% tab title="Python" %}
```python
from mindee.v2.search.rag_documents.rag_document_search_parameters import (
    RagDocumentSearchParameters,
)

search_params = RagDocumentSearchParameters(
    # The exact Model UUID the document is linked to.
    model_id="my-model-uuid",
    # Filter documents by partial filename match, case-insensitive.
    filename="invoice_32GB-RAM_450k-USD.pdf",
)

response = client.search(search_params)

# print a pretty representation of the response, useful for development
print(str(response))

# access RAG document information
for rag_doc in response.rag_documents:
    rag_doc_id = rag_doc.id
    rag_doc_total_matches = rag_doc.total_matches
```
{% endtab %}

{% tab title="Node.js" %}
```typescript
import { RagDocumentSearch } from "@/v2/search/index.js";

const searchParams = {
  // The exact Model UUID the document is linked to.
  modelId: "my-model-uuid",
  // Filter documents by partial filename match, case-insensitive.
  filename: "invoice_32GB-RAM_450k-USD.pdf"
};

const response = await client.search(RagDocumentSearch, searchParams);

// print a pretty representation of the response, useful for development
console.log(response.toString());

// access RAG document information
for (const ragDoc of response.ragDocuments) {
  const ragDocId = ragDoc.id;
  const ragDocTotalMatches = ragDoc.totalMatches;
}
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mindee\V2\Search\RagDocuments\RagDocumentSearchParameters;

$searchParams = new RagDocumentSearchParameters(
    // The exact Model UUID the document is linked to.
    modelId: "my-model-uuid",
    // Filter documents by partial filename match, case-insensitive.
    filename: "invoice_32GB-RAM_450k-USD.pdf",
);

$response = $client->search($searchParams);

// Print a pretty representation of the response, useful for development
print_r($response);

// Access RAG document information
foreach ($response->ragDocuments as $ragDoc) {
    $ragDocId = $ragDoc->id;
    $ragDocTotalMatches = $ragDoc->totalMatches;
}
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'mindee'

search_params = Mindee::V2::Search::RagDocuments::RagDocumentSearchParameters.new(
  # The exact Model UUID the document is linked to.
  model_id: 'my-model-uuid',
  # Filter documents by partial filename match, case-insensitive.
  filename: 'invoice_32GB-RAM_450k-USD.pdf',
)

response = client.search(search_params)

# print a pretty representation of the response, useful for development
puts response.to_s

# access RAG document information
response.rag_documents.each do |rag_doc|
  rag_doc_id = rag_doc.id
  rag_doc_total_matches = rag_doc.total_matches
end
```
{% endtab %}

{% tab title="Java" %}
```java
import com.mindee.v2.search.ragdocuments.RagDocumentSearchParameters;

var searchParams = new RagDocumentSearchParameters.builder()
        // The exact Model UUID the document is linked to.
        .modelId("my-model-uuid")
        // Filter documents by partial filename match, case-insensitive.
        .filename("invoice_32GB-RAM_450k-USD.pdf")
        .build();

var response = client.search(searchParams);

// print a pretty representation of the response, useful for development
System.out.println(response.toString());

// access RAG document information
for (var ragDoc : response.getRagDocuments()) {
    String ragDocId = ragDoc.getId();
    int ragDocTotalMatches = ragDoc.getTotalMatches();
}
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using Mindee.V2.Search.RagDocuments;

var searchParams = new RagDocumentSearchParameters(
    // The exact Model UUID the document is linked to.
    modelId: "my-model-uuid",
    // Filter documents by partial filename match, case-insensitive.
    filename: "invoice_32GB-RAM_450k-USD.pdf"
);

var response = await client.SearchAsync(searchParams);

// print a pretty representation of the response, useful for development
Console.WriteLine(response.ToString());

// access RAG document information
foreach (var ragDoc in response.RagDocuments)
{
    string ragDocId = ragDoc.Id;
    int ragDocTotalMatches = ragDoc.TotalMatches;
}
```
{% endtab %}
{% endtabs %}
