---
title: java-process-listfield-simplefield
---

```java
import com.mindee.parsing.v2.InferenceResponse;
import com.mindee.parsing.v2.field.InferenceFields;
import com.mindee.parsing.v2.field.ListField;
import com.mindee.parsing.v2.field.SimpleField;

public void handleResponse(InferenceResponse response) {
    InferenceFields fields = response.inference.getResult().getFields();

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
