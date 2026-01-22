---
description: >-
  Reference documentation on processing responses using the Mindee client
  libraries.
icon: cloud-arrow-down
---

# Process the Response

{% include "../../.gitbook/includes/this-is-reference-documenta....md" %}

## Requirements

You'll need to have already sent a file or URL as described in the [send-a-file-or-url.md](send-a-file-or-url.md "mention") section.

## Overview

Depending on how you've sent the file, there are two ways of obtaining the result.

If you've sent via polling (or polling and webhook) you'll get the response directly in your method call.

If you've sent only via webhook, you'll receive the response on your Web server.

Here we'll go over how you can best process the results.

## Load From Webhook

If you're using the webhook pattern, you'll need to use the payload sent to your Web server.

Reading the callback data will vary greatly depending on your HTTP server.\
This is therefore beyond the scope of this example.

Regardless of how you access the JSON payload sent by the Mindee servers, loading this data is done by using a LocalResponse class.

Once it is loaded you can access the data in exactly the same way as a polling response.

To verify the HMAC signature, you'll need the Signing Secret from the webhook:

<figure><img src="../../.gitbook/assets/webhook-copy-secret.png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Python" %}
Assuming you're able to get the raw HTTP request via the variable `request` .

```python
from mindee import LocalResponse, InferenceResponse

# Load the JSON string sent by the Mindee webhook POST callback.
local_response = LocalResponse(request.body())

# You can also load the json from a local path.
# local_response = LocalResponse("path/to/my/file.ext")

# Optionally: verify the HMAC signature
# You'll need to get the "X-Signature" custom HTTP header.
hmac_signature = request.headers.get("X-Signature")
is_valid = local_response.is_valid_hmac_signature(
    "obviously-fake-secret-key", hmac_signature
)
if not is_valid:
    raise Error("Bad HMAC signature! Is someone trying to do evil?")

# Deserialize the response into objects
response = local_response.deserialize_response(InferenceResponse)
```
{% endtab %}

{% tab title="Node.js" %}
Assuming you're able to get the raw HTTP request via the variable `request` .

```javascript
async handleMindeeResponse(data, hmacSignature) {
  const localResponse = new mindee.LocalResponse(data);
  await localResponse.init();

  const isValid = localResponse.isValidHmacSignature(
      "obviously-fake-secret-key", hmacSignature
    );
  if (!isValid) {
    throw Error("Bad HMAC signature! Is someone trying to do evil?");
  }
  const response = await localResponse.deserializeResponse(
    mindee.InferenceResponse
  );
}

// Load the JSON string sent by the Mindee webhook POST callback.
// Will vary depending on your implementation.
async handleMindeePost(request, response) {
  let body = "";
  request.on("data", function (data) {
    body += data;
  });
  req.on("end", function () {
    // Optionally: verify the HMAC signature
    // You'll need to get the "X-Signature" custom HTTP header.
    const hmacSignature = request.headers.get("X-Signature");
    
    // validate using the entire body of the response with the signature header
    await handleMindeeResponse(body, hmacSignature);
  });
}
```
{% endtab %}

{% tab title="Ruby" %}
Assuming you're able to get the raw HTTP request via the variable `request` .

```ruby
require 'mindee'

# Load the JSON string sent by the Mindee webhook POST callback.
local_response = Mindee::Input::LocalResponse.new(request.body.to_s)

# You can also use a File object as the input.
# FILE_PATH = File.join('path', 'to', 'file.json').freeze
# local_response = Mindee::Input::LocalResponse.new(FILE_PATH);

# Optional: verify the HMAC signature.
unless local_response.valid_hmac_signature?(my_secret_key, 'dummy signature')
  raise "Invalid HMAC signature!"
end

# Deserialize the response:
response = local_response.deserialize_response(
  Mindee::Parsing::V2::InferenceResponse
)

# Print a summary of the parsed data in RST format
puts response
```
{% endtab %}

