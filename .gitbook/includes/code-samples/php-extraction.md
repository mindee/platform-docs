---
title: sample-code-php-extraction
---

Requires PHP ≥ 8.1. PHP ≥ 8.3 is recommended.\
Requires the [Mindee PHP client library](https://packagist.org/packages/mindee/mindee) version **3.0.0** or greater.

{% code lineNumbers="true" %}
```php
<?php

use Mindee\Input\PathInput;
use Mindee\V2\Client;
use Mindee\V2\Product\Extraction\Params\ExtractionParameters;
use Mindee\V2\Product\Extraction\ExtractionResponse;

$apiKey = "MY_API_KEY";
$modelId = "MY_MODEL_ID";
$filePath = "/path/to/the/file.ext";

// Init a new client
$mindeeClient = new Client($apiKey);

// Set inference parameters
$modelParams = new ExtractionParameters(
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
$response = $mindeeClient->enqueueAndGetResult(
    ExtractionResponse::class,
    $inputSource,
    $modelParams
);

// Print a summary of the response
echo strval($response->inference);

// Access the extracted fields
$fields = $response->inference->result->fields;
```
{% endcode %}

Also take a look at the [Processing Results](https://docs.mindee.com/extraction-models/sdk-integration/extraction-result) documentation.
