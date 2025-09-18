---
title: ruby-process-listfield-objectfield
---

```ruby
def handle_response(response)
  object_list_field = result.inference.fields.get('my_object_list_field')

  # access an object at a given position
  object_item_0 = object_list_field.items[0]
  sub_field_0_value = object_item_0.fields['sub_field'].value

  # Loop over the list of Object fields
  object_list_field.fields.each do |object_item|
    sub_field_value = object_item['sub_field'].value
  end
end
```
