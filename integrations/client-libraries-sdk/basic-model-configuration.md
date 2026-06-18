---
description: >-
  Reference documentation on preparing and configuring the Mindee model
  inference.
icon: wrench-simple
---

# Basic Model Configuration

{% include "../../.gitbook/includes/this-is-reference-documenta....md" %}

Parameters that apply to all Mindee model types (Extraction, Split, Crop, etc).

Inference parameters control:

* which model to use
* server-side processing options

All model parameter classes inherit from a base class. In these samples we will be showing the general usage and parameters common to all.

All examples use the Extraction model (product in the SDK), but you'll need to adjust depending on the model type you are using.

The available classes are:

* `ExtractionParameters`  for [Extraction](https://app.gitbook.com/s/u5bStlX8nv4b9z4GXB2S/extraction-models) models
* `SplitParameters`  for [Split](https://app.gitbook.com/s/u5bStlX8nv4b9z4GXB2S/split-models) models
* `CropParameters`  for [Crop](https://app.gitbook.com/s/u5bStlX8nv4b9z4GXB2S/crop-models) models
* `ClassificationParameters`  for [Classification](https://app.gitbook.com/s/u5bStlX8nv4b9z4GXB2S/classification-models) models
* `OCRParameters`  or `OcrParameters`  for [Raw Text OCR](https://app.gitbook.com/s/u5bStlX8nv4b9z4GXB2S/ocr-models) models

### Use an Alias

The optional `alias` argument lets you attach your own identifier to a request as a free-form string.

This alias could be an internal document ID, a reference number, or a database key.

It is echoed back unchanged in both the job and result responses, making it straightforward to match API responses with your own records.

Aliases are not unique in Mindee, you can use the same alias value multiple times.

{% tabs %}
{% tab title="Python" %}
```python
inference_params = ExtractionParameters(
    # ID of the model, required.
    model_id="MY_MODEL_ID",
    
    # Use an alias to link the file to your own DB.
    # If set, it will be included in the job and result responses.
    alias="internal-doc-id-123",
    
    # ... any other options ...
)
```
{% endtab %}

{% tab title="Node.js" %}
```typescript
const modelParams = {
  // ID of the model, required.
  modelId: "MY_MODEL_ID",
  
  // Use an alias to link the file to your own DB.
  // If set, it will be included in the job and result responses.
  alias: "internal-doc-id-123",
  
  // ... any other options ...
};
```
{% endtab %}

{% tab title="PHP" %}
```php
$modelParams = new ExtractionParameters(
    // ID of the model, required.
    "MY_MODEL_ID",

    // Use an alias to link the file to your own DB.
    // If set, it will be included in the job and result responses.
    alias: "internal-doc-id-123",
    
    // ... any other options ...
);
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
inference_params = {
    # ID of the model, required.
    model_id: 'MY_MODEL_ID',
    
    # Use an alias to link the file to your own DB.
    # If set, it will be included in the job and result responses.
    file_alias: 'internal-doc-id-123',
    
    # ... any other options ...
}
```
{% endtab %}

{% tab title="Java" %}
```java
var modelParams = ExtractionParameters
    // ID of the model, required.
    .builder("MY_MODEL_ID")
    
    // Use an alias to link the file to your own DB.
    // If set, it will be included in the job and result responses.
    .alias("internal-doc-id-123")
    
    // ... any other options ...

    // complete the builder
    .build();
```
{% endtab %}

{% tab title=".NET" %}
```csharp
var modelParams = new ExtractionParameters(
    // ID of the model, required.
    modelId: "MY_MODEL_ID"

    // Use an alias to link the file to your own DB.
    // If set, it will be included in the job and result responses.
    , alias: "internal-doc-id-123"
    
    // ... any other options ...
);
```
{% endtab %}
{% endtabs %}
