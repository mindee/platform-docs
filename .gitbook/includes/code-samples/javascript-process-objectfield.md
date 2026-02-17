---
title: javascript-process-objectfield
---

```javascript
handleResponse(response) {
  const fields = response.inference.result.fields;

  const objectField = fields.getObjectField("my_object_field");

  const simpleSubFields = objectField.simpleFields;

  // grab a single sub-field
  const subfield1 = subFields.get("subfield_1");

  // loop over simple sub-fields
  subFields.forEach((simpleSubFields, fieldName) => {
    // Choose the appropriate accessor:
    // stringValue, doubleValue, booleanValue
    const fieldValue = subField.stringValue;
  });

  // Object fields can also have lists:
  const listSubFields = objectField.listFields;
}
```
