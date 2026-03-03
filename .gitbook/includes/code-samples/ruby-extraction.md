---
title: sample-code-ruby-extraction
---

Requires Ruby ≥ 3.0.\
Requires the [Mindee Ruby client library](https://rubygems.org/gems/mindee) version **4.13.0** or greater.

{% code lineNumbers="true" %}
```ruby
require 'mindee'
require 'mindee/v2/product'

input_path = '/path/to/the/file.ext'
api_key = 'MY_API_KEY'
model_id = 'MY_MODEL_ID'

# Init a new client
mindee_client = Mindee::ClientV2.new(api_key: api_key)

# Set inference parameters
inference_params = {
    # ID of the model, required.
    model_id: model_id,

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
}

# Load a file from disk
input_source = Mindee::Input::Source::PathInputSource.new(input_path)

# Send for processing
response = mindee_client.enqueue_and_get_result(
    Mindee::V2::Product::Extraction::Extraction,
    input_source,
    inference_params
)

# Print a brief summary of the parsed data
puts response.inference

# fields.get_simple_field('my_field')
# fields.get_list_field('my_field')
# fields.get_object_field('my_field')
```
{% endcode %}

Also take a look at the [Processing Results](https://docs.mindee.com/integrations/client-libraries-sdk/quick-start#processing-the-results) documentation.
