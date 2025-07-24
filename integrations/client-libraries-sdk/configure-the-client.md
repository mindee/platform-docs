---
description: Prepare and configure the Mindee client.
---

# Configure the Client

## Requirements

Before proceeding you'll need to have one of the [official Mindee client libraries](./) installed.

## Overview

This section will go into detail for each step, and list all possible options.\
It is reference documentation.

{% hint style="info" %}
**If you want just the quick TL;DR:**

* Take a look at the [integrating-mindee.md](../../getting-started/integrating-mindee.md "mention") page.
* Use the **search bar** at the top to ask our documentation AI to write code samples for you.
{% endhint %}

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
    alias="MY_ALIAS",
)
```
{% endtab %}

{% tab title="Node.js" %}
Only the `modelId` is required.

```typescript
const params = {
  // ID of the model, required.
  modelId: "MY_MODEL_ID",

  // Options:

  // If set to `true`, will enable Retrieval-Augmented Generation.
  rag: false,

  // Use an alias to link the file to your own DB.
  // If empty, no alias will be used.
  alias: "MY_ALIAS"
};
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

{% tab title="Node.js" %}
When polling you really only need to set the `modelId` .

```typescript
const params = {modelId: "MY_MODEL_ID"};
```

You can also set the various polling parameters.\
However, **we do not recommend** setting this option unless you are encountering timeout problems.

```typescript
const params = {
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

{% tab title="Node.js" %}
When using a webhook, you'll need to set the `modelId` and which webhook(s) to use.

```typescript
const params = {
  modelId: "MY_MODEL_ID",
  webhookIds: ["ENDPOINT_1_UUID"],

  // ... any other options ...
};
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

## Next Steps

Now that everything is ready to, it's time to send your files to the Mindee servers.

Head on over to the [send-a-file.md](send-a-file.md "mention") page for details on the next step.
