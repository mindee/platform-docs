---
title: php-process-listfield-simplefield
---

```php
$inferenceFields = $response->inference->result->fields;
$simpleListField = $inferenceFields["my_simple_list_field"];

// access a value at a given position
$fieldFirstValue = $simpleListField[0]->value;

// Loop over the list of Simple fields
foreach ($simpleListField->items as $listItem) {
    $itemValue = $listItem->value;
}
```