{% tab title="PHP" %}
Assuming you're able to get the raw HTTP request via the variable `$requestBody` .

```php
<?php
  use Mindee\Input\LocalResponse;
  use Mindee\Error\MindeeException;
  use Mindee\Parsing\V2\InferenceResponse;

  // Load the JSON string sent by the Mindee webhook POST callback.
  $localResponse = new LocalResponse($requestBody);
  
  // Or load from a file path:
  // $localResponse = new LocalResponse($filePath);

  // Optional: verify the HMAC signature.
  if (!$localResponse->isValidHmacSignature($mySecretKey, 'dummy signature')){
    throw new MindeeException("Invalid HMAC signature!");
  }
  
  // Deserialize the response:
  $response = $localResponse->deserializeResponse(InferenceResponse::class);

  // Print a summary of the parsed data in RST format
  echo $response->inference;
```
{% endtab %}

{% tab title="Java" %}
Assuming you have a Web server instance `myHttpServer` .

```java

// Load the JSON string sent by the Mindee webhook POST callback.
String jsonData = myHttpServer.getPostBodyAsString();
LocalResponse localResponse = new LocalResponse(jsonData);

// Verify the HMAC signature.
// You'll need to get the "X-Signature" custom HTTP header.
String hmacSignature = myHttpServer.getHeader("X-Signature");
boolean isValid = localResponse.isValidHmacSignature(
    "obviously-fake-secret-key", hmacSignature
);
if (!isValid) {
    throw new Exception("Bad HMAC signature! Is someone trying to do evil?");
}

// You can also use a File object as the input.
//LocalResponse localResponse = new LocalResponse(
//    new File("/path/to/file.json"));

// Deserialize the response into objects
InferenceResponse response = localResponse.deserializeResponse(
    InferenceResponse.class
);

// Print a summary of the parsed data
System.out.println(response.getInference().toString());
```
{% endtab %}

{% tab title=".NET" %}
Assuming you're able to get the raw HTTP request via the variable `request` .

```csharp
using Mindee.Parsing.V2;

public void HandleMindeeCallback(HttpRequest request)
{
    LocalResponse localResponse;

    using (var reader = new StreamReader(request.Body))
    {
        localResponse = new LocalResponse(reader.ReadToEnd());
    }
    
    // Verify the HMAC signature.
    // You'll need to get the "X-Signature" custom HTTP header.
    string hmacSignature = request.Headers.get("X-Signature");
    bool isValid = localResponse.IsValidHmacSignature(
         "obviously-fake-secret-key", hmacSignature);
    if (!isValid)
        throw new Exception("Bad HMAC signature! Is someone trying to do evil?");

    // Deserialize the response into objects
    var response = localResponse.DeserializeResponse<InferenceResponse>();
    
    // Print a summary of the parsed data
    System.Console.WriteLine(response.Inference);
}
```
{% endtab %}
{% endtabs %}

## The Inference Object

This is the top-level object in the response.

It contains the following attributes:

