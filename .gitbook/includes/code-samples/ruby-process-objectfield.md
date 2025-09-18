---
title: ruby-process-objectfield
---

```ruby
def handle_response(response)
  object_field = response.inference.fields.get('my_object_field')
  sub_field_value = object_field.fields['sub_field'].value
end
```
