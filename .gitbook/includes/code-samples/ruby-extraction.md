---
title: sample-code-ruby-extraction
---

<code class="expression">space.vars.VERSIONS_RUBY</code>\
Requires the [Mindee Ruby client library](https://rubygems.org/gems/mindee) version &#x35;**.1.0** or greater.

{% code lineNumbers="true" %}
```ruby
require 'mindee'
require 'mindee/v2/product'

input_path = '/path/to/the/file.ext'
api_key = 'MY_API_KEY'
model_id = 'MY_MODEL_ID'

# Init a new client
mindee_client = Mindee::V2::Client.new(api_key: api_key)

# Set inference parameters
extraction_params = {
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
    extraction_params
)

# Print a brief summary of the parsed data
puts response.inference

# Access the result fields
fields = response.inference.result.fields

# fields.get_simple_field('my_simple_field')
# fields.get_list_field('my_list_field')
# fields.get_object_field('my_object_field')
```
{% endcode %}

Also take a look at the [Processing Results](https://docs.mindee.com/integrations/client-libraries-sdk/quick-start#processing-the-results) documentation.
