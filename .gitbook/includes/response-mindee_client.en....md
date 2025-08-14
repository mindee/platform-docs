---
title: response = mindee_client.en...
---

```ruby

response = mindee_client.enqueue_and_get_inference(
  input_source,
  inference_params
)

# To easily test which data was extracted,
# simply print an RST representation of the inference
puts response.inference
```
