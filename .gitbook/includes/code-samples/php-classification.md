---
title: sample-code-php-extraction
---

Requires PHP ≥ 8.1. PHP ≥ 8.3 is recommended.\
Requires the [Mindee PHP SDK](https://packagist.org/packages/mindee/mindee) version **2.7.1** or greater.

{% code lineNumbers="true" %}
```php
<?php

use Mindee\ClientV2;
use Mindee\V2\Product\Classification\Params\ClassificationParameters;
use Mindee\V2\Product\Classification\ClassificationResponse;
use Mindee\Input\PathInput;

$apiKey = "MY_API_KEY";
$filePath = "/path/to/the/file.ext";
$modelId = "MY_MODEL_ID";

// Init a new client
$mindeeClient = new ClientV2($apiKey);

// Set classification parameters
$modelParams = new ClassificationParameters(
    // ID of the model, required.
    $modelId
);

// Load a file from disk
$inputSource = new PathInput($filePath);

// Send for processing using polling
$response = $mindeeClient->enqueueAndGetResult(
    ClassificationResponse::class,
    $inputSource,
    $modelParams
);

// Print a summary of the response
echo strval($response->inference);

// Access the classification results
$classification = $response->inference->result->classification;
```
{% endcode %}

Also take a look at the [Classification Result](https://docs.mindee.com/classification-models/sdk-integration/classification-result) documentation.
