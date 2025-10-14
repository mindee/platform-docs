---
title: java-process-simplefield
---

```java
import com.mindee.parsing.v2.InferenceResponse;
import com.mindee.parsing.v2.field.InferenceFields;

public void handleResponse(InferenceResponse response) {
  InferenceFields fields = response.inference.getResult().getFields();

  // texts, dates, classifications ...
  String stringFieldValue = fields.getSimpleField("string_field")
        .getStringValue();

  // a JSON float will be a Double
  Double floatFieldValue = fields.getSimpleField("float_field")
      .getDoubleValue();

  // even if the API always returns an integer, the type will be Double
  Double intFieldValue = fields.getSimpleField("int_field")
      .getDoubleValue();

  // booleans
  Boolean boolFieldValue = fields.getSimpleField("bool_field")
      .getBooleanValue();
}
```
