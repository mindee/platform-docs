---
title: python-process-simplefield
---

```python
from mindee import InferenceResponse

def handle_response(response: InferenceResponse):
    fields = response.inference.result.fields

    my_simple_field = fields["my_simple_field"]
    field_value = my_simple_field.value
```
