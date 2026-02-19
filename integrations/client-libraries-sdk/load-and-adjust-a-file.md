---
description: >-
  Reference documentation on loading and manipulating files using Mindee client
  libraries.
icon: file-lines
---

# Load and Adjust a File

{% include "../../.gitbook/includes/this-is-reference-documenta....md" %}

## Requirements

In most cases you'll be loading a source file for use in the Mindee Client, take a look at the [configure-the-client.md](configure-the-client.md "mention") section for more info.

However, you don't actually need the client initialized to use these features, only the client library installed.

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
To load a file, you'll need to import the corresponding input class from the `mindee` module.

To load a path string, use `PathInput` .

```python
from mindee import PathInput

input_path = "/path/to/the/file.ext"
input_source = PathInput(input_path)
```

To load a `Path` instance, use `PathInput`.

```python
from pathlib import Path
from mindee import PathInput

input_path = Path("/path/to/the/file.ext")
input_source = PathInput(input_path)
```

To load raw bytes, use `BytesInput` .

```python
from pathlib import Path
from mindee import BytesInput

input_path = Path("/path/to/the/file.ext")
with input_path.open("rb") as fh:
    input_bytes = fh.read()

input_source = BytesInput(
    input_bytes,
    filename="file.ext",
)
```

To load a base-64 string, use `Base64Input` .\
The string will be decoded into bytes internally.

```python
from pathlib import Path
from mindee import Base64Input

input_base64 = "iVBORw0KGgoAAAANSUhEUgAAABgAAA ..."

input_source = Base64Input(
    input_base64,
    filename="base64_file.txt",
)
```

To load a file handle, use `FileInput`.\
It **must** be opened in binary mode, as a `BinaryIO` .

```python
from pathlib import Path
from mindee import FileInput

input_path = Path("/path/to/the/file.ext")
with input_path.open("rb") as fh:
    input_source = FileInput(fh)
    # IMPORTANT:
    # Continue all operations inside the 'with' statement.
    response = mindee_client.enqueue_and_get_result(
        InferenceResponse,
        input_source,
        params,
    )
```
{% endtab %}

{% tab title="Node.js" %}
To load a file, you'll need to import the corresponding input class and instantiate it.

Make sure to import the needed classes:

```typescript
import * as mindee from "mindee";
// If you're on CommonJS:
// const mindee = require("mindee");
```

To load a path string, use `PathInput`.

```typescript
const filePath = "/path/to/the/file.ext";
const inputSource = new mindee.PathInput({ inputPath: filePath });
```

To load a `Buffer` instance, use `BufferInput` .

```typescript
const buffer = Buffer.from(
  await fs.promises.readFile("/path/to/the/file.ext")
);

const inputSource = new mindee.BufferInput({
  buffer: buffer,
  filename: "file.ext",
});
```

To load raw bytes, use `BytesInput` .

```typescript
const inputBytes = await fs.promises.readFile("/path/to/the/file.ext");

const inputSource = new mindee.BytesInput({
  inputBytes: inputBytes,
  filename: "file.ext",
});
```

To load a `Stream`, use `StreamInput`.

```typescript
const stream = fs.createReadStream("/path/to/the/file.ext");

const inputSource = new mindee.StreamInput({
  inputStream: stream,
  filename: "file.ext",
});
```

To load a base-64 string, use `Base64Input` .

```typescript
const b64String = "iVBORw0KGgoAAAANSUhEUgAAABgAAA ...";

const inputSource = new mindee.Base64Input({
  inputString: b64String,
  filename: "base64_file.txt",
});
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

{% tab title="Ruby" %}
To load a path string, use the `PathInputSource` class.

```ruby
input_path = '/path/to/the/file.ext'
input_source = Mindee::Input::Source::PathInputSource.new(input_path)
```

To load raw bytes, use the `BytesInputSource` class.

```ruby
input_bytes = File.binread('/path/to/the/file.ext')
input_source = Mindee::Input::Source::BytesInputSource.new(input_bytes, file_name)
```

To load a base-64 string, use `Base64InputSource`.\
The string will be decoded into bytes internally.

```ruby
input_base64 = 'iVBORw0KGgoAAAANSUhEUgAAABgAAA ...'
input_source = Mindee::Input::Source::Base64InputSource.new(
    input_base64, 'file.ext'
)
```

To load a file handle, use `FileInputSource`.\
It must be opened in binary mode.

```ruby
file = File.open('/path/to/the/file.ext', 'rb')
input_source = Mindee::Input::Source::FileInputSource.new(file, 'file.ext')
```
{% endtab %}

{% tab title="Java" %}
To load a file, initialize it using the `LocalInputSource` class.

This class has different constructors to allow for opening various types of inputs.

To load a path string:

```java
String filePath = "/path/to/the/file.ext";

