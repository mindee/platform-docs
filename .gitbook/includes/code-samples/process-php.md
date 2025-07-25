---
title: process-php
---

Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

```php
$inferenceFields = $response->inference->result->fields;
$mySimpleField = $inferenceFields["my_simple_field"];
$field_value = $mySimpleField->value;
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

```php
$inferenceFields = $response->inference->result->fields;
$myListField = $inferenceFields["my_list_field"];

// access a value at a given position
$fieldFirstValue = $myListField[0]->value;

// loop over all values in the list
foreach ($myListField as $listItem) {
    $itemValue = $listItem["value"];
}
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```php
$inferenceFields = $response->inference->result->fields;
$objectField = $inferenceFields["my_object_field"];
$subFieldValue = $objectField["sub_field"]->value;
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```php
$inferenceFields = $response->inference->result->fields;
$objectListField = $inferenceFields["my_object_list_field"];

// access an object at a given position
$objectItem0 = $objectListField[0];
$subField0Value = $objectItem0["sub_field"]->value;

// loop over object lists
foreach ($objectListField as $objectItem) {
    $subFieldValue = $objectItem["sub_field"]->value;
}
```
