---
title: ruby-process-listfield-simplefield
---

```ruby
my_list_field = response.inference.fields['my_simple_list_field']

# access a value at a given position
simple_list_field = my_list_field[0]['value']

# Loop over the list of Simple fields
simple_list_field.items.each do |list_item|
  item_value = list_item['value']
end
```