LocalInputSource inputSource = new LocalInputSource(filePath);
```

To load a `Path` instance:

```java
Path filePath = new Path("/path/to/the/file.ext");

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

To load a path string:

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

## Source File Metadata

Once a source file is loaded, various metadata can be accessed.

This can be useful for applying business rules based on the input file, for example:

* Send PDFs to one model, images to another
* Don't send PDFs with too many pages
* Save the filename to a database
* ...

{% include "../../.gitbook/includes/code-samples-input-source.md" %}

{% tabs %}
{% tab title="Python" %}
```python
filename: str = input_source.filename
is_pdf: bool = input_source.is_pdf
number_of_pages: int = input_source.page_count
```
{% endtab %}

{% tab title="Node.js" %}
```javascript
// make sure to initialze the source first
await inputSource.init();

const filename = inputSource.filename;
const isPdf = inputSource.isPdf();
const numberOfPages = await inputSource.getPageCount();
```
{% endtab %}

{% tab title="PHP" %}
```php
$filename = $inputSource->fileName;
$isPdf = $inputSource->isPdf();
$numberOfPages = $inputSource->getPageCount();
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
filename = input_source.filename
is_pdf = input_source.pdf?
number_of_pages = input_source.page_count
```
{% endtab %}

{% tab title="Java" %}
```java
String filename = inputSource.getFilename();
boolean isPdf = inputSource.isPdf();
int numberOfPages = inputSource.getPageCount();
```
{% endtab %}

{% tab title=".NET" %}
```csharp
string filename = inputSource.Filename;
bool isPdf = inputSource.IsPdf();
int numberOfPages = inputSource.GetPageCount();
```
{% endtab %}
{% endtabs %}

## Adjust the Source File

Optionally make changes and adjustments to the source file before sending.

{% hint style="info" %}
All file adjustments are applied in-memory to the source file instance.

If loaded from disk, the original file is not modified.
{% endhint %}

### Fix PDF Headers

In some cases, PDFs will have corrupt or invalid headers.\
These files will return a 4xx HTTP error as the server will be unable to process them.

You can try to fix the headers using the provided functions.

**Note:** this feature is not yet available for all languages.

{% include "../../.gitbook/includes/code-samples-input-source.md" %}

{% tabs %}
{% tab title="Python" %}
```python
input_source.fix_pdf()
```
{% endtab %}

{% tab title="PHP" %}
```php
$inputSource->fixPDF();
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
input_source.fix_pdf!
```
{% endtab %}
{% endtabs %}

### Compress Files

There is no need to send excessively large files to the Mindee API.

Unfortunately, many modern smartphones can take very high resolution images.

We provide a way to compress images before sending to the API.

{% include "../../.gitbook/includes/code-samples-input-source.md" %}

{% tabs %}
{% tab title="Python" %}
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
Basic usage is very simple, and can be applied to both images and PDFs:

```typescript
await inputSource.compress(85);
```

For images, you can also set a maximum height and/or width.\
The aspect ratio will always be preserved.

For example to compress and resize to no greater than 1920x1920 pixels:

```typescript
await inputSource.compress(85, 1920, 1920);
```
{% endtab %}

{% tab title="PHP" %}
Basic usage is very simple, and can be applied to both images and PDFs:

```php
$inputSource->compress(quality: 85);
```

For images, you can also set a maximum height and/or width.\
The aspect ratio will always be preserved.

For example to compress and resize to no greater than 1920x1920 pixels:

```php
$inputSource->compress(
    quality: 85, maxWidth: 1920, maxHeight: 1920
);
```
{% endtab %}

{% tab title="Ruby" %}
Basic usage is very simple, and can be applied to both images and PDFs:

```ruby
input_source.compress!(quality:85)
```

For images, you can also set a maximum height and/or width. The aspect ratio will always be preserved.\
For example to compress and resize to no greater than 1920x1920 pixels:

```ruby
input_source.compress!(
    quality:85, max_width:1920, max_height:1920
)
```
{% endtab %}

{% tab title="Java" %}
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

### Manipulate PDF Pages

In some cases, PDFs will have some superfluous pages present.

For example a cover page or terms and conditions which are not useful to the desired data extraction.

These extra pages count towards your billing and slow down processing.

It is therefore in your best interest to remove them before sending.

**Parameters:**

* "Page Indexes" is required and is a list of 0-based page indexes.\
  Use negative values to specify indexes starting from the end, i.e. `-1` for the last page.
* "Operation" specifies whether to keep only specified pages or remove specified pages.\
  One of "Keep Only" or "Remove".
* "On Min Pages" is optional and specifies the minimum number of pages a document must have for the operation to take place. The value of `0` means any number of pages.

Exact naming of parameters will depend on the language.

{% include "../../.gitbook/includes/code-samples-input-source.md" %}

