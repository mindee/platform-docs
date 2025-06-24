---
icon: plug-circle-check
---

# Integrating Mindee

Once you have your model set up, you'll want to start using it!

## API key

Make sure you've created your API Key before continuing.

To create and manage your API keys, go to the "[API Keys](https://app.mindee.com/api-keys)" section on the Mindee Platform.

Click on create API Key, choose a name for this API Key, and validate.

You're now ready to go!

## Sending a File

To process your document using Mindee, simply send the file using the [REST API](../integrations/api-overview.md).

Make a note of your model's ID for use in the API.

When getting started, we recommend using the [#polling](../integrations/api-overview.md#polling "mention") method which will be quickest.

Here are some code examples, these are self-contained and can be run as-is:

{% tabs %}
{% tab title="Python" %}
Requires Python 3.9 minimum and the [requests](https://pypi.org/project/requests/) library.

{% code lineNumbers="true" %}
```python
import time
import requests
from pathlib import Path


def send_file_with_polling(
        file_path: str,
        model_id: str,
        api_key: str,
        max_retries: int = 30,
        polling_interval: int = 2,
) -> dict:
    file = Path(file_path)
    headers = {"Authorization": api_key}
    form_data = {"model_id": model_id, "rag": False}
    with open(file_path, "rb") as fh:
        files = {"file": (file.name, fh)}
        print(f"Enqueuing file: {file_path}")
        response = requests.post(
            url="https://api-v2.mindee.net/v2/inferences/enqueue",
            files=files,
            data=form_data,
            headers=headers,
        )
    response.raise_for_status()
    job_data = response.json().get("job")
    polling_url = job_data.get("polling_url")

    # Important to wait before attempting to poll
    time.sleep(3)

    # Poll for completion
    for attempt in range(max_retries):
        print(f"Polling on: {polling_url}")
        poll_response = requests.get(polling_url, headers=headers, allow_redirects=False)
        poll_data = poll_response.json()
        job_status = poll_data.get("job", {}).get("status")
        if poll_response.status_code == 302 or job_status == "Processed":
            result_url = poll_data.get("job", {}).get("result_url")
            print(f"Get result from: {result_url}")
            result_response = requests.get(result_url, headers=headers)
            result_data = result_response.json()
            return result_data
        # still processing, wait before next poll
        time.sleep(polling_interval)
    # If we've exhausted all retries
    raise TimeoutError(f"Polling timed out after {max_retries} attempts")


result = send_file_with_polling(
    file_path="/path/to/file.pdf",
    model_id="MY_MODEL_ID",
    api_key="MY_API_KEY",
)
print(result)

```
{% endcode %}
{% endtab %}

{% tab title="JavaScript" %}
Requires Node.js 20 minimum and the [axios](https://www.npmjs.com/package/axios) library.

{% code lineNumbers="true" %}
```javascript
const fs = require("fs");
const path = require("path");
const axios = require("axios");
const FormData = require("form-data");

async function sendFileWithPolling(
  filePath,
  modelId,
  apiKey,
  maxRetries = 30,
  pollingInterval = 2
) {
  const fileName = path.basename(filePath);
  const headers = {
    "Authorization": apiKey
  };

  const formData = new FormData();
  formData.append("model_id", modelId);
  formData.append("rag", "false");
  formData.append("file", fs.createReadStream(filePath), {
    filename: fileName
  });

  console.log(`Enqueuing file: ${filePath}`);
  const response = await axios.post(
    "https://api-v2.mindee.net/v2/inferences/enqueue",
    formData,
    {headers: { ...headers, ...formData.getHeaders() }}
  );

  const jobData = response.data.job;
  const pollingUrl = jobData.polling_url;

  await new Promise(resolve => setTimeout(resolve, 3000));

  for (let attempt = 0; attempt < maxRetries; attempt++) {
    console.log(`Polling on: ${pollingUrl}`);

    const pollResponse = await axios.get(pollingUrl, {
      headers,
      maxRedirects: 0,
      validateStatus: status => status >= 200 && status < 400
    });

    const pollData = pollResponse.data;
    const jobStatus = pollData.job?.status;

    if (pollResponse.status === 302 || jobStatus === "Processed") {
      const resultUrl = pollData.job?.result_url;
      console.log(`Get result from: ${resultUrl}`);

      const resultResponse = await axios.get(resultUrl, { headers });
      return resultResponse.data;
    }
    await new Promise(resolve => setTimeout(resolve, pollingInterval * 1000));
  }
  throw new Error(`Polling timed out after ${maxRetries} attempts`);
}

async function main() {
  try {
    const result = await sendFileWithPolling(
      "/path/to/file.pdf",
      "MY_MODEL_ID",
      "MY_API_KEY"
    );
    console.log(result);
  } catch (error) {
    console.error("Error:", error.message);
  }
}

main();
```
{% endcode %}
{% endtab %}

{% tab title="Ruby" %}
Requires Ruby 3.0 minimum. Could be greatly simplified if using RoR.

{% code lineNumbers="true" %}
```ruby
require 'uri'
require 'net/http'
require 'json'
require 'securerandom'

def send_file_with_polling(file_path, model_id, api_key, max_retries = 30, polling_interval = 2)
  # Upload file
  uri = URI.parse("https://api-v2.mindee.net/v2/inferences/enqueue")
  boundary = "----RubyFormBoundary#{SecureRandom.hex(8)}"
  file_name = File.basename(file_path)

  # Build multipart form data
  post_body = []
  post_body << "--#{boundary}\r\nContent-Disposition: form-data; name=\"model_id\"\r\n\r\n#{model_id}\r\n"
  post_body << "--#{boundary}\r\nContent-Disposition: form-data; name=\"rag\"\r\n\r\nfalse\r\n"
  post_body << "--#{boundary}\r\nContent-Disposition: form-data; name=\"file\"; filename=\"#{file_name}\""
  post_body << "\r\n#{File.binread(file_path)}\r\n--#{boundary}--\r\n"

  # Send initial request
  http = Net::HTTP.new(uri.host, uri.port)
  http.use_ssl = true
  request = Net::HTTP::Post.new(uri.request_uri)
  request["Authorization"] = api_key
  request["Content-Type"] = "multipart/form-data; boundary=#{boundary}"
  request.body = post_body.join

  response = http.request(request)
  if response.code.to_i >= 400
    raise "HTTP Error: #{response.code} - #{response.message}. Response body: #{response.body}"
  end
  polling_url = JSON.parse(response.body).dig("job", "polling_url")

  sleep(3)

  # Poll for results
  max_retries.times do
    puts "Polling on: #{polling_url}"
    uri = URI.parse(polling_url)
    poll_request = Net::HTTP::Get.new(uri)
    poll_request["Authorization"] = api_key
    http = Net::HTTP.new(uri.host, uri.port)
    http.use_ssl = true
    poll_response = http.request(poll_request)

    # Handle redirection or processed status
    if poll_response.is_a?(Net::HTTPRedirection) || poll_response.code == "302"
      result_url = poll_response["location"]
    else
      poll_data = JSON.parse(poll_response.body)
      if poll_data.dig("job", "status") == "Processed"
        result_url = poll_data.dig("job", "result_url")
      else
        sleep(polling_interval)
        next
      end
    end

    # Fetch results
    puts "Get result from: #{result_url}"
    uri = URI.parse(result_url)
    result_request = Net::HTTP::Get.new(uri)
    result_request["Authorization"] = api_key
    http = Net::HTTP.new(uri.host, uri.port)
    http.use_ssl = true
    return JSON.parse(http.request(result_request).body)
  end

  raise "Polling timed out after #{max_retries} attempts"
end

result = send_file_with_polling(
  "/path/to/file.pdf",
  "MY_MODEL_ID",
  "MY_API_KEY"
)
puts result
```
{% endcode %}
{% endtab %}

{% tab title="PHP" %}
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
{% endtab %}
{% endtabs %}

## Processing the Results

Once you've sent the file and retrieved the results, you can start extracting the JSON payload.

The model's fields will be in the `result.fields` object in the returned JSON.

Each key in the `fields` object corresponds to the field's `name` in your model configuration.

You'll want to adapt your processing depending on the [type of field](../features/models/data-schema.md#field-types), for example looping over lists.

{% tabs %}
{% tab title="Python" %}
Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

```python
my_simple_field = result["inference"]["fields"]["my_simple_field"]
field_value = my_simple_field["value"]
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

```python
my_list_field = result["inference"]["fields"]["my_list_field"]

# access a value at a given position
field_first_value = my_list_field[0]["value"]

# loop over all values in the list
for list_item in my_list_field:
    item_value = list_item["value"]
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```python
object_field = result["inference"]["fields"]["my_object_field"]
sub_field_value = object_field["sub_field"]["value"]
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```python
object_list_field = result["inference"]["fields"]["my_object_list_field"]

# access an object at a given position
object_item_0 = object_list_field[0]
sub_field_0_value = object_item_0["sub_field"]["value"]

# loop over object lists
for object_item in object_list_field:
  sub_field_value = object_item["sub_field"]["value"]
```
{% endtab %}

{% tab title="JavaScript" %}
Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

```javascript
const mySimpleField = result.inference.fields.my_simple_field;
const fieldValue = mySimpleField.value;
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

```javascript
const myListField = result.inference.fields.my_list_field;

// access a value at a given position
const fieldFirstValue = myListField[0].value;

// loop over all values in the list
for (const listItem of myListField) {
    const itemValue = listItem.value;
}
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```javascript
const objectField = result.inference.fields.my_object_field;
const subFieldValue = objectField.sub_field.value;
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```javascript
const objectListField = result.inference.fields.my_object_list_field;

// access an object at a given position
const objectItem0 = objectListField[0];
const subField0Value = objectItem0.sub_field.value;

// loop over object lists
for (const objectItem of objectListField) {
    const subFieldValue = objectItem.sub_field.value;
}
```
{% endtab %}

{% tab title="Ruby" %}
Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

```ruby
my_simple_field = result["inference"]["fields"]["my_simple_field"]
field_value = my_simple_field["value"]
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

```ruby
my_list_field = result["inference"]["fields"]["my_list_field"]

# access a value at a given position
field_first_value = my_list_field[0]["value"]

# loop over all values in the list
my_list_field.each do |list_item|
  item_value = list_item["value"]
end
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```ruby
object_field = result["inference"]["fields"]["my_object_field"]
sub_field_value = object_field["sub_field"]["value"]
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```ruby
object_list_field = result["inference"]["fields"]["my_object_list_field"]

# access an object at a given position
object_item_0 = object_list_field[0]
sub_field_0_value = object_item_0["sub_field"]["value"]

# loop over object lists
object_list_field.each do |object_item|
  sub_field_value = object_item["sub_field"]["value"]
end
```
{% endtab %}

{% tab title="PHP" %}
Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

```php
$my_simple_field = $result["inference"]["fields"]["my_simple_field"];
$field_value = $my_simple_field["value"];
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

```php
$my_list_field = $result["inference"]["fields"]["my_list_field"];

// access a value at a given position
$field_first_value = $my_list_field[0]["value"];

// loop over all values in the list
foreach ($my_list_field as $list_item) {
    $item_value = $list_item["value"];
}
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```php
$object_field = $result["inference"]["fields"]["my_object_field"];
$sub_field_value = $object_field["sub_field"]["value"];
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```php
$object_list_field = $result["inference"]["fields"]["my_object_list_field"];

// access an object at a given position
$object_item_0 = $object_list_field[0];
$sub_field_0_value = $object_item_0["sub_field"]["value"];

// loop over object lists
foreach ($object_list_field as $object_item) {
    $sub_field_value = $object_item["sub_field"]["value"];
}
```
{% endtab %}
{% endtabs %}
