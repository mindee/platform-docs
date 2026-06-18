---
title: java-process-objectfield
---

```java
import com.mindee.v2.product.extraction.ExtractionResponse;
import com.mindee.parsing.v2.field.ListField;
import com.mindee.parsing.v2.field.ObjectField;
import com.mindee.parsing.v2.field.SimpleField;

public void handleResponse(ExtractionResponseresponse) {
  var fields = response.getInference().getResult().getFields();

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
