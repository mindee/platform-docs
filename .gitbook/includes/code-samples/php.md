---
title: sample-code-php
---

Requires PHP 8.0 minimum.

{% code lineNumbers="true" %}
```php
<?php

function sendFileWithPolling(
    string $filePath,
    string $modelId,
    string $apiKey,
    int $maxRetries = 30,
    int $pollingInterval = 2
): array {
    $fileName = basename($filePath);
    $headers = ["Authorization: $apiKey"];

    $postFields = [
        'model_id' => $modelId,
        'rag' => 'false',
        'file' => new CURLFile($filePath, 'application/octet-stream', $fileName)
    ];

    // Initial API request
    $ch = curl_init("https://api-v2.mindee.net/v2/inferences/enqueue");
    curl_setopt_array($ch, [
        CURLOPT_POST => true,
        CURLOPT_POSTFIELDS => $postFields, // Using array instead of string
        CURLOPT_RETURNTRANSFER => true,
        CURLOPT_HTTPHEADER => $headers
    ]);

    $result = curl_exec($ch);
    $httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);

    // Check for HTTP error codes
    if ($httpCode >= 400) {
        curl_close($ch);
        throw new Exception("API request failed with HTTP code $httpCode: " . ($result ?: 'No response'));
    }
    $response = json_decode($result, true);
    curl_close($ch);

    $pollingUrl = $response['job']['polling_url'];
    sleep(3);

    // Poll for results
    for ($i = 0; $i < $maxRetries; $i++) {
        echo "Polling on: $pollingUrl\n";

        $ch = curl_init($pollingUrl);
        curl_setopt_array($ch, [
            CURLOPT_RETURNTRANSFER => true,
            CURLOPT_HTTPHEADER => $headers,
            CURLOPT_FOLLOWLOCATION => false
        ]);

        $pollResponse = curl_exec($ch);
        $httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
        $redirectUrl = curl_getinfo($ch, CURLINFO_REDIRECT_URL);
        curl_close($ch);

        if ($httpCode == 302 || $redirectUrl) {
            $resultUrl = $redirectUrl;
        } else {
            $pollData = json_decode($pollResponse, true);
            if (($pollData['job']['status'] ?? '') != 'Processed') {
                sleep($pollingInterval);
                continue;
            }
            $resultUrl = $pollData['job']['result_url'];
        }

        echo "Get result from: $resultUrl\n";
        $ch = curl_init($resultUrl);
        curl_setopt_array($ch, [
            CURLOPT_RETURNTRANSFER => true,
            CURLOPT_HTTPHEADER => $headers
        ]);
        $result = curl_exec($ch);
        curl_close($ch);

        return json_decode($result, true);
    }
    throw new Exception("Polling timed out after $maxRetries attempts");
}

$result = sendFileWithPolling(
    "/path/to/file.pdf",
    "MY_MODEL_ID",
    "MY_API_KEY"
);
print_r($result);
```
{% endcode %}
