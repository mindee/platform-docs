---
description: Manage RAG documents associated to a model.
icon: layer-group
---

# RAG Documents

Programmatic handling of RAG documents is useful when needing to integrate their management directly in your system or application. For example, allowing your end-users to annotate documents, or setting up automated pipelines for internal review.

Documents added with the SDKs will also appear on the platform, and documents added on the platform can be manipulated using the SDKs.

Currently RAG documents are limited to Extraction models.

## Overview

The server side APIs are semi-asynchronous: a given route will respond immediately with the current data, but changes require the system some processing time to take effect. During this time the document will be in a transitive state.

In the SDKs, there are two versions of each operation. The main version will poll on the document until the change has been propagated in the system. The [polling options](send-a-file-or-url.md#polling-configuration) are fully configurable, using the same options as the other SDK polling methods.

In the alternate version, the polling and consistency logic is left to the user.

We highly recommend using the polling versions unless there is a specific use case that requires otherwise.

An API key and a [Mindee client instance](configure-the-client.md) is required for all operations.

## Adding New Documents

Upload a file and associate it to a model.

When a file is added, the document entry is created immediately, however the initial annotation will take several seconds to complete.

For the purpose of example we will be loading the file from a path, but any type of [local input source](load-and-adjust-a-file.md#load-a-source-file) may be used. It is not possible to upload an URL.

When using the "upload and get" method, the initial annotation will be included in the method's return object.

Save the document's ID in your system, it will be needed for all subsequent calls, such as updating the annotation or deleting the document.

{% tabs %}
{% tab title="Python" %}
```python
from mindee import PathInput, PollingOptions
from mindee.v2 import Client
from mindee.v2.product.extraction.rag_documents import (
    RagAnnotation,
    RagDocumentUploadParameters,
)

# Load the input source
input_source = PathInput("/path/to/the/file.ext")

post_parameters = RagDocumentUploadParameters(
    model_id="my-extraction-model-id"
)

# Send the file
client = Client()
post_response = client.upload_and_get_rag_document(
    input_source=input_source,
    parameters=post_parameters
    # optional polling options
    # polling_options=PollingOptions( ... ),
)

# Save the document ID
document_id = post_response.id

# The initial annotation
annotation: RagAnnotation = post_response.annotation

# Serialize the annotation to save it
# annotation.to_dict()

# The initial status, should be "Draft"
document_status = post_response.status
```
{% endtab %}

{% tab title="Node.js" %}

{% endtab %}

{% tab title="PHP" %}

{% endtab %}

{% tab title="Ruby" %}

{% endtab %}

{% tab title="Java" %}

{% endtab %}

{% tab title=".NET" %}

{% endtab %}
{% endtabs %}

## Updating Documents

Update the annotation data and status of a given document.

Annotation data and document status can be set in separate calls or jointly in the same call.

Annotation data must be updated as a single field, either the entire set of fields is sent, or none is sent.

In this example, we are using the document ID as returned when uploading the document. For the annotation fields, we are using the "Invoice" catalog template.

{% tabs %}
{% tab title="Python" %}
```python
from mindee import PollingOptions
from mindee.v2 import Client
from mindee.v2.product.extraction.rag_documents import (
    RagAnnotation,
    RagDocumentAnnotationParameters,
)

# RAG document ID as returned by the upload request
document_id = "my-document-id"

# The annotation can be loaded from various sources
with open("path/to/annotation.json", encoding="utf-8") as fh:
    annotation = RagAnnotation(fh) # load from IO
    # annotation = RagAnnotation(fh.read()) # load from str
    # annotation = RagAnnotation(json.load(fh)) # load from dict

# Or use the annotation returned by the upload request
# annotation: RagAnnotation = post_response.annotation

# Modify the annotation
annotation.fields["supplier_name"].selected = True
annotation.fields["supplier_name"].guidelines = "I am the walrus!"
annotation.fields["supplier_name"].value = "Odobenus rosmarus"

patch_parameters = RagDocumentAnnotationParameters(
    document_id=document_id,
    annotation=annotation, # optional
    status="Active", # optional
)

# Send the update
client = Client()
patch_annotation_response = client.update_and_get_rag_annotations(
    parameters=patch_parameters,
    # optional polling options
    # polling_options=PollingOptions( ... ),
)
```
{% endtab %}

{% tab title="Node.js" %}


```typescript
```
{% endtab %}

{% tab title="PHP" %}


```php
```
{% endtab %}

{% tab title="Ruby" %}


```ruby
```
{% endtab %}

{% tab title="Java" %}


```java
```
{% endtab %}

{% tab title=".NET" %}


```cs
```
{% endtab %}
{% endtabs %}

## Deleting Documents

Deleting a document removes the file and its annotation data. Neither can be recovered once deleted.

{% tabs %}
{% tab title="Python" %}
```python
from mindee.v2 import Client

# RAG document ID as returned by the upload request
document_id = "my-document-id"

# Send the deletion request
client = Client()
delete_success = client.delete_extraction_rag_document(document_id)
```
{% endtab %}

{% tab title="Node.js" %}
```typescript
import * as mindee from "mindee";

// RAG document ID as returned by the upload request
const documentId = "my-document-id";

// Send the deletion request
client = new mindee.Client();
deleteSuccess = await client.deleteRagDocument(
  mindee.product.Extraction,
  documentId
);
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mindee\V2\Client;

// RAG document ID as returned by the upload request
$documentId = "my-document-id";

// Send the deletion request
$client = new Client();
$deleteSuccess = $client->deleteExtractionRagDocument($documentId);
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'mindee'

# RAG document ID as returned by the upload request
document_id = "my-document-id"

# Send the deletion request
client = Mindee::V2::Client.new
delete_success = client.delete_rag_document(
  Mindee::V2::Product::Extraction::Extraction,
  document_id
)
```
{% endtab %}

{% tab title="Java" %}
```java
import com.mindee.v2.MindeeClient;

// RAG document ID as returned by the upload request
documentId = "my-document-id";

// Send the deletion request
client = new MindeeClient();
boolean deleteSuccess = client.deleteExtractionRagDocument(documentId);
```
{% endtab %}

{% tab title=".NET" %}
```cs
using Mindee.V2;

// RAG document ID as returned by the upload request
var documentId = "my-document-id";

// Send the deletion request
Client mindeeClient = new Client(apiKey);
bool deleteSuccess = await mindeeClient.DeleteExtractionRagDocumentAsync(documentId);
```
{% endtab %}
{% endtabs %}
