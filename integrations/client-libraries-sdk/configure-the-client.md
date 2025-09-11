---
description: Reference documentation on preparing and configuring the Mindee client.
icon: wrench
---

# Configure the Client

{% include "../../.gitbook/includes/this-is-reference-documenta....md" %}

## Requirements

Before proceeding you'll need to have one of the [official Mindee client libraries](./) installed.

You'll also need to use one of your [#api-keys](../api-overview.md#api-keys "mention") and one or several [Models](../../models/models-overview.md) configured.

## Overview

Before sending any files to the Mindee servers for processing, you'll need to initialize your client and set inference options.

These settings will determine how your files are sent, including any extra options, and how you want to process the result.

## Initialize the Mindee Client

This should be the first step in your code. It will determine which organization is used to make the calls.

You should reuse the same client instance for all calls of the same organization.

The client instance is thread-safe where applicable.

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

{% tab title="Node.js" %}
First import the needed classes. We recommend using TypeScript.

```typescript
const mindee = require("mindee");
// for TS or modules:
// import * as mindee from "mindee";
```

For the API key, you can pass it directly to the client.\
This is useful for quick testing.

```typescript
const apiKey = "MY_API_KEY";

const mindeeClient = new mindee.ClientV2({ apiKey: apiKey });
```

Instead of passing the key directly, you can also set the following environment variable:

`MINDEE_V2_API_KEY`

This is recommended for production use.\
In this way there is no need to pass the `apiKey` argument when initializing the client.

```typescript
const mindeeClient = new mindee.ClientV2();
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

## Set Inference Parameters

Inference parameters control:

* which model to use
* server-side processing options
* how the results will be returned to you

### Processing Parameters

These are mostly the same parameters as present in the Web API.

Default values for the processing Options can be changed on the platform.\
Any values set here will override the defaults, leave empty to use the default values.

For example: if the polygon feature is enabled on the platform, and polygon is explicitly set to `false` in the parameters ⇒ the polygon feature will not be enabled for the API call.

{% tabs %}
{% tab title="Python" %}
Only the `model_id` is required.

```python
inference_params = InferenceParameters(
    # ID of the model, required.
    model_id="MY_MODEL_ID",
    
    # Use an alias to link the file to your own DB.
    # If empty, no alias will be used.
    alias="MY_ALIAS",
    
    # Options: set to `True` or `False` to override defaults

    # Enhance extraction accuracy with Retrieval-Augmented Generation.
    rag=None,
    # Extract the full text content from the document as strings.
    raw_text=None,
    # Calculate bounding box polygons for all fields.
    polygon=None,
    # Boost the precision and accuracy of all extractions.
    # Calculate confidence scores for all fields.
    confidence=None,
)
```
{% endtab %}

{% tab title="Node.js" %}
Only the `modelId` is required.

```typescript
const inferenceParams = {
  // ID of the model, required.
  modelId: "MY_MODEL_ID",
  
  // Use an alias to link the file to your own DB.
  // If empty, no alias will be used.
  alias: "MY_ALIAS"

  // Options:

  // If set to `true`, will enable Retrieval-Augmented Generation.
  rag: false,
};
```
{% endtab %}

{% tab title="PHP" %}
Only the `modelId` is required.

```php
$inferenceParams = new InferenceParameters(
    // ID of the model, required.
    $modelId,

    // Options: set to `true` or `false` to override defaults

    // Enhance extraction accuracy with Retrieval-Augmented Generation.
    rag: null,
    // Extract the full text content from the document as strings.
    rawText: null,
    // Calculate bounding box polygons for all fields.
    polygon: null,
    // Boost the precision and accuracy of all extractions.
    // Calculate confidence scores for all fields.
    confidence: null
);
```
{% endtab %}

{% tab title="Ruby" %}
Only the `model_id` is required.

```ruby
inference_params = Mindee::Input::InferenceParameters.new(
    # ID of the model, required.
    model_id,
    
    # Use an alias to link the file to your own DB.
    # If empty, no alias will be used.
    file_alias: "MY_ALIAS"

    # Options:

    # If set to `true`, will enable Retrieval-Augmented Generation.
    rag: false,
)
```
{% endtab %}

{% tab title="Java" %}
Only the `modelId` is required.

```java
InferenceParameters params = InferenceParameters
    // ID of the model, required.
    .builder("MY_MODEL_ID")
    
    // Use an alias to link the file to your own DB.
    // If empty, no alias will be used.
    .alias("MY_ALIAS")

    // Options: set to `true` or `false` to override defaults

    // Enhance extraction accuracy with Retrieval-Augmented Generation.
    .rag(null)
    // Extract the full text content from the document as strings.
    .rawText(null)
    // Calculate bounding box polygons for all fields.
    .polygon(null)
    // Boost the precision and accuracy of all extractions.
    // Calculate confidence scores for all fields.
    .confidence(null)

    // complete the builder
    .build();
