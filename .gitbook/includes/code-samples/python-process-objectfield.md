---
title: python-process-objectfield
---

```python
from mindee import InferenceResponse

def handle_response(response: InferenceResponse):
    fields: dict = response.inference.result.fields

    object_field = fields["my_object_field"]

    sub_fields: dict = object_field.fields

    # grab a single sub-field
    subfield_1 = sub_fields["subfield_1"]

    # loop over sub-fields
    for field_name, sub_field in sub_fields.items():
        sub_field.value
```
