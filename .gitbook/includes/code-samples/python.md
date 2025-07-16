---
title: sample-code-python
---

Requires Python 3.9 or greater and the [Mindee Python client library](https://pypi.org/project/mindee/4.24.0rc2/) version 4.24.0 or greater.\
**Currently you'll need the RC version, full release coming soon!**

{% code lineNumbers="true" %}
```python
from mindee import ClientV2, InferencePredictOptions
from mindee.parsing.v2 import InferenceResponse

input_path = "/path/to/the/file.ext"
api_key = "MY_API_KEY"
model_id = "MY_MODEL_ID"

# Init a new client
mindee_client = ClientV2(api_key)

# Set inference options
options = InferencePredictOptions(
    # ID of the model, required.
    model_id=model_id,
    # If set to `True`, will enable Retrieval-Augmented Generation.
    rag=False,
)

# Load a file from disk
input_source = mindee_client.source_from_path(input_path)

# Upload the file
response: InferenceResponse = mindee_client.enqueue_and_parse(
    input_source, options
)

# Print a brief summary of the parsed data
print(response.inference)
```
{% endcode %}
