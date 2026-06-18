---
title: python-process-simplefield
---

```python
from mindee.v2 import ExtractionResponse

def handle_response(response: ExtractionResponse):
  fields: dict = response.inference.result.fields

  # texts, dates, classifications ...
  string_field_value: str | None = fields["string_field"].value

  # a JSON float will be a float
  float_field_value: float | None = fields["float_field"].value

  # even if the API always returns an integer, the type will be float
  int_field_value: float | None = fields["int_field"].value

  # booleans
  bool_field_value: bool | None = fields["bool_field"].value
```
