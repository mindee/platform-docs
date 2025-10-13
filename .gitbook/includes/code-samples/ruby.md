---
title: sample-code-ruby
---

Requires Ruby ≥ 3.0.\
Requires the [Mindee Ruby client library](https://rubygems.org/gems/mindee/versions/4.7.0.pre.rc1) version **4.7.2** or greater.

{% code lineNumbers="true" %}
```ruby
require 'mindee'

input_path = '/path/to/the/file.ext'
api_key = 'MY_API_KEY'
model_id = 'MY_MODEL_ID'

# Init a new client
mindee_client = Mindee::ClientV2.new(api_key: api_key)

# Set inference parameters
inference_params = Mindee::Input::InferenceParameters.new(
    # ID of the model, required.
    model_id,

    # Options: set to `true` or `false` to override defaults

    # Enhance extraction accuracy with Retrieval-Augmented Generation.
    rag: nil,
    # Extract the full text content from the document as strings.
    raw_text: nil,
    # Calculate bounding box polygons for all fields.
    polygon: nil,
    # Boost the precision and accuracy of all extractions.
    # Calculate confidence scores for all fields.
    confidence: nil
)

# Load a file from disk
input_source = Mindee::Input::Source::PathInputSource.new(input_path)

# Send for processing using polling
response = mindee_client.enqueue_and_get_inference(
    input_source,
    inference_params # Note: this parameter can also be provided as a Hash.
)

# Print a brief summary of the parsed data
puts response.inference
```
{% endcode %}
