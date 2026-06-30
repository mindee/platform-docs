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
from mindee.v2 import Client
```

For the API key, you can pass it directly to the client.\
This is useful for quick testing.

```python
api_key = "MY_API_KEY"

mindee_client = Client(api_key)
```

Instead of passing the key directly, you can also set the following environment variable:

`MINDEE_V2_API_KEY`

This is recommended for production use.\
In this way there is no need to pass the `api_key` when initializing the client.

```python
mindee_client = Client()
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
If you set a custom Agent as your global dispatcher, Mindee will use it for all calls.

In some rare cases you may need a specific dispatcher for Mindee, different from your global dispatcher. You can set a custom dispatcher as follows:

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

The Mindee client will then use the given dispatcher for **all calls**.

This is the recommended setup when needing to pass extra parameters or configuration options, for example when using the Client behind a proxy.

When running in some serverless environments like Vercel, _sometimes_ (this depends on your exact setup) there are errors caused by freezing/thawing of the process. These can be avoided using Undici's `RetryAgent` class:

```javascript
const myDispatcher = new RetryAgent(new Agent(), {
  maxRetries: 3,
  errorCodes: ["UND_ERR_SOCKET", "UND_ERR_CONNECT_TIMEOUT", "ECONNRESET"],
});
```
{% endtab %}

{% tab title="PHP" %}
First import the needed classes:

```php
use Mindee\V2\Client;
```

For the API key, you can pass it directly to the client.\
This is useful for quick testing.

```php
$apiKey = "MY_API_KEY";

$mindeeClient = new Client($apiKey);
```

Instead of passing the key directly, you can also set the following environment variable:

`MINDEE_V2_API_KEY`

This is recommended for production use.\
In this way there is no need to pass the `$apiKey` when initializing the client.

```php
$mindeeClient = new Client($apiKey);
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
mindee_client = Mindee::V2::Client.new(api_key: api_key)
```

Instead of passing the key directly, you can also set the following environment variable:

`MINDEE_V2_API_KEY`

This is recommended for production use.\
In this way there is no need to pass the `api_key` when initializing the client.

```ruby
mindee_client = Mindee::V2::Client.new()
```
{% endtab %}

{% tab title="Java" %}
First import the needed classes:

```java
import com.mindee.v2.MindeeClient;
```

For the API key, you can pass it directly to the client.\
This is useful for quick testing.

```java
String apiKey = "MY_API_KEY";

MindeeClient mindeeClient = new MindeeClient(apiKey);
```

Instead of passing the key directly, you can also set the following environment variable:

`MINDEE_V2_API_KEY`

This is recommended for production use.\
In this way there is no need to pass the `apiKey` argument when initializing the client.

```java
MindeeClient mindeeClient = new MindeeClient();
```
{% endtab %}

{% tab title=".NET" %}
First add the required namespaces.

```csharp
using Mindee.V2;
```

For the API key, you can pass it directly to the client.\
This is useful for quick testing.

```csharp
string apiKey = "MY_API_KEY";

Client mindeeClient = new Client(apiKey);
```

Instead of passing the key directly, you can also set the following environment variable:

`MindeeV2__ApiKey`

This is recommended for production use.\
In this way there is no need to pass the `apiKey` argument when initializing the client.

```csharp
Client mindeeClient = new Client();
```
{% endtab %}
{% endtabs %}
