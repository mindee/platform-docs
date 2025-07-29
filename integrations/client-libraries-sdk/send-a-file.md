---
description: In-depth instruction on handling files using a Mindee client library.
icon: file-lines
---

# Use a File

## Requirements

You'll nee to have your Mindee client configured correctly as described in the [configure-the-client.md](configure-the-client.md "mention") page.

## Overview

Overall, the steps to sending a file are:

1. Load a source file.
2. _Optional_: adjust the source file before sending.
3. Use the Mindee client instance to send the file.

## Load a Source File

You can load a source file from a path, from raw bytes, from a bytes stream, or from a language-specific object. Choose the appropriate type based on your application requirements.

If you're unsure of which to use, we recommend loading from a path.

{% tabs %}
{% tab title="Python" %}
You'll need to use the `mindee_client` instance created in [configure-the-client.md](configure-the-client.md "mention").

To load a path string, use `source_from_path` .

```python
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

input_base64 = "iVBORw0KGgoAAAANSUhEUgAAABgAAA ..."

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

{% tab title="PHP" %}
To load a file, you'll need to import the corresponding input class from the `Mindee\Input` namespace.

To load a path string, use `PathInput`.

```php
use Mindee\Input\PathInput;

$filePath = "/path/to/the/file.ext";
$inputSource = new PathInput($filePath);
```

To load a file resource, use `FileInput`.

```php
use Mindee\Input\FileInput;

$handle = fopen("/path/to/the/file.ext", "rb");
$inputSource = new FileInput($handle);
```

To load raw bytes, use `BytesInput`.

```php
use Mindee\Input\BytesInput;

$filePath = "/path/to/the/file.ext";
$handle = fopen($filePath, "rb");
$contents = fread($handle, filesize($filePath));

$inputSource = new BytesInput($contents, "file.ext");
```

To load a base-64 string, use `Base64Input` .\
The string will be decoded into bytes internally.

```php
use Mindee\Input\Base64Input;

$inputBase64 = "iVBORw0KGgoAAAANSUhEUgAAABgAAA ..."

$inputSource = Base64Input($inputBase64, "base64_file.txt");
```
{% endtab %}

{% tab title="Java" %}
To load a file, initialize it using the `LocalInputSource` class.

This class has different constructors to allow for opening various types of inputs.

&#x20;To load a path string:

```java
String filePath = "/path/to/the/file.ext";

LocalInputSource inputSource = new LocalInputSource(filePath);
```

To load a `File` instance:

```java
File file = new File("/path/to/the/file.ext");

LocalInputSource inputSource = new LocalInputSource(file);
```

To load a byte array:

```java
byte[] fileBytes = Files.readAllBytes("/path/to/the/file.ext");
String filename = "file.ext";

LocalInputSource inputSource = new LocalInputSource(fileBytes, filename);
```

To load an `InputStream` instance:

```java
InputStream fileStream = new FileInputStream(
    new File("/path/to/the/file.ext")
);
String filename = "file.ext";

LocalInputSource inputSource = new LocalInputSource(fileStream, filename);
```

To load a base-64 string:

```java
String inputBase64 = "iVBORw0KGgoAAAANSUhEUgAAABgAAA ...";
String filename = "file.ext";

LocalInputSource inputSource = new LocalInputSource(inputBase64, filename);
```
{% endtab %}

{% tab title=".NET" %}
To load a file, initialize it using the `LocalInputSource` class.

This class has different constructors to allow for opening various types of inputs.

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

For example to compress and resize to no greater than 1920x1920 pixels:

```python
input_source.compress(
    quality=85, max_width=1920, max_height=1920
)
```
{% endtab %}

{% tab title="Node.js" %}
Using the `inputSource` instance created above.

Basic usage is very simple, and can be applied to both images and PDFs:

```typescript
inputSource.compress(85);
```

For images, you can also set a maximum height and/or width.\
The aspect ratio will always be preserved.

For example to compress and resize to no greater than 1920x1920 pixels:

```typescript
inputSource.compress(85, 1920, 1920);
```
{% endtab %}

{% tab title="Java" %}
Using the `inputSource` instance created above.

Basic usage is very simple, and can be applied to both images and PDFs:

```java
inputSource.compress(85);
```

For images, you can also set a maximum height and/or width.\
The aspect ratio will always be preserved.

For example to compress and resize to no greater than 1920x1920 pixels:

```java
inputSource.compress(85, 1920, 1920);
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

For example to compress and resize to no greater than 1920x1920 pixels:

```csharp
inputSource.Compress(
    quality: 85, maxWidth: 1920, maxHeight: 1920);
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
    page_indexes=[0],
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
    page_indexes=[0, -2, -1],
)

# For all documents:
# Remove the first page
PageOptions(
    operation="REMOVE",
    page_indexes=[0],
)

# Only for documents having 10 or more pages:
# Remove the first 5 pages
PageOptions(
    operation="REMOVE",
    on_min_pages=10,
    page_indexes=list(range(5)),
)
```
{% endtab %}

{% tab title="Node.js" %}
Using the `inputSource` instance created above.

```typescript
// Set the options as follows:
// For all documents, keep only the first page
const pageOptions: PageOptions = {
  operation: PageOptionsOperation.KeepOnly,
  pageIndexes: [0],
};

// Apply in-memory
await inputDoc.applyPageOptions(pageOptions);
```

Some other examples:

```typescript
// Only for documents having 3 or more pages:
// Keep only these pages: first, penultimate, last
const pageOptions: PageOptions = {
  operation: PageOptionsOperation.KeepOnly,
  onMinPages: 3,
  pageIndexes: [0, -2, -1],
};

// For all documents:
// Remove the first page
const pageOptions: PageOptions = {
  operation: PageOptionsOperation.Remove,
  pageIndexes: [0],
};

// Only for documents having 10 or more pages:
// Remove the first 5 pages
const pageOptions: PageOptions = {
  operation: PageOptionsOperation.Remove,
  onMinPages: 10,
  pageIndexes: [0, 1, 2, 3, 4],
};
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
Using:

* `input_source`  created above
* `mindee_client` and `inference_params` created in [configure-the-client.md](configure-the-client.md "mention").

For **polling**, use:

```python
response = mindee_client.enqueue_and_get_inference(
    input_source, inference_params
)

# To easily test which data was extracted,
# simply print an RST representation of the inference
print(response.inference)
```

For **webhooks**, use:

```python
response = mindee_client.enqueue_inference(
    input_source, inference_params
)

# You can save the job ID for your records
print(response.job.id)

# If you set an `alias`, you can verify it was taken into account
print(response.job.alias)
```

**Note:** You can use both methods!

First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `enqueue_and_get_inference` .\
You'll get the response via polling and webhooks will be used as well.&#x20;
{% endtab %}

{% tab title=".NET" %}
Using:

* `inputSource`  created above
* `mindeeClient` and `inferenceParams` created in [configure-the-client.md](configure-the-client.md "mention").

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

**Note:** You can also use both methods!

First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `EnqueueAndGetInferenceAsync`.\
You'll get the response via polling and webhooks will be used as well.
{% endtab %}
{% endtabs %}

## Process the Result

Now that your file is sent, you'll want to get the results from Mindee and use them in your application.

Head on over to the [process-the-result.md](process-the-result.md "mention") page for details on the next step.
