---
title: java-process-objectfield
---

```java
import com.mindee.parsing.v2.InferenceResponse;
import com.mindee.parsing.v2.field.InferenceFields;
import com.mindee.parsing.v2.field.ListField;
import com.mindee.parsing.v2.field.ObjectField;
import com.mindee.parsing.v2.field.SimpleField;

public void handleResponse(InferenceResponse response) {
  InferenceFields fields = response.inference.getResult().getFields();

  ObjectField objectField = fields.getObjectField("my_object_field");

  HashMap<String, SimpleField> subFields = objectField.getSimpleFields();

  // grab a single sub-field
  SimpleField subfield1 = subFields.get("subfield_1");

  // loop over sub-fields
  for (Map.Entry<String, SimpleField> entry : subFields.entrySet()) {
    String fieldName = entry.getKey();
    SimpleField subField = entry.getValue();
    
    // Choose the appropriate value type accessor method:
    // String, Double, Boolean
    String fieldValue = subField.getStringValue();
  }
}
```
