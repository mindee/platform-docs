---
title: php-process-objectfield
---

```php
use Mindee\V2\Product\Extraction\ExtractionResponse;

public function handleResponse(ExtractionResponse $response)
{
    $fields = $response->inference->result->fields;

    $objectField = $fields->getObjectField('my_object_field');
    $subFields = $objectField->fields;

    // grab a single sub-field
    $subfield1 = $subFields->getSimpleField('subfield_1');

    // loop over sub-fields
    foreach ($subFields as $fieldName => $subField) {
        $fieldValue = $subField->value;
    }
}
```
