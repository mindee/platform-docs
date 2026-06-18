---
title: sample-code-php-extraction
---

Requires PHP ≥ 8.1. PHP ≥ 8.3 is recommended.\
Requires the [Mindee PHP SDK](https://packagist.org/packages/mindee/mindee) version **3.0.0** or greater.

{% code lineNumbers="true" %}
```php
<?php

use Mindee\Input\PathInput;
use Mindee\V2\Client;
use Mindee\V2\Product\Ocr\Params\OcrParameters;
use Mindee\V2\Product\Ocr\OcrResponse;

$apiKey = "MY_API_KEY";
$modelId = "MY_MODEL_ID";
$filePath = "/path/to/the/file.ext";

// Init a new client
$mindeeClient = new Client($apiKey);

// Set ocr parameters
$modelParams = new OcrParameters(
    // ID of the model, required.
    $modelId,
);

// Load a file from disk
$inputSource = new PathInput($filePath);

// Send for processing using polling
$response = $mindeeClient->enqueueAndGetResult(
    OcrResponse::class,
    $inputSource,
    $modelParams
);

// Print a summary of the response
echo strval($response->inference);

// Access the ocr results
$pages = $response->inference->result->pages;
```
{% endcode %}

Also take a look at the [OCR Result](https://docs.mindee.com/ocr-models/sdk-integration/ocr-result) documentation.
