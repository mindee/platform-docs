---
title: python-process-objectfield
---

```python
from mindee import InferenceResponse

def handle_response(response: InferenceResponse):
    fields = response.inference.result.fields

    object_field = fields["my_object_field"]
    sub_field_value = object_field.fields["sub_field"].value
```
