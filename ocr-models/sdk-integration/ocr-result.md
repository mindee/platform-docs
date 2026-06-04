---
description: Reference documentation on processing an OCR result using the Mindee SDKs.
icon: brain-circuit
---

# OCR Result

{% include "../../.gitbook/includes/result-response-requirements.md" %}

## Accessing the Page OCR

An `OCRPage` describes the text and words of a single page in the document.

### `OCRPage` Attributes

#### Content

Full text content extracted from the document page.

#### Words

List of all words found on the page.

Each word has the following properties:

* Content: Text content of the word.
* Polygon: Coordinates of the detected word.

{% tabs %}
{% tab title="Python" %}
```python
from mindee import OCRResponse

def handle_response(response: OCRResponse) -> None:
    pages = response.inference.result.pages

    for page in pages:
        # Page-level properties
        page_content = page.content
        words = page.words

        # Access the full text content extracted from this page.
        print(f"Page content: {page_content}")

        # Access all words detected on this page.
        for word in words:
            word_content = word.content
            word_polygon = word.polygon

            print(f"Word: {word_content}")
            print(f"Polygon: {word_polygon}")
```
{% endtab %}

{% tab title="Node.js" %}
```javascript
handleResponse(response) {
  const pages = response.inference.result.pages;

  for (const page of pages) {
    // Full text content extracted from this page.
    const pageContent = page.content;
    console.log(`Page content: ${pageContent}`);

    // All words detected on this page.
    for (const word of page.words) {
      const wordContent = word.content;
      const wordPolygon = word.polygon;

      console.log(`Word: ${wordContent}`);
      console.log(`Polygon: ${wordPolygon.toString()}`);
    }
  }
}
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mindee\V2\Product\Ocr\OcrResponse;

public function handleResponse(OcrResponse $response)
{
    $pages = $response->inference->result->pages;
}
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
def handle_response(response)
  pages = response.inference.result.pages

  pages.each do |page|
    # Page-level properties
    page_content = page.content
    words = page.words

    # Access the full text content extracted from this page.
    puts "Page content: #{page_content}"

    # Access all words detected on this page.
    words.each do |word|
      word_content = word.content
      word_polygon = word.polygon

      puts "Word: #{word_content}"
      puts "Polygon: #{word_polygon}"
    end
  end
end
```
{% endtab %}

{% tab title="Java" %}
```java
import com.mindee.v2.product.ocr.OcrPage;
import com.mindee.v2.product.ocr.OcrResponse;
import com.mindee.v2.product.ocr.OcrWord;

public void handleResponse(OcrResponse response) {
    var pages = response.getInference().getResult().getPages();

    for (OcrPage page : pages) {
        // Page-level properties
        String pageContent = page.getContent();
        var words = page.getWords();

        // Access the full text content extracted from this page.
        System.out.println("Page content: " + pageContent);

        // Access all words detected on this page.
        for (OcrWord word : words) {
            String wordContent = word.getContent();
            var wordPolygon = word.getPolygon();

            System.out.println("Word: " + wordContent);
            System.out.println("Polygon: " + wordPolygon.toString());
        }
    }
}
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using Mindee.V2.Product.Ocr;

public void HandleResponse(OcrResponse response)
{
    var pages = response.Inference.Result.Pages;

    foreach (var page in pages)
    {
        // Page-level properties
        string pageContent = page.Content;
        var words = page.Words;

        // Access the full text content extracted from this page.
        Console.WriteLine($"Page content: {pageContent}");

        // Access all words detected on this page.
        foreach (var word in words)
        {
            string wordContent = word.Content;
            var wordPolygon = word.Polygon;

            Console.WriteLine($"Word: {wordContent}");
            Console.WriteLine($"Polygon: {wordPolygon}");
        }
    }
}
```
{% endtab %}
{% endtabs %}
