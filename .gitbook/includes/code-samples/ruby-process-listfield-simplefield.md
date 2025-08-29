---
title: ruby-process-listfield-simplefield
---

```ruby
my_list_field = response.inference.fields['my_list_field']

# access a value at a given position
field_first_value = my_list_field[0]["value"]
# Note: Here `value` could be another subfield attribute, since my_list_field[0] can be an `ObjectField`.

# loop over all values in the list
my_list_field.each do |list_item|
  item_value = list_item["value"]
end
```
