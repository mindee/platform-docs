---
title: sample-code-php
---

Requires PHP ≥ 8.1\
Requires the [Mindee PHP client library](https://packagist.org/packages/mindee/mindee) version **2.0.3** or greater.

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

// Load a file from disk
$inputSource = new PathInput($filePath);

// Send for processing using polling
$response = $mindeeClient->enqueueAndGetInference(
    $inputSource,
    $inferenceParams
);

// Print a summary of the response
echo strval($response->inference);

// Access the result fields
$fields = $response->inference->result->fields;
```
{% endcode %}

Next take a look at the  [#processing-the-results](../../../integrations/client-libraries-sdk/quick-start.md#processing-the-results "mention") documentation.
