---
description: Reference documentation on processing a Split result using the Mindee SDKs.
icon: brain-circuit
---

# Split Result

{% include "../../.gitbook/includes/this-is-reference-documenta....md" %}

{% include "../../.gitbook/includes/result-response-requirements.md" %}

## Accessing Split Ranges

A `SplitRange` describes one logical sub-document identified within the source file.

### `SplitRange` Attributes

Each `SplitRange` instance will have these properties.

#### Document Type

The document category assigned to the sub-document. It is always filled.

It is returned as a string and is identical to the value entered on the Mindee platform — case, spaces, and punctuation included.

#### Page Range

A two-element array of **0-based** page indexes, where the first integer indicates the start page and the second integer indicates the end page. It is always filled.

A page range value of `(0,2)` would mean from the **first** page to the **third** page.

#### Extraction Response

Optional extraction response associated with the split. This is only filled if extraction chaining is activated for the model.

### Iterate Over Split Ranges

You'll usually want to iterate over all split ranges, since the number of ranges is dependent on the document.

{% tabs %}
{% tab title="Python" %}
```python
from mindee import SplitResponse

def handle_response(response: SplitResponse):
    splits: list = response.inference.result.splits

    for split in splits:
        # 0-based [start_page, end_page] range
        page_range = split.page_range

        # Document type identified for this split
        document_type = split.document_type
```
{% endtab %}

{% tab title="Node.js" %}
```javascript
handleResponse(response) {
  const splits = response.inference.result.splits;

  for (const split of splits) {
    // 0-based [startPage, endPage] range
    const pageRange = split.pageRange;

    // Document type identified for this split
    const documentType = split.documentType;

    console.log(`Document Type: ${documentType}`);
    console.log(`Page Range: ${pageRange[0]} - ${pageRange[1]}`);
    
    // Optional extraction response, present if extraction chaining was requested
    const extractionResponse = split.extractionResponse;

    if (extractionResponse) {
      // Access extracted fields from the split's inference result
      const fields = extractionResponse.inference.result.fields;
      console.log("Extraction fields:", fields.toString());
    }
  }
}
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mindee\V2\Product\Split\SplitResponse;

public function handleResponse(SplitResponse $response)
{
    $splits = $response->inference->result->splits;
}
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
def handle_response(response)
  splits = response.inference.result.splits

  splits.each do |split|
    # 0-based [start_page, end_page] range
    page_range = split.page_range

    # Document type identified for this split
    document_type = split.document_type

    puts "Document Type: #{document_type}"
    puts "Page Range: #{page_range[0]} - #{page_range[1]}"

    # Optional extraction response, present if extraction chaining was requested
    extraction_response = split.extraction_response

    if extraction_response
      # Access extracted fields from the split's inference result
      fields = extraction_response.inference.result.fields
      puts "Extraction fields: #{fields}"
    end
  end
```
{% endtab %}

{% tab title="Java" %}
```java
import com.mindee.v2.product.split.SplitResponse;

public void handleResponse(SplitResponse response) {
  var splits = response.getInference().getResult().getSplits();
}
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using Mindee.V2.Product.Split;

public void HandleResponse(SplitResponse response)
{
    var splits = response.Inference.Result.Splits;
}
```
{% endtab %}
{% endtabs %}

{% include "../../.gitbook/includes/access-chained-extraction.md" %}