```
{% endtab %}

{% tab title=".NET" %}
Only the `modelId` is required.

```csharp
var inferenceParams = new InferenceParameters(
    // ID of the model, required.
    modelId: "MY_MODEL_ID"

    // Use an alias to link the file to your own DB.
    // If empty, no alias will be used.
    , alias: "MY_ALIAS"
    
    // Options: set to `true` or `false` to override defaults

    // Enhance extraction accuracy with Retrieval-Augmented Generation.
    , rag: null
    // Extract the full text content from the document as strings.
    , rawText: null
    // Calculate bounding box polygons for all fields.
    , polygon: null
    // Boost the precision and accuracy of all extractions.
    // Calculate confidence scores for all fields.
    , confidence: null
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
inference_params = InferenceParameters(model_id="MY_MODEL_ID")
```

You can also set the various polling parameters.\
However, **we do not recommend** setting this option unless you are encountering timeout problems.

```python
from mindee import PollingOptions

inference_params = InferenceParameters(
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

{% tab title="Node.js" %}
When polling you really only need to set the `modelId` .

```typescript
const inferenceParams = {modelId: "MY_MODEL_ID"};
```

You can also set the various polling parameters.\
However, **we do not recommend** setting this option unless you are encountering timeout problems.

```typescript
const inferenceParams = {
  // ID of the model, required.
  modelId: "MY_MODEL_ID",
  
  // Set only if having timeout issues.
  pollingOptions: {
    // Initial delay before the first polling attempt.
    initialDelaySec: 3.0,
    // Delay between each polling attempt.
    delaySec: 1.5,
    // Total number of polling attempts.
    maxRetries: 80
  }
  // ... any other options ...
}
```
{% endtab %}

{% tab title="PHP" %}
When polling you really only need to set the `modelId` .

```php
$inferenceParams = new InferenceParameters(modelId: "MY_MODEL_ID");
```

You can also set the various polling parameters.\
However, **we do not recommend** setting this option unless you are encountering timeout problems.

```php
use Mindee\Input\PollingOptions;

$inferenceParams = new InferenceParameters(
    // ID of the model, required.
    modelId: "MY_MODEL_ID",
    
    // Set only if having timeout issues.
    pollingOptions: new PollingOptions(
        // Initial delay before the first polling attempt.
        initialDelaySec: 3.0,
        // Delay between each polling attempt.
        delaySec: 1.5,
        // Total number of polling attempts.
        maxRetries: 80,
    ),
    // ... any other options ...
);
```
{% endtab %}

{% tab title="Ruby" %}
When polling you really only need to set the `model_id` .

```ruby
inference_params = Mindee::Input::InferenceParameters.new("MY_MODEL_ID")
```

You can also set the various polling parameters.\
However, **we do not recommend** setting this option unless you are encountering timeout problems.

```ruby
require 'mindee'

inference_params = Mindee::Input::InferenceParameters.new(
  "MY_MODEL_ID",

  # Set only if having timeout issues.
  polling_options: Mindee::Input::PollingOptions.new(
    # Initial delay before the first polling attempt.
    initial_delay_sec: 3,
    # Delay between each polling attempt.
    delay_sec: 1.5,
    # Total number of polling attempts.
    max_retries: 80,
  ),
# ... any other options ...
)
```
{% endtab %}

{% tab title="Java" %}
When polling you really only need to set the `modelId` .

```java
InferenceParameters params = InferenceParameters
        .builder("MY_MODEL_ID")
        .build();
```

You can also set the various polling parameters.\
However, **we do not recommend** setting this option unless you are encountering timeout problems.

```java
InferenceParameters params = InferenceParameters
        .builder("MY_MODEL_ID")
        
        // Set only if having timeout issues.
        .pollingOptions(
            AsyncPollingOptions.builder()
                // Initial delay before the first polling attempt.
                .initialDelaySec(3.0)
                // Delay between each polling attempt.
                .intervalSec(1.5)
                // Total number of polling attempts.
                .maxRetries(80)
                // complete the builder
                .build()
        )
    
        // ... any other options ...
    
        .build();
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

For more information on webhooks, take a look at the [webhooks.md](../webhooks.md "mention") page.

When using a webhook, you'll need to set the model ID and the webhook ID(s) to use.

{% tabs %}
{% tab title="Python" %}
```python
inference_params = InferenceParameters(
    model_id="MY_MODEL_ID",
    webhook_ids=["ENDPOINT_1_UUID"],
    
    # ... any other options ...
)
```
{% endtab %}

{% tab title="Node.js" %}
```typescript
const inferenceParams = {
  modelId: "MY_MODEL_ID",
  webhookIds: ["ENDPOINT_1_UUID"],

  // ... any other options ...
};
```
{% endtab %}

{% tab title="PHP" %}
```php
$inferenceParams = new InferenceParameters(
    modelId: "MY_MODEL_ID",
    webhooksIds: array("ENDPOINT_1_UUID"),

    // ... any other options ...
);
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
inference_params = Mindee::Input::InferenceParameters.new(
  "MY_MODEL_ID",
  webhook_ids: ["ENDPOINT_1_UUID"],

# ... any other options ...
)
```
{% endtab %}

{% tab title="Java" %}
```java
InferenceParameters params = InferenceParameters
    .builder("MY_MODEL_ID")
    .webhookIds(new String[]{"ENDPOINT_1_UUID"})
    
    // ... any other options ...
    
    .build();
```
{% endtab %}

{% tab title=".NET" %}
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

## Next Steps

Now that everything is ready to, it's time to send your files to the Mindee servers.

If you're sending a local file, head on over to the [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention") section for details on the next step.

If you're sending an URL, head on over to the [send-a-file-or-url.md](send-a-file-or-url.md "mention") section.
