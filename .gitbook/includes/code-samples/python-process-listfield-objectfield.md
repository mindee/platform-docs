---
title: python-process-listfield-objectfield
---

```python
from mindee import InferenceResponse

def handle_response(response: InferenceResponse):
    fields = response.inference.result.fields

    object_list_field = fields["my_object_list_field"]

    # loop over object lists
    for object_item in object_list_field.items:
      sub_field_value = object_item.fields["sub_field"].value
```
