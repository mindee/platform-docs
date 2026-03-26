---
description: >-
  Reference documentation on sending files or URLs for processing using Mindee
  client libraries.
icon: paper-plane
---

# Send a File or URL

{% include "../../.gitbook/includes/this-is-reference-documenta....md" %}

## Requirements

You'll need to have your Mindee client configured correctly as described in the [configure-the-client.md](configure-the-client.md "mention") section.

Both the Client and the Product Parameters are required.

## Overview

You can send either a local file or an URL to Mindee servers for processing.

The source has no impact on server-side processing nor on the result.

A local file can be manipulated and adjusted before sending, as described in the [#adjust-the-source-file](load-and-adjust-a-file.md#adjust-the-source-file "mention") section.

The contents of a URL **cannot** be manipulated locally.\
You'll need to download it to the local machine if you wish to adjust the file in any way before sending.

## Load for Sending

There's no difference between sending a file or an URL, both are considered valid Input Sources.

### Use a File

You'll need a Local Input Source as described in the [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention") section.

### Use an URL

You'll need a URL Input Source as described in the [load-an-url.md](load-an-url.md "mention") section.

## Send with Polling

Send a document using [polling](../polling-for-results.md), this is the simplest way to get started.

The client library will POST the request for you, and then automatically poll the API.

### Polling Configuration

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

# Use only if having timeout issues.
polling_options=PollingOptions(
    # Initial delay before the first polling attempt.
    initial_delay_sec=3,
    # Delay between each polling attempt.
    delay_sec=1.5,
    # Total number of polling attempts.
    max_retries=80,
)

inference_params = InferenceParameters(
    # ID of the model, required.
    model_id="MY_MODEL_ID",
    
    # Set only if having timeout issues.
    # polling_options=polling_options,

    # ... any other options ...
)
```
{% endtab %}

{% tab title="Node.js" %}
When polling you really only need to set the `modelId` .

```typescript
const productParams = {modelId: "MY_MODEL_ID"};
```

You can also set the various polling parameters.\
However, **we do not recommend** setting this option unless you are encountering timeout problems.

```typescript
// Optional, set only if having timeout issues.
const pollingOptions = {
  // Initial delay before the first polling attempt.
  initialDelaySec: 3.0,
  // Delay between each polling attempt.
  delaySec: 1.5,
  // Total number of polling attempts.
  maxRetries: 80,
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
inference_params = { model_id: "MY_MODEL_ID" }
```

You can also set the various polling parameters.\
However, **we do not recommend** setting this option unless you are encountering timeout problems.

```ruby
require 'mindee'

inference_params = {
  # ID of the model, required.
  model_id: 'MY_MODEL_ID',

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
}
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
    // ID of the model, required.
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
            // complete the polling builder
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
    // ID of the model, required.
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

### Polling Method Call

{% include "../../.gitbook/includes/input-source-requirements.md" %}

{% tabs %}
{% tab title="Python" %}
The `mindee_client`, created in [configure-the-client.md](configure-the-client.md "mention").

Use the `enqueue_and_get_result` method.

```python
response = mindee_client.enqueue_and_get_result(
    InferenceResponse,
    input_source,
    params,
)

# To easily test which data were extracted,
# simply print an RST representation of the inference
print(response.inference)
```
{% endtab %}

{% tab title="Node.js" %}
The `mindeeClient`, created in [configure-the-client.md](configure-the-client.md "mention").

Use the `enqueueAndGetResult` method:

```typescript
const response = mindeeClient.enqueueAndGetResult(
  mindee.product.Extraction,
  inputSource,
  inferenceParams,
  // optional, set only if having timeout issues.
  // pollingOptions,
);

// Handle the response Promise
response.then((resp) => {
  // To easily test which data were extracted,
  // simply print an RST representation of the inference
  console.log(resp.inference.toString());
});
```
{% endtab %}

{% tab title="PHP" %}
The `$mindeeClient` , created in [configure-the-client.md](configure-the-client.md "mention").

Use the `enqueueAndGetInference` method:

```php
$response = $mindeeClient->enqueueAndGetInference(
    $inputSource,
    $inferenceParams
);

// To easily test which data were extracted,
// simply print an RST representation of the inference
echo strval($response->inference);
```
{% endtab %}

{% tab title="Ruby" %}
The `mindee_client`, created in [configure-the-client.md](configure-the-client.md "mention").

Use the `enqueue_and_get_result` method.

```ruby
response = mindee_client.enqueue_and_get_result(
  Mindee::V2::Product::Extraction::Extraction,
  input_source,
  inference_params
)

# To easily test which data were extracted,
# simply print an RST representation of the inference
puts response.inference
```
{% endtab %}

{% tab title="Java" %}
The `mindeeClient`, created in [configure-the-client.md](configure-the-client.md "mention").

Use the `enqueueAndGetInference` method:

```java
InferenceResponse response = mindeeClient.enqueueAndGetInference(
    inputSource, inferenceParams
);

// To easily test which data were extracted,
// simply print an RST representation of the inference
System.out.println(response.getInference().toString());
```
{% endtab %}

{% tab title=".NET" %}
The `mindeeClient`, created in [configure-the-client.md](configure-the-client.md "mention").

Use the `EnqueueAndGetInferenceAsync` method:

```csharp
var response = await mindeeClient.EnqueueAndGetInferenceAsync(
    inputSource, inferenceParams);

// To easily test which data were extracted,
// simply print an RST representation of the inference
System.Console.WriteLine(response.Inference.ToString());
```
{% endtab %}
{% endtabs %}

## Send with Webhook

Send a document using [webhooks](../webhooks.md), this is recommended for production use, in particular for high volume.

{% include "../../.gitbook/includes/input-source-requirements.md" %}

### Webhook Configuration

The client library will POST the request to your Web server, as configured by your webhook endpoint.

For more information on webhooks, take a look at the [webhooks.md](../webhooks.md "mention") page.

When using a webhook, you'll need to set the model ID and the webhook ID(s) to use.

{% tabs %}
{% tab title="Python" %}
```python
inference_params = InferenceParameters(
    # ID of the model, required.
    model_id="MY_MODEL_ID",
    
    # Add any number of webhook IDs here.
    webhook_ids=["ENDPOINT_1_UUID"],
    
    # ... any other options ...
)
```
{% endtab %}

{% tab title="Node.js" %}
```typescript
const productParams = {
  // ID of the model, required.
  modelId: "MY_MODEL_ID",

  // Add any number of webhook IDs here.
  webhookIds: ["ENDPOINT_1_UUID"],

  // ... any other options ...
};
```
{% endtab %}

{% tab title="PHP" %}
```php
$inferenceParams = new InferenceParameters(
    // ID of the model, required.
    modelId: "MY_MODEL_ID",
    
    // Add any number of webhook IDs here.
    // Note: PHP 8.1 only allows a single ID to be passed.
    webhooksIds: array("ENDPOINT_1_UUID"),

    // ... any other options ...
);
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
inference_params = {
  # ID of the model, required.
  model_id: 'MY_MODEL_ID',

  # Add any number of webhook IDs here.
  webhook_ids: ["ENDPOINT_1_UUID"],

  # ... any other options ...
}
```
{% endtab %}

{% tab title="Java" %}
```java
InferenceParameters params = InferenceParameters
    // ID of the model, required.
    .builder("MY_MODEL_ID")
    
    // Add any number of webhook IDs here.
    .webhookIds(new String[]{"ENDPOINT_1_UUID"})
    
    // ... any other options ...
    
    .build();
```
{% endtab %}

{% tab title=".NET" %}
```csharp
var inferenceParams = new InferenceParameters(
    // ID of the model, required.
    modelId: "MY_MODEL_ID"
    
    // Add any number of webhook IDs here.
    , webhookIds: new List<string>{ "ENDPOINT_1_UUID" }
    
    // ... any other options ...
);
```
{% endtab %}
{% endtabs %}

### Webhook Method Call

You can specify any number of webhook endpoint IDs, each will be sent the payload.

{% tabs %}
{% tab title="Python" %}
The `mindee_client`, created in [#initialize-the-mindee-client](configure-the-client.md#initialize-the-mindee-client "mention").

Use the `enqueue_inference` method:

```python
response = mindee_client.enqueue_inference(
    input_source, inference_params
)

# You should save the job ID for your records/debugging
print(response.job.id)

# If you set an `alias`, you can verify it was taken into account
print(response.job.alias)
```

**Note:** You can use both methods!

First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `enqueue_and_get_result` .\
You'll get the response via polling and webhooks will be sent as well.
{% endtab %}

{% tab title="Node.js" %}
The `mindeeClient`, created in [#initialize-the-mindee-client](configure-the-client.md#initialize-the-mindee-client "mention").

Use the `enqueue` method:

```typescript
const response = await mindeeClient.enqueue(
  mindee.product.Extraction,
  inputSource,
  productParams
);

// You should save the job ID for your records/debugging
console.log(response.job.id);

// If you set an `alias`, you can verify it was taken into account
console.log(response.job.alias);
```

**Note:** You can use both methods!

First, make sure you've added a webhook ID to the `productParams` object.\
Then, call `enqueueAndGetResult` and `await` the promise.\
You'll get the response via polling and webhooks will be sent as well.
{% endtab %}

{% tab title="PHP" %}
The `$mindeeClient`, created in [#initialize-the-mindee-client](configure-the-client.md#initialize-the-mindee-client "mention").

Use the `enqueueInference` method:

```php
$response = $mindeeClient->enqueueInference(
    $inputSource,
    $inferenceParams
);

// You should save the job ID for your records/debugging
echo strval($response->job->id);

// If you set an `alias`, you can verify it was taken into account
echo strval($response->job->alias);
```

**Note:** You can also use both methods!

First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `enqueueAndGetInferenceAsync`.\
You'll get the response via polling and webhooks will be sent as well.
{% endtab %}

{% tab title="Ruby" %}
The `mindee_client`, created in [#initialize-the-mindee-client](configure-the-client.md#initialize-the-mindee-client "mention").

Use the `enqueue` method:

```ruby
response = mindee_client.enqueue(
    Mindee::V2::Product::Extraction::Extraction,
    input_source, inference_params
)

# You should save the job ID for your records/debugging
puts response.job.id

# If you set an `alias`, you can verify it was taken into account
puts response.job.alias
```

**Note:** You can use both methods!

First, make sure you've added a webhook ID to the `inference_params` hash.\
Then, call `enqueue_and_get_result` .\
You'll get the response via polling and webhooks will be sent as well.
{% endtab %}

{% tab title="Java" %}
The `mindeeClient`, created in [#initialize-the-mindee-client](configure-the-client.md#initialize-the-mindee-client "mention").

Use the `enqueueInference` method:

```java
JobResponse response = mindeeClient.enqueueInference(
    inputSource, inferenceParams
);

// You should save the job ID for your records/debugging
System.out.println(response.getJob().getId());

// If you set an `alias`, you can verify it was taken into account
System.out.println(response.getJob().getAlias());
```

**Note:** You can use both methods!

First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `enqueueAndGetInference` and handle the promise.\
You'll get the response via polling and webhooks will be sent as well.
{% endtab %}

{% tab title=".NET" %}
The `mindeeClient`, created in [#initialize-the-mindee-client](configure-the-client.md#initialize-the-mindee-client "mention").

Use `EnqueueInferenceAsync` method:

```csharp
var response = mindeeClient.EnqueueInferenceAsync(
    inputSource, inferenceParams
);

// You should save the job ID for your records/debugging
System.Console.WriteLine(response.Job.Id);

// If you set an `alias`, you can verify it was taken into account
System.Console.WriteLine(response.Job.Alias);
```

**Note:** You can also use both methods!

First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `EnqueueAndGetInferenceAsync`.\
You'll get the response via polling and webhooks will be sent as well.
{% endtab %}
{% endtabs %}

## Get Processing Status

Accessing processing information is done using the `Job` object and related method calls.

If you are using webhooks, we highly recommend storing the job's ID so you can retrieve this information for debugging purposes.

You can access:

* overall processing status
* detailed errors, if any
* status for each webhook sent
* creation and completion times
* etc

{% tabs %}
{% tab title="Python" %}
```python
# from `enqueue` method (typically for webhook)
job_id = response.job.id

# from `enqueue_and_get_result` method (typically for polling)
# job_id = response.inference.job.id

job_response = mindee_client.get_job(job_id)

# some metadata, check your IDE for all available attributes
print(job_response.job.status)
print(job_response.job.created_at)
print(job_response.job.completed_at)

# check webhooks
for webhook in job_response.job.webhooks:
    print(f"{webhook.id} status: {webhook.status}")
```
{% endtab %}

{% tab title="Node.js" %}
```typescript
// from `enqueue` method (typically for webhook)
const jobId = response.job.id;

// from `enqueueAndGetResult` method (typically for polling)
//const jobId = response.inference.job.id;

const jobResponse = await mindeeClient.getJob(jobId);

// some metadata, check your IDE for all available attributes
console.log(jobResponse.job.status);
console.log(jobResponse.job.createdAt);
console.log(jobResponse.job.completedAt);

// check webhooks
jobResponse.job.webhooks.forEach((webhook) => {
  console.log(`${webhook.id} status: ${webhook.status}`);
});
```
{% endtab %}

{% tab title="PHP" %}
```php
// from `enqueueInference` method (typically for webhook)
$jobId = $response->job->id;

// from `enqueueAndGetInference` method (typically for polling)
// $jobId = $response->inference->job->id;

$jobResponse = $mindeeClient->getJob($jobId);

// some metadata, check your IDE for all available attributes
echo $jobResponse->job->status;
echo $jobResponse->job->createdAt->format('Y-m-d H:i:s');
echo $jobResponse->job->completedAt?->format('Y-m-d H:i:s');

// check webhooks
foreach ($jobResponse->job->webhooks as $webhook) {
    echo "{$webhook->id} status: {$webhook->status}";
}
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
# from `enqueue` method (typically for webhook)
job_id = response.job.id

# from `enqueue_and_get_result` method (typically for polling)
# job_id = response.inference.job.id

job_response = mindee_client.get_job(job_id)

# some metadata, check your IDE for all available attributes
puts job_response.job.status
puts job_response.job.created_at
puts job_response.job.completed_at

# check webhooks
job_response.job.webhooks.each do |webhook|
  puts "#{webhook.id} status: #{webhook.status}"
end
```
{% endtab %}

{% tab title="Java" %}
```java
// from `enqueueInference` method (typically for webhook)
String jobId = response.getJob().getId();

// from `enqueueAndGetInference` method (typically for polling)
// String jobId = response.getInference().getJob().getId();

JobResponse jobResponse = mindeeClient.getJob(jobId);

// some metadata, check your IDE for all available attributes
Job job = jobResponse.getJob();
System.out.println(job.getStatus());
System.out.println(job.getCreatedAt());
System.out.println(job.getCompletedAt());

// check webhooks
job.getWebhooks().forEach(webhook ->
    System.out.println(webhook.getId() + " status: " + webhook.getStatus())
);
```
{% endtab %}

{% tab title=".NET" %}
```csharp
// from `EnqueueInferenceAsync` method (typically for webhook)
var jobId = response.Job.Id;

// from `EnqueueAndGetInferenceAsync` method (typically for polling)
// var jobId = response.Inference.Job.Id;

var jobResponse = await mindeeClientV2.GetJobAsync(jobId);

// some metadata, check your IDE for all available attributes
Console.WriteLine(jobResponse.Job.Status);
Console.WriteLine(jobResponse.Job.CreatedAt);
Console.WriteLine(jobResponse.Job.CompletedAt);

// check webhooks
foreach (var webhook in jobResponse.Job.Webhooks)
{
    Console.WriteLine($"{webhook.Id} status: {webhook.Status}");
}
```
{% endtab %}
{% endtabs %}

## Process the Result

Now that your file or URL has been handled by the Mindee servers, you'll want to process the results and use them in your application.

Head on over to the [process-the-response.md](process-the-response.md "mention") section for details on the next step.
