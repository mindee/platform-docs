---
description: Reference documentation on loading URLs using Mindee client libraries.
icon: globe-pointer
---

# Load an URL

{% include "../../.gitbook/includes/this-is-reference-documenta....md" %}

## Overview

Overall, the steps to sending an URL are:

1. Load the URL, **this does not download anything locally**.
2. _Optional_: adjust the source file before sending.
3. Use the Mindee client instance to send the file.

## Requirements

In most cases you'll be loading a source file for use in the Mindee Client, take a look at the [configure-the-client.md](configure-the-client.md "mention") section for more info.

However, you don't actually need the client initialized to use these features, only the client library installed.

{% include "../../.gitbook/includes/file-url-technical-limitation.md" %}

## Load the URL

{% tabs %}
{% tab title="Python" %}
Use the `URLInputSource` class.

```python
from mindee import UrlInputSource

input_source = UrlInputSource(
    "https://example.com/file.ext"
)
```
{% endtab %}

{% tab title="Node.js" %}
Use the `URLInput` class.

```typescript
const inputSource = new mindee.UrlInput({
  url: "https://example.com/file.ext"
});
```
{% endtab %}

{% tab title="PHP" %}
Use the `URLInputSource` class.

```php
use Mindee\Input\URLInputSource;

$inputSource = new URLInputSource(
  url: "https://example.com/file.ext"
);
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'mindee'

input_source = Mindee::Input::Source::URLInputSource.new(
  'https://example.com/file.ext'
)
```
{% endtab %}

{% tab title="Java" %}
Use the `URLInputSource` class.

```java
import com.mindee.input.URLInputSource;

URLInputSource inputSource = URLInputSource
    .builder("https://example.com/file.ext")
    .build();
```
{% endtab %}

{% tab title=".NET" %}
Use the `URLInputSource` class.

```csharp
var inputSource = new UrlInputSource(
    "https://example.com/file.ext");
```
{% endtab %}
{% endtabs %}

## Send the URL

Now that your URL is ready, you'll want to send it to the Mindee servers for processing.

Head on over to the [#send-for-processing](send-a-file-or-url.md#send-for-processing "mention") section for details on the next step.
