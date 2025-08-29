---
title: javascript-process-simplefield
---

```typescript
handleResponse(response) {
  const fields = response.inference.result.fields;
  
  // texts, dates, classifications ...
  const stringFieldValue = fields.getSimpleField("string_field").stringValue;
  
  // no distinction between floats and numbers
  const floatFieldValue = fields.getSimpleField("float_field").numberValue;
  const intFieldValue = fields.getSimpleField("int_field").numberValue;
  
  // booleans
  const boolFieldValue = fields.getSimpleField("bool_field").booleanValue;
}
```