* `id` UUID of the inference
* `model` Model used for the inference
* `file` Metadata concerning the file used for the inference
* `result` Result of inference processing, the most important portion of the response.
  * Fields: For handling the extracted fields, see the [process-result-fields.md](process-result-fields.md "mention") section.
  * Raw Text: For using the extracted text, see the [#raw-text](process-the-response.md#raw-text "mention") section.

## File Metadata

You can access various metadata concerning the file sent for processing.

{% tabs %}
{% tab title="Python" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```python
from mindee import InferenceResponse
from mindee.parsing.v2 import InferenceFile

def handle_response(response: InferenceResponse):
    inference_file: InferenceFile = response.inference.file

    # various attributes are available, such as:
    filename: str = inference_file.name
    page_count: int = file.page_count
    mime_type: str = file.mine_type
```
{% endtab %}

{% tab title="Node.js" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```javascript
handleResponse(response) {
  const file = response.inference.file;

  // various attributes are available, such as:
  const filename = file.name;
  const pageCount = file.pageCount;
  const mimeType = file.mimeType;
}
```
{% endtab %}

{% tab title="PHP" %}
Using the `$response` deserialized object from either the polling response or a webhook payload.

```php
use Mindee\Parsing\V2\InferenceResponse;

public function handleResponse(InferenceResponse $response)
{
    $file = $response->inference->file;

    // various attributes are available, such as:
    $filename = $file->name;
    $pageCount = $file->pageCount;
    $mimeType = $file->mimeType;
}
```
{% endtab %}

{% tab title="Ruby" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```ruby
require 'mindee'

def handle_response(response)
  file = response.inference.file

  # various attributes are available, such as:
  filename = inference_file.name
  page_count = file.page_count
  mime_type = file.mime_type
end
```
{% endtab %}

{% tab title="Java" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```java
import com.mindee.parsing.v2.InferenceFile;
import com.mindee.parsing.v2.InferenceResponse;

public void handleResponse(InferenceResponse response) {
    InferenceFile file = response.inference.getFile();

    // various attributes are available, such as:
    String filename = file.getName();
    int pageCount = file.getPageCount();
    String mimeType = file.getMimeType();
}
```
{% endtab %}

{% tab title=".NET" %}
Using the `response` deserialized object from either the polling response or a webhook payload.

```csharp
using Mindee.Parsing.V2;

public void HandleResponse(InferenceResponse response)
{
    InferenceFile file = response.Inference.File;

    // various attributes are available, such as:
    string filename = file.Name;
    int pageCount = file.PageCount;
    string mimeType = file.MimeType;
}
```
{% endtab %}
{% endtabs %}

## Results

### Fields

For handling the extracted fields, see the [process-result-fields.md](process-result-fields.md "mention") section.

### Raw Text

Access the full text content from the document, extracted as strings.

The object will always be null if the [raw-text-full-ocr.md](../../extraction-models/optional-features/raw-text-full-ocr.md "mention") feature was not activated.

Using the `InferenceResponse` deserialized object from either the polling response or a webhook payload.

{% tabs %}
{% tab title="Python" %}
```python
from mindee import InferenceResponse

def handle_response(response: InferenceResponse):
    raw_text = response.inference.result.raw_text
    
    # get the entire document as a single string
    document_text = str(raw_text)
    
    # loop over pages
    for page in raw_text.pages:
        page_text = page.content
```
{% endtab %}

{% tab title="Node.js" %}
```javascript
handleResponse(response) {
  const rawText = response.inference.result.rawText;

  // get the entire document as a single string
  const documentText = rawText.toString();
  
  // loop over pages
  for (const page of rawText.pages) {
    const pageText = page.content;
  }
}
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mindee\Parsing\V2\InferenceResponse;

public function handleResponse(InferenceResponse $response)
{
    $rawText = $response->inference->result->rawText;

    // get the entire document as a single string
    $documentText = strval($rawText);

    // loop over pages
    foreach ($rawText->pages as $page) {
        $pageText = $page->content;
    }
}
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'mindee'

def handle_response(response)
  raw_text = response.inference.result.raw_text

  # get the entire document as a single string
  document_text = raw_text.to_s

  # loop over pages
  raw_text.pages.each do |page|
    page_text = page.content
  end
end
```
{% endtab %}

{% tab title="Java" %}
```java
import com.mindee.parsing.v2.InferenceResponse;
import com.mindee.parsing.v2.RawText;
import com.mindee.parsing.v2.RawTextPage;

public void handleResponse(InferenceResponse response) {
    RawText rawText = response.getInference().getResult().getRawText();
    
    // get the entire document as a single string
    String documentText = rawText.toString();
    
    // loop over pages
    for (RawTextPage page : rawText.getPages()) {
        String pageText = page.getContent();
    }
}
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using Mindee.Parsing.V2;

public void HandleResponse(InferenceResponse response)
{
    RawText rawText = response.Inference.Result.RawText;
    
    // get the entire document as a single string
    string documentText = rawText.ToString();

    // loop over pages
    foreach (RawTextPage page in rawText.Pages)
    {
        string pageText = page.Content;
    }
}
```
{% endtab %}
{% endtabs %}

### RAG

Access information related to the RAG operation. This allows you to add various business logic depending on whether a document was matched (retrieved) during the RAG operation.

The object will always be null if the [improving-accuracy.md](../../extraction-models/optional-features/improving-accuracy.md "mention") feature was not activated.

Using the `InferenceResponse` deserialized object from either the polling response or a webhook payload.

{% tabs %}
{% tab title="Python" %}
```python
from mindee import InferenceResponse

def handle_response(response: InferenceResponse):
  rag = response.inference.result.rag

  if (rag is None):
    print("No RAG operation took place.")
  else:
    print("A RAG operation took place:")

    rag_doc_id = rag.retrieved_document_id

    if (rag_doc_id is None):
      print("No matching document found in RAG database.")
    else
      print(f"Matched on document with ID: {rag_doc_id}")
```
{% endtab %}

{% tab title="Node.js" %}
```javascript
handleResponse(response) {
  const rag = response.inference.result.rag;

    if (rag === undefined) {
        console.log("No RAG operation took place.");
    }
    else {
        console.log("A RAG operation took place:");

        const ragDocId = rag.retrievedDocumentId;

        if (ragDocId === undefined) {
            console.log("No matching document found in RAG database.");
         }
         else {
             console.log(`Matched on document with ID: ${ragDocId}`);
         }
    }
}
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mindee\Parsing\V2\InferenceResponse;

public function handleResponse(InferenceResponse $response)
{
    $rag = response->inference->result->rag;

    if ($rag == null) {
        echo 'No RAG operation took place.';
    }
    else {
        echo 'A RAG operation took place:';

        $ragDocId = $rag->retrievedDocumentId;

        if ($ragDocId == null) {
            echo 'No matching document found in RAG database.';
         }
         else {
             echo "Matched on document with ID: $ragDocId";
         }
    }
}
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'mindee'

def handle_response(response)
  rag = response.inference.result.rag

  if (rag.nil?)
    puts 'No RAG operation took place.'
  else
    puts 'A RAG operation took place:'

    rag_doc_id = rag.retrieved_document_id

    if (rag_doc_id.nil?)
      puts 'No matching document found in RAG database.'
    else
      puts "Matched on document with ID:  #{rag_doc_id}"
    end
end
```
{% endtab %}

{% tab title="Java" %}
```java
import com.mindee.parsing.v2.InferenceResponse;
import com.mindee.parsing.v2.RagMetadata;

public void handleResponse(InferenceResponse response) {
    RagMetadata rag = response.getInference().getResult().getRag();

    if (rag == null) {
        System.out.println("No RAG operation took place.");
    }
    else {
        System.out.println("A RAG operation took place:");

        String ragDocId = rag.getRetrievedDocumentId();

        if (ragDocId == null) {
            System.out.println("No matching document found in RAG database.");
         }
         else {
             System.out.println("Matched on document with ID: " + ragDocId);
         }
    }
}
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using Mindee.Parsing.V2;

public void HandleResponse(InferenceResponse response)
{
    RagMetadata rag = response.Inference.Result.Rag;

    if (rag == null)
        System.Console.WriteLine("No RAG operation took place.");
    else
    {
        System.Console.WriteLine("A RAG operation took place:");

        string ragDocId = rag.RetrievedDocumentId;

        if (ragDocId == null)
            System.Console.WriteLine(
                 "No matching document was found in the RAG database.");
         else
             System.Console.WriteLine(
                "Matched on RAG document with ID: " + ragDocId);
    }
}
```
{% endtab %}
{% endtabs %}
