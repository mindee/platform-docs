---
title: php-process-listfield-simplefield
---

```php
$inferenceFields = $response->inference->result->fields;
$myListField = $inferenceFields["my_list_field"];

// access a value at a given position
$fieldFirstValue = $myListField[0]->value;

// loop over all values in the list
foreach ($myListField->items as $listItem) {
    $itemValue = $listItem->value;
}
```
