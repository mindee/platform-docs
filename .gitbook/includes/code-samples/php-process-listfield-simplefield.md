---
title: php-process-listfield-simplefield
---

```php
use Mindee\V2\Product\Extraction\ExtractionResponse;

public function handleResponse(ExtractionResponse$response)
{
    $fields = $response->inference->result->fields;

    $simpleListField = $fields->getListField('my_simple_list_field');

    // access a value at a given position
    $fieldFirstValue = $simpleListField->items[0]->value;

    // Loop over the list of Simple fields
    foreach ($simpleListField->items as $listItem) {
        $itemValue = $listItem->value;
    }
}
```
