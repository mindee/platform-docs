---
title: python-process-listfield-simplefield
---

```python
from mindee.v2 import ExtractionResponse

def handle_response(response: ExtractionResponse):
    fields = response.inference.result.fields

    simple_list_field = fields.get_list_field("my_simple_list_field")

    # Loop over the list of Simple fields
    for list_item in simple_list_field.items:
        item_value = list_item.value
```
