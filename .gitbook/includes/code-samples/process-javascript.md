---
title: process-javascript
---

Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

```javascript
const mySimpleField = response.inference.result.fields.get("my_simple_field");
const fieldValue = mySimpleField.value;
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

```javascript
const myListField = response.inference.result.fields.get("my_list_field");

// access a value at a given position
const fieldFirstValue = myListField.items[0].value;

// loop over all values in the list
for (const listItem of myListField) {
    const itemValue = listItem.value;
}
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```javascript
const objectField = response.inference.result.fields.get("my_object_field");
const subFieldValue = objectField.fields.get("sub_field").value;
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```javascript
const objectListField = response.inference.result.fields.get("my_object_list_field");

// access an object at a given position
const objectItem0 = objectListField.items[0].fields;
const subField0Value = objectItem0.get("sub_field").value;

// loop over object lists
for (const objectItem of objectListField.items) {
    const subFieldValue = objectItem.fields.get("sub_field").value;
}
```
