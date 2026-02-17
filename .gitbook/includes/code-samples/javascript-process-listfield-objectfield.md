---
title: javascript-process-listfield-objectfield
---

```javascript
handleResponse(response) {
  const fields = response.inference.result.fields;

  const fieldObjectList = fields.getListField("my_object_list_field");

  const objectItems = fieldSimpleList.objectItems;

  // Loop over the list of Object fields
  for (const itemField of objectItems) {
    const simpleSubFields = itemField.simpleFields;

    // grab a single sub-field
    const subField1 = subFields.get("subfield_1");

    // Choose the appropriate accessor:
    // stringValue, doubleValue, booleanValue
    const subFieldValue = subField1.stringValue;

    // loop over simple sub-fields
    simpleSubFields.forEach((subField, fieldName) => {
      // Choose the appropriate accessor:
      // stringValue, doubleValue, booleanValue
      const fieldValue = subField.stringValue;
    });

    // Object fields can also have lists:
    const listSubFields = itemField.listFields;
  }
}
```
