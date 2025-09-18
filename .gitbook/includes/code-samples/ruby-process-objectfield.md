---
title: ruby-process-objectfield
---

```ruby
def handle_response(response)
  fields = response.inference.result.fields

  object_field = fields.get('my_object_field')
  sub_field_value = object_field.fields.get('sub_field').value
end
```
