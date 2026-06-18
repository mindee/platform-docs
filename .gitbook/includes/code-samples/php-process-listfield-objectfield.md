---
title: php-process-listfield-objectfield
---

```php
use Mindee\V2\Product\Extraction\ExtractionResponse;

public function handleResponse(ExtractionResponse $response)
{
    $fields = $response->inference->result->fields;
    $fieldObjectList = $fields->getObjectField('my_object_list_field');

    // access an object at a given position
    $objectItem0 = $fieldObjectList->items[0];
    $subField0Value = $objectItem0->fields->get('sub_field')->value;

    // Loop over the list of Object fields
    foreach ($myObjectListField->items as $objectItem) {
        $subFieldValue = $objectItem->fields->get('sub_field')->value;
    }
}
```
