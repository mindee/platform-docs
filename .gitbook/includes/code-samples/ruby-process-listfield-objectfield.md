---
title: ruby-process-listfield-objectfield
---

```ruby
object_list_field = result.inference.fields["my_object_list_field"]

# access an object at a given position
object_item_0 = object_list_field[0]
sub_field_0_value = object_item_0["sub_field"]["value"]

# loop over object lists
object_list_field.each do |object_item|
  sub_field_value = object_item["sub_field"]["value"]
end
```
