---
title: sample-code-python
---

Requires Python ≥ 3.9. Python ≥ 3.10 is highly recommended.\
Requires the [Mindee Python client library](https://pypi.org/project/mindee/) version **4.33.0** or greater.

{% code lineNumbers="true" %}
```python
from mindee import (
    ClientV2,
    PathInput,
    OCRParameters,
    OCRResponse,
)

input_path = "/path/to/the/file.ext"
api_key = "MY_API_KEY"
model_id = "MY_OCR_MODEL_ID"

# Init a new client
mindee_client = ClientV2(api_key)

# Set parameters
params = OCRParameters(
    # ID of the model, required.
    model_id=model_id,
)

# Load a file from disk
input_source = PathInput(input_path)

# Send for processing using polling
response = mindee_client.enqueue_and_get_result(
    OCRResponse,
    input_source,
    params,
)

# Print a brief summary of the parsed data
print(response.inference)

# Access the ocr result
pages: list = response.inference.result.pages
```
{% endcode %}

Also take a look at the [Processing Results](https://docs.mindee.com/integrations/client-libraries-sdk/quick-start#processing-the-results) documentation.
