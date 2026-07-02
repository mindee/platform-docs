---
description: Reference documentation on processing a Split result using the Mindee SDKs.
icon: brain-circuit
---

# Split Result

{% include "../../.gitbook/includes/result-response-requirements.md" %}

## Access Split Ranges

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

def handle_response(response: SplitResponse) -> None:
    splits = response.inference.result.splits

    for split in splits:
        # 0-based [start_page, end_page] range
        page_range = split.page_range

        print(f"Detected type: {split.document_type}")
        print(f"On pages: {page_range[0]} - {page_range[1]}")

        # Optional extraction response, present if extraction chaining was requested
        extraction_response = split.extraction_response

        if extraction_response is not None:
            # Access extracted fields from the split's inference result
            fields = extraction_response.inference.result.fields
            print(f"Extraction fields: {fields}")
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

    console.log(`Detected type: ${documentType}`);
    console.log(`On pages: ${pageRange[0]} - ${pageRange[1]}`);
    
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

    foreach ($splits as $split) {
        // 0-based [startPage, endPage] range
        $pageRange = $split->pageRange;

        // Document type identified for this split
        $documentType = $split->documentType;

        echo "Detected type: $documentType\n";
        echo "On pages: {$pageRange[0]} - {$pageRange[1]}\n";

        // Optional extraction response, present if extraction chaining was requested
        $extractionResponse = $split->extractionResponse;

        if ($extractionResponse !== null) {
            // Access extracted fields from the split's inference result
            $fields = $extractionResponse->inference->result->fields;
            echo "Extraction fields: " . $fields->toString() . "\n";
        }
    }
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

    puts "Detected type: #{document_type}"
    puts "On pages: #{page_range[0]} - #{page_range[1]}"

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
import com.mindee.v2.product.split.SplitRange;

public void handleResponse(SplitResponse response) {
  var splits = response.getInference().getResult().getSplits();

  for (SplitRange split : splits) {
    // 0-based [startPage, endPage] range
    var pageRange = split.getPageRange();

    // Document type identified for this split
    String documentType = split.getDocumentType();

    System.out.println("Detected type: " + documentType);
    System.out.println(
      "On pages: " + pageRange.get(0) + " - " + pageRange.get(1)
    );

    // Optional extraction response, present if extraction chaining was requested
    var extractionResponse = split.getExtractionResponse();

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
using System;
using Mindee.V2.Product.Split;

public void HandleResponse(SplitResponse response)
{
    var splits = response.Inference.Result.Splits;

    foreach (SplitRange split in splits)
    {
        // 0-based [startPage, endPage] range
        var pageRange = split.PageRange;

        // Document type identified for this split
        string documentType = split.DocumentType;

        Console.WriteLine($"Detected type: {documentType}");
        Console.WriteLine($"On pages: {pageRange[0]} - {pageRange[1]}");

        // Optional extraction response, present if extraction chaining was requested
        var extractionResponse = split.ExtractionResponse;

        if (extractionResponse != null)
        {
            // Access extracted fields from the split's inference result
            var fields = extractionResponse.Inference.Result.Fields;
            Console.WriteLine($"Extraction fields: {fields}");
        }
    }
}
```
{% endtab %}
{% endtabs %}

{% include "../../.gitbook/includes/access-chained-extraction.md" %}

## Extract Split Ranges From the Input File

The SDKs provide support for extracting each split range as separate PDF files.

{% tabs %}
{% tab title="Python" %}
```python
from mindee import SplitResponse

def handle_response(response: SplitResponse, input_source) -> None:
    splits = response.inference.result.splits

    for split in splits:
      extracted_split = split.extract_from_input_source(input_source)

```
{% endtab %}

{% tab title="Node.js" %}
<pre class="language-javascript"><code class="lang-javascript"><strong>async handleResponse(response, inputSource) {
</strong>  const splits = response.inference.result.splits;

  for (const split of splits) {
    const extractedSplit = await split.extractFromInputSource(inputSource);
  }
}
</code></pre>
{% endtab %}

{% tab title="PHP" %}
```php
use Mindee\V2\Product\Split\SplitResponse;

public function handleResponse(SplitResponse $response, $inputSource)
{
    $splits = $response->inference->result->splits;

    foreach ($splits as $split) {
        $extractedSplit = $split->extractFromInputSource($inputSource)
    }
}
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
def handle_response(response)
  splits = response.inference.result.splits

  splits.each do |split|
    extracted_split = split.extract_from_input_source(input_source)
  end
```
{% endtab %}

{% tab title="Java" %}
```java
import com.mindee.input.LocalInputSource;
import com.mindee.v2.product.split.SplitResponse;
import com.mindee.v2.product.split.SplitRange;

public void handleResponse(
  SplitResponse response,
  LocalInputSource inputSource
) {
  var splits = response.getInference().getResult().getSplits();

  for (SplitRange split : splits) {
    var extractedSplit = split.extractFromInputSource(inputSource);
  }
}
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using System;
using Mindee.Input;
using Mindee.V2.Product.Split;

public void HandleResponse(SplitResponse response, LocalInputSource inputSource)
{
    var splits = response.Inference.Result.Splits;

    foreach (SplitRange split in splits)
    {
        var extractedSplit = split.ExtractFromInputSource(inputSource);
    }
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Only the methods documented here are production-ready**.

This is because we are still improving the SDKs, hang tight!
{% endhint %}
