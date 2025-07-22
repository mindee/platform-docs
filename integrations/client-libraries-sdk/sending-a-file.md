---
description: How to send a file to Mindee using a client library.
---

# Sending a File

## Requirements

Before proceeding you'll need to have one of the [official Mindee client libraries](./) installed.

## Overview

This page will go into detail for each step, and list all possible options.\
It is reference documentation.

{% hint style="info" %}
**If you want just the quick TL;DR:**

* Take a look at the [integrating-mindee.md](../../getting-started/integrating-mindee.md "mention") page.
* Use the **search bar** at the top to ask our documentation AI to write code samples for you.
{% endhint %}

Overall, the steps to sending a file are:

1. Initialize the Mindee client.
2. Set inference parameters, in particular the model ID to use.
3. Load a source file.
4. _Optional_: adjust the source file before sending.
5. Send the file with the proper parameters.

## Initialize the Mindee Client

This should be the first step in your code.

You should reuse the same client instance for all calls.

{% tabs %}
{% tab title="Python" %}
First import the needed classes:

```python
from mindee import ClientV2, InferenceParameters
```

For the API key, you can pass it directly to the client.\
This is useful for quick testing.

```python
api_key = "MY_API_KEY"

mindee_client = ClientV2(api_key)
```

Instead of passing the key directly, you can also set the following environment variable:

`MINDEE_V2_API_KEY`

This is recommended for production use.\
In this way there is no need to pass the `api_key` when initializing the client.

```python
mindee_client = ClientV2()
```
{% endtab %}

{% tab title=".NET" %}
First add the required namespaces.

```csharp
using Mindee;
using Mindee.Input;
```

For the API key, you can pass it directly to the client.\
This is useful for quick testing.

```csharp
string apiKey = "MY_API_KEY";

MindeeClientV2 mindeeClient = new MindeeClientV2(apiKey);
```

Instead of passing the key directly, you can also set the following environment variable:

`MindeeV2__ApiKey`

This is recommended for production use.\
In this way there is no need to pass the `apiKey` argument when initializing the client.

```csharp
MindeeClientV2 mindeeClient = new MindeeClientV2();
```
{% endtab %}
{% endtabs %}

## Set Inference Parameters

Inference parameters control:

* which model to use
* server-side processing options
* how the results will be returned to you

### Processing Options

These are mostly the same options as present in the Web API.

{% tabs %}
{% tab title="Python" %}
Only the `model_id` is required.

```python
params = InferenceParameters(
    # ID of the model, required.
    model_id="MY_MODEL_ID",
    
    # Options:

    # If set to `True`, will enable Retrieval-Augmented Generation.
    rag=True,

    # Use an alias to link the file to your own DB.
    # If empty, no alias will be used.
    alias="MY_ALIAS"
)
```
{% endtab %}

{% tab title=".NET" %}
Only the `modelId` is required.

```csharp
var inferenceParams = new InferenceParameters(
    // ID of the model, required.
    modelId: "MY_MODEL_ID"

    // Options:

    // If set to `true`, will enable Retrieval-Augmented Generation.
    , rag: false

    // Use an alias to link the file to your own DB.
    // If empty, no alias will be used.
    , alias: "MY_ALIAS"
);
```
{% endtab %}
{% endtabs %}

### Polling Configuration

The client library will POST the request for you, and then automatically poll the API.

{% tabs %}
{% tab title="Python" %}
When polling you really only need to set the `model_id` .

```python
params = InferenceParameters(model_id="MY_MODEL_ID")
```

You can also set the various polling parameters.\
However, **we do not recommend** setting this option unless you are encountering timeout problems.

```python
from mindee import PollingOptions

params = InferenceParameters(
    model_id="MY_MODEL_ID",
    # Set only if having timeout issues.
    polling_options=PollingOptions(
        # Initial delay before the first polling attempt.
        initial_delay_sec=3,
        # Delay between each polling attempt.
        delay_sec=1.5,
        # Total number of polling attempts.
        max_retries=80,
    ),
    # ... any other options ...
)
```
{% endtab %}

{% tab title=".NET" %}
When polling you really only need to set the `modelId` .

```csharp
var inferenceParams = new InferenceParameters(modelId: "MY_MODEL_ID");
```

You can also set the various polling parameters.\
However, **we do not recommend** setting this option unless you are encountering timeout problems.

```csharp
var inferenceParams = new InferenceParameters(
    modelId: "MY_MODEL_ID"
    // Set only if having timeout issues.
    , pollingOptions: new AsyncPollingOptions(
        // Initial delay before the first polling attempt.
        initialDelaySec: 3.0,
        // Delay between each polling attempt.
        intervalSec: 1.5,
        // Total number of polling attempts.
        maxRetries: 80
    )
    // ... any other options ...
);
```
{% endtab %}
{% endtabs %}

