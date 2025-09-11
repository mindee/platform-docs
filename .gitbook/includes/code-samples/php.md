---
title: sample-code-php
---

Requires PHP ≥ 8.0.\
Requires the [Mindee PHP client library](https://packagist.org/packages/mindee/mindee) version **1.23.0-rc3** or greater.

{% code lineNumbers="true" %}
```php
<?php

use Mindee\ClientV2;
use Mindee\Input\InferenceParameters;
use Mindee\Input\PathInput;
use Mindee\Error\MindeeException;

$apiKey = "MY_API_KEY";
$filePath = "/path/to/the/file.ext";
$modelId = "MY_MODEL_ID";

// Init a new client
$mindeeClient = new ClientV2($apiKey);

// Set inference parameters
// Note: modelId is mandatory.
$inferenceParams = new InferenceParameters(
    $modelId,
    // If set to `true`, will enable Retrieval-Augmented Generation.
    false
);

// Load a file from disk
$inputSource = new PathInput($filePath);

// Send for processing using polling
$response = $mindeeClient->enqueueAndGetInference(
    $inputSource,
    $inferenceParams
);

// Print a summary of the response
echo strval($response->inference);
```
{% endcode %}