{% tabs %}
{% tab title="Python" %}
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
```typescript
// Set the options as follows:
// For all documents, keep only the first page
const pageOptions: mindee.PageOptions = {
  operation: mindee.PageOptionsOperation.KeepOnly,
  pageIndexes: [0],
};

// Apply in-memory
await inputSource.applyPageOptions(pageOptions);
```

Some other examples:

```typescript
// Only for documents having 3 or more pages:
// Keep only these pages: first, penultimate, last
const pageOptions: mindee.PageOptions = {
  operation: mindee.PageOptionsOperation.KeepOnly,
  onMinPages: 3,
  pageIndexes: [0, -2, -1],
};

// For all documents:
// Remove the first page
const pageOptions: mindee.PageOptions = {
  operation: mindee.PageOptionsOperation.Remove,
  pageIndexes: [0],
};

// Only for documents having 10 or more pages:
// Remove the first 5 pages
const pageOptions: mindee.PageOptions = {
  operation: mindee.PageOptionsOperation.Remove,
  onMinPages: 10,
  pageIndexes: [0, 1, 2, 3, 4],
};
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mindee\Input\PageOptions;
use const Mindee\Input\KEEP_ONLY;

// Set the options as follows:
// For all documents, keep only the first page
$pageOptions = new PageOptions(
    pageIndexes: [0],
    operation: KEEP_ONLY
);

// Apply in-memory
$inputSource->applyPageOptions($pageOptions);
```

Some other examples:

```php
use Mindee\Input\PageOptions;
use const Mindee\Input\KEEP_ONLY;
use const Mindee\Input\REMOVE;

// Only for documents having 3 or more pages:
// Keep only these pages: first, penultimate, last
$pageOptions = new PageOptions(
    pageIndexes: [0, -2, -1],
    operation: KEEP_ONLY,
    onMinPage: 3
);

// For all documents:
// Remove the first page
$pageOptions = new PageOptions(
    pageIndexes: [0],
    operation: REMOVE
);

// Only for documents having 10 or more pages:
// Remove the first 5 pages
$pageOptions = new PageOptions(
    pageIndexes: [0, 1, 2, 3, 4],
    operation: REMOVE,
    onMinPage: 10
);
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
# Set the options as follows:
# For all documents, keep only the first page
page_options = Mindee::PageOptions.new(
    operation: :KEEP_ONLY,
    page_indexes: [0],
)

# Apply in-memory
input_source.apply_page_options(page_options)
```

Note: the name is `apply_page_options` instead of `apply_page_options!` even though the operation is in-place, this to harmonize with the other client libraries.

Some other examples:

```ruby
# Only for documents having 3 or more pages:
# Keep only these pages: first, penultimate, last
Mindee::PageOptions.new(
    operation: :KEEP_ONLY,
    on_min_pages: 3,
    page_indexes: [0, -2, -1],
)

# For all documents:
# Remove the first page
Mindee::PageOptions.new(
    operation: :REMOVE,
    page_indexes: [0],
)

# Only for documents having 10 or more pages:
# Remove the first 5 pages
Mindee::PageOptions.new(
    operation: :REMOVE,
    on_min_pages: 10,
    page_indexes: array[0..4]
)
```
{% endtab %}

{% tab title="Java" %}
```java
import com.mindee.input.PageOptions;
import com.mindee.input.PageOptionsOperation;

// Set the options as follows:
// For all documents, keep only the first page
PageOptions pageOptions = new PageOptions.Builder()
    .pageIndexes(new Integer[]{ 0 })
    .operation(PageOptionsOperation.KEEP_ONLY)
    .build();
```

Some other examples:

```java
import com.mindee.input.PageOptions;
import com.mindee.input.PageOptionsOperation;

// Only for documents having 3 or more pages:
// Keep only these pages: first, penultimate, last
PageOptions pageOptions = new PageOptions.Builder()
    .pageIndexes(new Integer[]{ 0, -2, -1 })
    .operation(PageOptionsOperation.KEEP_ONLY)
    .onMinPages(3)
    .build();

// For all documents:
// Remove the first page
PageOptions pageOptions = new PageOptions.Builder()
    .pageIndexes(new Integer[]{ 0 })
    .operation(PageOptionsOperation.REMOVE)
    .build();

// Only for documents having 10 or more pages:
// Remove the first 5 pages
PageOptions pageOptions = new PageOptions.Builder()
    .pageIndexes(new Integer[]{ 0, 1, 2, 3, 4 })
    .operation(PageOptionsOperation.REMOVE)
    .onMinPages(10)
    .build();
```
{% endtab %}

{% tab title=".NET" %}
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

Now that your file is ready, you'll want to send it to the Mindee servers for processing.

Head on over to the [#send-for-processing](send-a-file-or-url.md#send-for-processing "mention") section for details on the next step.
