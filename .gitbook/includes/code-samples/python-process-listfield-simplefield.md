---
title: python-process-listfield-simplefield
---

```python
from mindee import InferenceResponse

def handle_response(response: InferenceResponse):
    fields = response.inference.result.fields

    my_list_field = fields["my_list_field"]

    # loop over all values in the list
    for list_item in my_list_field:
        item_value = list_item.value
```
