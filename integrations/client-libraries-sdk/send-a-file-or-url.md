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

Both the Client and the Inference Parameters are required.

## Overview

You can send either a local file or an URL to Mindee servers for processing.

The source has no impact on server-side processing nor on the result.

A local file can be manipulated and adjusted before sending, as described in the [#adjust-the-source-file](load-and-adjust-a-file.md#adjust-the-source-file "mention") section.

An URL cannot be manipulated locally for obvious reasons.\
You'll need to download it to the local machine if you wish to adjust the file in any way before sending.

## Use a File

You'll need a Local Input Source as described in the [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention") section.

## Use an URL

You'll need a Remote Input Source as described below.

### Requirements

The source URL must adhere to the following rules:

* Secured using TLS (HTTPS).
* Publicly available using only the URL, no authentication _headers_.
* Authentication may be provided in the URL: username/password or token.\
  For example, Amazon S3 signed URLs will work.
* Contents must be a binary file (raw bytes, _not_ base64-encoded).
* No redirections (HTTP 3xx), these will _not_ work.

### Initialize the URL

{% tabs %}
{% tab title="Python" %}
Use the `URLInputSource` class.

```python
from mindee.input import UrlInputSource

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
input_source = Mindee::Input::Source::URLInputSource.new(
  "https://example.com/file.ext"
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

## Send for Processing

There's no difference between sending a file or an URL, both are considered valid Input Sources.

You can send either using polling or webhooks.

### Send with Polling

{% tabs %}
{% tab title="Python" %}
`input_source`  is any valid input source, one of:

* a local source created in [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
* a remote source created in [#use-an-url](send-a-file-or-url.md#use-an-url "mention")

The `mindee_client` and `inference_params` are created in [configure-the-client.md](configure-the-client.md "mention").

Use the `enqueue_and_get_inference` method.

```python
response = mindee_client.enqueue_and_get_inference(
    input_source, inference_params
)

# To easily test which data was extracted,
# simply print an RST representation of the inference
print(response.inference)
```
{% endtab %}

{% tab title="Node.js" %}
`inputSource`  is any valid input source, one of:

* a local source created in [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
* a remote source created in [#use-an-url](send-a-file-or-url.md#use-an-url "mention")

The `mindeeClient` and `inferenceParams` are created in [configure-the-client.md](configure-the-client.md "mention").

Use the `enqueueAndGetInference` method:

```typescript
const response = mindeeClient.enqueueAndGetInference(
  inputSource,
  inferenceParams
);

// Handle the response Promise
response.then((resp) => {
  // To easily test which data was extracted,
  // simply print an RST representation of the inference
  console.log(resp.inference.toString());
});
```
{% endtab %}

{% tab title="PHP" %}
`$inputSource`  is any valid input source, one of:

* a local source created in [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
* a remote source created in [#use-an-url](send-a-file-or-url.md#use-an-url "mention")

The `$mindeeClient` and `$inferenceParams` are created in [configure-the-client.md](configure-the-client.md "mention").

Use the `enqueueAndGetInference` method:

```php
$response = $mindeeClient->enqueueAndGetInference(
    $inputSource,
    $inferenceParams
);

// To easily test which data was extracted,
// simply print an RST representation of the inference
echo strval($response->inference);
```
{% endtab %}

{% tab title="Ruby" %}
`input_source`  is any valid input source, one of:

* a local source created in [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
* a remote source created in [#use-an-url](send-a-file-or-url.md#use-an-url "mention")

The `mindee_client` and `inference_params` are created in [configure-the-client.md](configure-the-client.md "mention").

Use the `enqueue_and_get_inference` method.

```ruby
response = mindee_client.enqueue_and_get_inference(
  input_source,
  inference_params
)

# To easily test which data was extracted,
# simply print an RST representation of the inference
puts response.inference
```
{% endtab %}

{% tab title="Java" %}
`inputSource`  is any valid input source, one of:

* a local source created in [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
* a remote source created in [#use-an-url](send-a-file-or-url.md#use-an-url "mention")

The `mindeeClient` and `inferenceParams` are created in [configure-the-client.md](configure-the-client.md "mention").

Use the `enqueueAndGetInference` method:

```java
InferenceResponse response = mindeeClient.enqueueAndGetInference(
    inputSource, inferenceParams
);

// To easily test which data was extracted,
// simply print an RST representation of the inference
System.out.println(response.getInference().toString());
```
{% endtab %}

{% tab title=".NET" %}
`inputSource`  is any valid input source, one of:

* a local source created in [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
* a remote source created in [#use-an-url](send-a-file-or-url.md#use-an-url "mention")

The `mindeeClient` and `inferenceParams` are created in [configure-the-client.md](configure-the-client.md "mention").

Use the `EnqueueAndGetInferenceAsync` method:

```csharp
var response = await mindeeClient.EnqueueAndGetInferenceAsync(
    inputSource, inferenceParams);

// To easily test which data was extracted,
// simply print an RST representation of the inference
System.Console.WriteLine(response.Inference.ToString());
```
{% endtab %}
{% endtabs %}

### Send with Webhook

Make sure your webhook is configured as detailed here: [#webhook-configuration](configure-the-client.md#webhook-configuration "mention").

{% tabs %}
{% tab title="Python" %}
`input_source`  is any valid input source, one of:

* a local source created in [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
* a remote source created in [#use-an-url](send-a-file-or-url.md#use-an-url "mention")

The `mindee_client` as created in [#initialize-the-mindee-client](configure-the-client.md#initialize-the-mindee-client "mention").

The `inference_params` as created in [#webhook-configuration](configure-the-client.md#webhook-configuration "mention").

Use the `enqueue_inference` method:

```python
response = mindee_client.enqueue_inference(
    input_source, inference_params
)

# You should save the job ID for your records
print(response.job.id)

# If you set an `alias`, you can verify it was taken into account
print(response.job.alias)
```

**Note:** You can use both methods!

First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `enqueue_and_get_inference` .\
You'll get the response via polling and webhooks will be used as well.&#x20;
{% endtab %}

{% tab title="Node.js" %}
`inputSource`  is any valid input source, one of:

* a local source created in [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
* a remote source created in [#use-an-url](send-a-file-or-url.md#use-an-url "mention")

The `mindeeClient` as created in [#initialize-the-mindee-client](configure-the-client.md#initialize-the-mindee-client "mention").

The `inferenceParams` as created in [#webhook-configuration](configure-the-client.md#webhook-configuration "mention").

Use the `enqueueInference` method:

```typescript
const response = mindeeClient.enqueueInference(
  inputSource,
  inferenceParams
);

// Handle the response Promise
response.then((resp) => {
  // You should save the job ID for your records
  console.log(resp.job.id);
  
  // If you set an `alias`, you can verify it was taken into account
  console.log(resp.job.alias);
});
```

**Note:** You can use both methods!

First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `enqueueAndGetInference`  and handle the promise.\
You'll get the response via polling and webhooks will be used as well.&#x20;
{% endtab %}

{% tab title="PHP" %}
`$inputSource`  is any valid input source, one of:

* a local source created in [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
* a remote source created in [#use-an-url](send-a-file-or-url.md#use-an-url "mention")

The `$mindeeClient` as created in [#initialize-the-mindee-client](configure-the-client.md#initialize-the-mindee-client "mention").

The `$inferenceParams` as created in [#webhook-configuration](configure-the-client.md#webhook-configuration "mention").

Use the  `enqueueInference` method:

```php
$response = $mindeeClient->enqueueInference(
    $inputSource,
    $inferenceParams
);

// You should save the job ID for your records
echo strval($response->job->id);

// If you set an `alias`, you can verify it was taken into account
echo strval($response->job->alias);
```

**Note:** You can also use both methods!

First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `enqueueAndGetInferenceAsync`.\
You'll get the response via polling and webhooks will be used as well.
{% endtab %}

{% tab title="Ruby" %}
`input_source`  is any valid input source, one of:

* a local source created in [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
* a remote source created in [#use-an-url](send-a-file-or-url.md#use-an-url "mention")

The `mindee_client` as created in [#initialize-the-mindee-client](configure-the-client.md#initialize-the-mindee-client "mention").

The `inference_params` as created in [#webhook-configuration](configure-the-client.md#webhook-configuration "mention").

Use the `enqueue_inference` method:

```ruby
response = mindee_client.enqueue_inference(
    input_source, inference_params
)

# You should save the job ID for your records
puts response.job.id

# If you set an `alias`, you can verify it was taken into account
puts response.job.alias
```

**Note:** You can use both methods!

First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `enqueue_and_get_inference` .\
You'll get the response via polling and webhooks will be used as well.&#x20;
{% endtab %}

{% tab title="Java" %}
`inputSource`  is any valid input source, one of:

* a local source created in [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
* a remote source created in [#use-an-url](send-a-file-or-url.md#use-an-url "mention")

The The `mindeeClient` as created in [#initialize-the-mindee-client](configure-the-client.md#initialize-the-mindee-client "mention").

The `inferenceParams` as created in [#webhook-configuration](configure-the-client.md#webhook-configuration "mention").

Use the `enqueueInference` method:

```java
JobResponse response = mindeeClient.enqueueInference(
    inputSource, inferenceParams
);

// You should save the job ID for your records
System.out.println(response.getJob().getId());

// If you set an `alias`, you can verify it was taken into account
System.out.println(response.getJob().getAlias());
```

**Note:** You can use both methods!

First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `enqueueAndGetInference`  and handle the promise.\
You'll get the response via polling and webhooks will be used as well.&#x20;
{% endtab %}

{% tab title=".NET" %}
`inputSource`  is any valid input source, one of:

* a local source created in [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
* a remote source created in [#use-an-url](send-a-file-or-url.md#use-an-url "mention")

The `mindeeClient` as created in [#initialize-the-mindee-client](configure-the-client.md#initialize-the-mindee-client "mention").

The `inferenceParams` as created in [#webhook-configuration](configure-the-client.md#webhook-configuration "mention").

Use `EnqueueInferenceAsync` method:

```csharp
var response = mindeeClient.EnqueueInferenceAsync(
    inputSource, inferenceParams
);

// You should save the job ID for your records
System.Console.WriteLine(response.Job.Id);

// If you set an `alias`, you can verify it was taken into account
System.Console.WriteLine(response.Job.Alias);
```



**Note:** You can also use both methods!

First, make sure you've added a webhook ID to the `InferenceParameters` instance.\
Then, call `EnqueueAndGetInferenceAsync`.\
You'll get the response via polling and webhooks will be used as well.
{% endtab %}
{% endtabs %}

## Process the Result

Now that your file or URL has been handled by the Mindee servers, you'll want to process the results and use them in your application.

Head on over to the [process-the-result.md](process-the-result.md "mention") section for details on the next step.

