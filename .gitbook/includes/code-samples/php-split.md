---
title: sample-code-php-extraction
---

Requires PHP ≥ 8.1\
Requires the [Mindee PHP client library](https://packagist.org/packages/mindee/mindee) version **2.7.0** or greater.

{% code lineNumbers="true" %}
```php
<?php

use Mindee\ClientV2;
use Mindee\V2\Product\Split\Params\SplitParameters;
use Mindee\V2\Product\Split\SplitResponse;
use Mindee\Input\PathInput;

$apiKey = "MY_API_KEY";
$filePath = "/path/to/the/file.ext";
$modelId = "MY_MODEL_ID";

// Init a new client
$mindeeClient = new ClientV2($apiKey);

// Set split parameters
// Note: modelId is mandatory.
$splitParams = new SplitParameters(
    // ID of the model, required.
    $modelId,
);

// Load a file from disk
$inputSource = new PathInput($filePath);

// Send for processing using polling
$response = $mindeeClient->enqueueAndGetResult(
    SplitResponse::class,
    $inputSource,
    $splitParams
);

// Print a summary of the response
echo strval($response->inference);

// Access the split results
$splits = $response->inference->result->splits;
```
{% endcode %}

Also take a look at the [Processing Results](https://docs.mindee.com/integrations/client-libraries-sdk/quick-start#processing-the-results) documentation.
