---
title: javascript-process-listfield-simplefield
---

```javascript
handleResponse(response) {
  const fields = response.inference.result.fields;

  const simpleListField = fields.getListField("my_simple_list_field");

  const simpleItems = simpleListField.simpleItems;

  // Loop over the list of Simple fields
  for (const itemField of simpleItems) {
    // Choose the appropriate accessor:
    // stringValue, doubleValue, booleanValue
    const fieldValue = itemField.stringValue;
  }
}
```
