---
title: ruby-process-objectfield
---

```ruby
def handle_response(response)
  fields = response.inference.result.fields

  object_field = fields.get_object_field('my_object_field')
  sub_fields = object_field.fields
  
  # grab a single sub-field
  sub_field_value = sub_fields.get_simple_field('sub_field').value
  
  # loop over sub-fields
  sub_fields.each_value do |sub_field|
    field_value = sub_field.value
  end
end
```
