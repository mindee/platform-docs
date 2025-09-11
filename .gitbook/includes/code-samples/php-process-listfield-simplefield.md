---
title: php-process-listfield-simplefield
---

```php
use Mindee\Parsing\V2\InferenceResponse;

public function handleResponse(InferenceResponse $response)
{
    $fields = $response->inference->result->fields;

    $simpleListField = $fields->getListField('my_simple_list_field');

    // access a value at a given position
    $fieldFirstValue = $simpleListField[0]->value;

    // Loop over the list of Simple fields
    foreach ($simpleListField->items as $listItem) {
        $itemValue = $listItem->value;
    }
}
```
