---
title: ruby-process-simplefield
---

```ruby
def handle_response(response)
  fields = response.inference.result.fields

  # texts, dates, classifications ...
  string_field_value = fields.get_simple_field('string_field').string_value

  # a JSON float will be a float
  float_field_value = fields.get_simple_field('float_field').float_value

  # even if the API always returns an integer, the type will be float
  int_field_value = fields.get_simple_field('int_field').float_value

  # booleans
  bool_field_value = fields.get_simple_field('bool_field').boolean_value
end
```