### Webhook Configuration

The client library will POST the request to your Web server, as configured by your webhook endpoint.

For more information on webhooks, take a look at the [webhooks.md](../api-overview/webhooks.md "mention") page.

{% tabs %}
{% tab title="Python" %}
When using a webhook, you'll need to set the `model_id` and which webhook(s) to use.

```python
params = InferenceParameters(
    model_id="MY_MODEL_ID",
    webhook_ids=["ENDPOINT_1_UUID"],
    
    # ... any other options ...
)
```
{% endtab %}

{% tab title=".NET" %}
When using a webhook, you'll need to set the `modelId` and which webhook(s) to use.

```csharp
var inferenceParams = new InferenceParameters(
    modelId: "MY_MODEL_ID"
    , webhookIds: new List<string>{ "ENDPOINT_1_UUID" }
    
    // ... any other options ...
);
```
{% endtab %}
{% endtabs %}

You can specify any number of webhook endpoint IDs, each will be sent the payload.

## Load a Source File

You can load a source file from a path, from raw bytes, from a bytes stream, or from a language-specific object.

{% tabs %}
{% tab title="Python" %}
You'll need to use the `mindee_client` instance created above.

To load a path string, use `source_from_path` .

```
input_path = "/path/to/the/file.ext"
input_source = mindee_client.source_from_path(input_path)
```

To load a `Path` instance, use `source_from_path`.

```python
from pathlib import Path

input_path = Path("/path/to/the/file.ext")
input_source = mindee_client.source_from_path(input_path)
```

To load raw bytes, use `source_from_bytes` .

```python
from pathlib import Path

input_path = Path("/path/to/the/file.ext")
with input_path.open("rb") as fh:
    input_bytes = fh.read()

input_source = mindee_client.source_from_bytes(
    input_bytes,
    filename="file.ext",
)
```

To load a base-64 string, use `source_from_b64string` .\
The string will be decoded into bytes internally.

```python
from pathlib import Path

input_path = Path("/path/to/the/base64_file.txt")
with input_path.open("r", encoding="utf-8") as fh:
    input_base64 = fh.read()

input_source = mindee_client.source_from_b64string(
    input_base64,
    filename="base64_file.txt",
)
```

To load a file handle, use `source_from_file`.\
It **must** be opened in binary mode, as a `BinaryIO` .

```python
from pathlib import Path

input_path = Path("/path/to/the/file.ext")
with input_path.open("rb") as fh:
    input_source = mindee_client.source_from_file(fh)
    # IMPORTANT:
    # Continue all operations inside the 'with' statement.
    mindee_client.enqueue_and_get_inference(
        input_source, params
    )
```
{% endtab %}

{% tab title=".NET" %}
To load a file, initialize it using the `LocalInputSource` class.

This class has various constructors to allow for opening various types of inputs.

&#x20;To load a path string:

```csharp
string filePath = "/path/to/the/file.ext";

var inputSource = new LocalInputSource(filePath)
```

To load a `FileInfo` instance:

```csharp
FileInfo fileinfo = new FileInfo("/path/to/the/file.ext");

var inputSource = new LocalInputSource(fileinfo)
```

To load a byte array:

```csharp
byte[] fileBytes = File.ReadAllBytes("/path/to/the/file.ext");
string filename = "file.ext";

var inputSource = new LocalInputSource(fileBytes, filename)
```

To load a `Stream` instance:

```csharp
Stream fileStream = FileStream SourceStream = File.Open(
    "/path/to/the/file.ext", FileMode.Open);
string filename = "file.ext";

var inputSource = new LocalInputSource(fileStream, filename)
```
{% endtab %}
{% endtabs %}

## Adjust the Source File

Optionally make changes and adjustments to the source file before sending.

{% hint style="info" %}
All file adjustments are applied in-memory to the source file instance.

If loaded from disk, the original file is not modified.
{% endhint %}

### Fixing PDF Headers

In some cases, PDFs will have corrupt or invalid headers.\
These files will return a 4xx HTTP error as the server will be unable to process them.

You can try to fix the headers using the provided functions.

{% tabs %}
{% tab title="Python" %}
Using the `input_source` instance created above.

```python
input_source.fix_pdf()
```
{% endtab %}
{% endtabs %}

### File Compression

There is no need to send excessively large files to the Mindee API.

Unfortunately, many modern smartphones can take very high resolution images.

We provide a way to compress images before sending to the API.

{% tabs %}
{% tab title="Python" %}
Using the `input_source` instance created above.

Basic usage is very simple, and can be applied to both images and PDFs:

```python
input_source.compress(quality=85)
```

For images, you can also set a maximum height and/or width.\
The aspect ratio will always be preserved.

```python
input_source.compress(
    max_width=1920, max_height=1920,
)
```
{% endtab %}

