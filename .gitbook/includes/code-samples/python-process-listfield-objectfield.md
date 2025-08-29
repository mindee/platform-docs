---
title: python-process-listfield-objectfield
---

```python
object_list_field = response.inference.result.fields["my_object_list_field"]

# access an object at a given position
object_item_0 = object_list_field.items[0]
sub_field_0_value = object_item_0["sub_field"].value

# loop over object lists
for object_item in object_list_field.items:
  sub_field_value = object_item.fields["sub_field"].value
```
