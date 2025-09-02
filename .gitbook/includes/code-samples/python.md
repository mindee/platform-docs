---
title: sample-code-python
---

Requires Python ≥ 3.9. Python ≥ 3.10 is highly recommended.\
Requires the [Mindee Python client library](https://pypi.org/project/mindee/) version **4.27.1** or greater.

{% code lineNumbers="true" %}
```python
from mindee import ClientV2, InferenceParameters, PathInput

input_path = "/path/to/the/file.ext"
api_key = "MY_API_KEY"
model_id = "MY_MODEL_ID"

# Init a new client
mindee_client = ClientV2(api_key)

# Set inference parameters
params = InferenceParameters(
    # ID of the model, required.
    model_id=model_id,
    # If set to `True`, will enable Retrieval-Augmented Generation.
    rag=False,
)

# Load a file from disk
input_source = PathInput(input_path)

# Send for processing using polling
response = mindee_client.enqueue_and_get_inference(
    input_source, params
)

# Print a brief summary of the parsed data
print(response.inference)
```
{% endcode %}
