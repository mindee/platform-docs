---
title: python-process-listfield-simplefield
---

```python
my_list_field = response.inference.result.fields["my_list_field"]

# access a value at a given position
field_first_value = my_list_field.items[0].value

# loop over all values in the list
for list_item in my_list_field:
    item_value = list_item.value
```
