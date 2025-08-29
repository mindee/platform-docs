---
title: php-process-listfield-objectfield
---

```php
$inferenceFields = $response->inference->result->fields;
$myObjectListField = $inferenceFields["my_object_list_field"];

// access an object at a given position
$objectItem0 = $myObjectListField->items[0];
$subField0Value = $objectItem0["sub_field"]->value;

// loop over object lists
foreach ($myObjectListField->items as $objectItem) {
    $subFieldValue = $objectItem["sub_field"]->value;
}
```
