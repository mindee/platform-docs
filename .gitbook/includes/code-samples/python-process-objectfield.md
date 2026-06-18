---
title: python-process-objectfield
---

```python
from mindee.v2 import ExtractionResponse

def handle_response(response: ExtractionResponse):
    fields = response.inference.result.fields

    object_field = fields.get_object_field("my_object_field")

    sub_fields: dict = object_field.fields

    # grab a single sub-field
    subfield_1 = sub_fields["subfield_1"]

    # loop over sub-fields
    for field_name, sub_field in sub_fields.items():
        sub_field.value
```
