---
title: java-process-listfield-objectfield
---

```java
import com.mindee.parsing.v2.InferenceResponse;
import com.mindee.parsing.v2.field.InferenceFields;
import com.mindee.parsing.v2.field.ListField;
import com.mindee.parsing.v2.field.ObjectField;
import com.mindee.parsing.v2.field.SimpleField;

public void handleResponse(InferenceResponse response) {
    InferenceFields fields = response.inference.getResult().getFields();

    ListField fieldObjectList = fields.getListField("my_object_list_field");

    List<ObjectField> objectItems = listField.getObjectItems();

    // Loop over the list of Object fields
    for (ObjectField itemField : objectItems) {
    
        // Object sub-fields will always be Simple fields
        HashMap<String, SimpleField> subFields = itemField.getSimpleFields();

        // grab a single sub-field
        SimpleField subfield1 = subFields.get("subfield_1");
        
        // Choose the appropriate value type accessor method:
        // String, Double, Boolean
        String subFieldValue = subfield1.getStringValue();

        // loop over sub-fields
        for (Map.Entry<String, SimpleField> entry : subFields.entrySet()) {
            String fieldName = entry.getKey();
            SimpleField subField = entry.getValue();
        }
    }
}
```
