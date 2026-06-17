---
description: Reference documentation on preparing and configuring the Mindee client.
icon: wrench
---

# Client Configuration

{% include "../../.gitbook/includes/this-is-reference-documenta....md" %}

## Before You Start

You'll need to have one of the [official Mindee SDKs](./) installed.

You'll also need to use one of your [API keys](../api-keys.md) and have at least one [Model](../../models/models-overview.md) configured.

The client works for all model types.

## Initialize the Mindee Client

Before sending any files to the Mindee servers for processing, you'll need to initialize your client.

This should be the first step in your code. It will determine which organization is used to make the calls.

You should reuse the same client instance for all calls of the same organization.

The client instance is thread-safe in applicable languages.

{% tabs %}
{% tab title="Python" %}
First import the needed classes:

```python
from mindee import (
    ClientV2,
    InferenceParameters,
    InferenceResponse,
    PathInput,  # for loading files from disk
)
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

{% tab title="Node.js" %}
First import the needed classes. We recommend using ES Modules.

```typescript
import * as mindee from "mindee";
// If you're on CommonJS:
// const mindee = require("mindee");
```

For the API key, you can pass it directly to the client.\
This is useful for quick testing.

```typescript
const apiKey = "MY_API_KEY";

const mindeeClient = new mindee.Client({ apiKey: apiKey });
```

Instead of passing the key directly, you can also set the following environment variable:

`MINDEE_V2_API_KEY`

This is recommended for production use.\
In this way there is no need to pass the `apiKey` argument when initializing the client.

```typescript
const mindeeClient = new mindee.Client();
```

**Advanced Usage**

internally, [undici](https://undici.nodejs.org/) is used for making HTTP calls, and when the client is initialized `getGlobalDispatcher` is called.

**This is perfectly fine for the vast majority of cases:**\
If you set a custom Agent as the global dispatcher, Mindee will use it.

In the rare case where you need a specific dispatcher for Mindee, you can set it as follows:

```javascript
import { Agent, interceptors } from "undici";

// Init the custom Dispatcher
// REPLACE THE LINE BELOW WITH YOUR CODE - this example will NOT work!
const myDispatcher = new Agent().compose( ... );

const mindeeClient = new mindee.Client({
  // Don't set if using an environment variable
  apiKey: apiKey,

  // Activates verbose logging - disable in production!
  debug: true,

  // Pass the custom dispatcher to the Mindee client
  dispatcher: myDispatcher,
});
```
{% endtab %}

{% tab title="PHP" %}
First import the needed classes:

```php
use Mindee\ClientV2;
use Mindee\Input\InferenceParameters;
use Mindee\Error\MindeeException;
```

For the API key, you can pass it directly to the client.\
This is useful for quick testing.

```php
$apiKey = "MY_API_KEY";

$mindeeClient = new ClientV2($apiKey);
```

Instead of passing the key directly, you can also set the following environment variable:

`MINDEE_V2_API_KEY`

This is recommended for production use.\
In this way there is no need to pass the `$apiKey` when initializing the client.

```php
$mindeeClient = new ClientV2($apiKey);
```
{% endtab %}

{% tab title="Ruby" %}
First import the Mindee package:

```ruby
require 'mindee'
```

For the API key, you can pass it directly to the client.\
This is useful for quick testing.

```ruby
api_key = 'MY_API_KEY'
mindee_client = Mindee::ClientV2.new(api_key: api_key)
```

Instead of passing the key directly, you can also set the following environment variable:

`MINDEE_V2_API_KEY`

This is recommended for production use.\
In this way there is no need to pass the `api_key` when initializing the client.

```ruby
mindee_client = Mindee::ClientV2.new()
```
{% endtab %}

{% tab title="Java" %}
First import the needed classes:

```java
import com.mindee.MindeeClientV2;
import com.mindee.InferenceParameters;
```

For the API key, you can pass it directly to the client.\
This is useful for quick testing.

```java
String apiKey = "MY_API_KEY";

MindeeClientV2 mindeeClient = new MindeeClientV2(apiKey);
```

Instead of passing the key directly, you can also set the following environment variable:

`MINDEE_V2_API_KEY`

This is recommended for production use.\
In this way there is no need to pass the `apiKey` argument when initializing the client.

```java
MindeeClientV2 mindeeClient = new MindeeClientV2();
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