{% tab title=".NET" %}
Using the `inputSource` instance created above.

Basic usage is very simple, and can be applied to both images and PDFs:

```csharp
inputSource.Compress(quality: 85);
```

For images, you can also set a maximum height and/or width.\
The aspect ratio will always be preserved.

```csharp
inputSource.Compress(
    maxWidth: 1920, maxHeight: 1920);
```
{% endtab %}
{% endtabs %}

### PDF Page Manipulations

In some cases, PDFs will have some superfluous pages present.

For example a cover page or terms and conditions which are not useful to the desired data extraction.

These extra pages count towards your billing and slow down processing.

It is therefore in your best interest to remove them before sending.

**Parameters:**

* "page indexes" is required and is a list of 0-based page indexes.
* "operation" specifies whether to keep only specified pages or remove specified pages.
* "on min pages" is optional and specifies the minimum number of pages a document must have for the operation to take place. The value of `0` means any number of pages.

{% tabs %}
{% tab title="Python" %}
Using the `input_source` instance created above.

```python
from mindee import PageOptions

# Set the options as follows:
# For all documents, keep only the first page
page_options = PageOptions(
    operation="KEEP_ONLY",
    page_indexes=[0]
)

# Apply in-memory
input_source.apply_page_options(page_options)
```

Some other examples:

```python
# Only for documents having 3 or more pages:
# Keep only these pages: first, penultimate, last
PageOptions(
    operation="KEEP_ONLY",
    on_min_pages=3,
    page_indexes=[0, -2, -1]
)

# For all documents:
# Remove the first page
PageOptions(
    operation="REMOVE",
    page_indexes=[0]
)

# Only for documents having 10 or more pages:
# Remove the first 5 pages
PageOptions(
    operation="REMOVE",
    on_min_pages=10,
    page_indexes=list(range(5))
)
```
{% endtab %}

{% tab title=".NET" %}
Using the `inputSource` instance created above.

```csharp
// Set the options as follows:
// For all documents, keep only the first page
var pageOptions = new PageOptions(
    operation: PageOptionsOperation.KeepOnly
    , pageIndexes: [ 0 ]);

// Apply in-memory
inputSource.ApplyPageOptions(pageOptions);
```

Some other examples:

```csharp
// Only for documents having 3 or more pages:
// Keep only these pages: first, penultimate, last
new PageOptions(
    operation: PageOptionsOperation.KeepOnly
    , onMinPages: 3
    , pageIndexes: new short[] { 0, -2, -1 }
);

// For all documents:
// Remove the first page
new PageOptions(
    operation: PageOptionsOperation.Remove
    , pageIndexes: new short[] { 0 }
);

// Only for documents having 10 or more pages:
// Remove the first 5 pages
new PageOptions(
    operation: PageOptionsOperation.Remove
    , onMinPages: 10
    , pageIndexes: new short[] { 0, 1, 2, 3, 4 }
);
```
{% endtab %}
{% endtabs %}

## Send the File

Now that all has been set, we can send the file to the Mindee servers for data extraction!

{% tabs %}
{% tab title="Python" %}
Using the `mindee_client` , `input_source` , and `params` created in the steps above.

For **polling**, use:

```python
response = mindee_client.enqueue_and_get_inference(
    input_source, params
)

# To easily test which data was extracted,
# simply print an RST representation of the inference
print(response.inference)
```

For **webhooks**, use:

```python
response = mindee_client.enqueue_inference(
    input_source, params
)

# You can save the job ID for your records
print(response.job.id)

# If you set an `alias`, you can verify it was taken into account
print(response.job.alias)
```

**Note:** You can also use both methods!\
First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `enqueue_and_get_inference` .\
You'll get the response via polling and webhooks will be used as well.
{% endtab %}

{% tab title=".NET" %}
Using the `mindeeClient` , `inputSource` , and `inferenceParams` created in the steps above.

For **polling**, use:

```csharp
var response = await mindeeClient.EnqueueAndGetInferenceAsync(
    inputSource, inferenceParams);

// To easily test which data was extracted,
// simply print an RST representation of the inference
System.Console.WriteLine(response.Inference.ToString());
```

For **webhooks**, use:

```csharp
var response = mindeeClient.EnqueueInferenceAsync(
    inputSource, inferenceParams
)

// You can save the job ID for your records
System.Console.WriteLine(response.Job.Id)

// If you set an `alias`, you can verify it was taken into account
System.Console.WriteLine(response.Job.Alias)
```

**Note:** You can also use both methods!\
First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `EnqueueAndGetInferenceAsync`.\
You'll get the response via polling and webhooks will be used as well.
{% endtab %}
{% endtabs %}

## Process the Result

This page is long enough as it is, don't you think?

Head on over to the [processing-a-result.md](processing-a-result.md "mention") page for details on the next step.
