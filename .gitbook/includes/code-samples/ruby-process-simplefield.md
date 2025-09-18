---
title: ruby-process-simplefield
---

```ruby
def handle_response(response)
  fields = response.inference.result.fields

  # texts, dates, classifications ...
  string_field_value = fields.get('string_field').value

  # a JSON float will be a float
  float_field_value = fields.get('float_field').value

  # even if the API always returns an integer, the type will be float
  int_field_value = fields.get('int_field').value

  # booleans
  bool_field_value = fields.get('bool_field').value
end
```
