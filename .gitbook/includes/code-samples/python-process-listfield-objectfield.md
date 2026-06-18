---
title: python-process-listfield-objectfield
---

```python
from mindee.v2 import ExtractionResponse

def handle_response(response: ExtractionResponse):
    fields: dict = response.inference.result.fields

    object_list_field = fields["my_object_list_field"]

    # Loop over the list of Object fields
    for object_item in object_list_field.items:
        # grab a single sub-field
        sub_field_value = object_item.fields["sub_field"].value
        
        # loop over sub-fields
        for field_name, sub_field in object_item.fields.items():
            sub_field.value
```
