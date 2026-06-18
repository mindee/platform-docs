---
title: java-process-listfield-simplefield
---

```java
import com.mindee.v2.product.extraction.ExtractionResponse;
import com.mindee.parsing.v2.field.ListField;
import com.mindee.parsing.v2.field.SimpleField;

public void handleResponse(ExtractionResponseresponse) {
  var fields = response.getInference().getResult().getFields();

  ListField simpleListField = fields.getListField("my_simple_list_field");

  List<SimpleField> simpleItems = simpleListField.getSimpleItems();

  // Loop over the list of Simple fields
  for (SimpleField itemField : simpleItems) {
    // Choose the appropriate value type accessor method:
    // String, Double, Boolean
    String fieldValue = itemField.getStringValue();
  }
}
```
