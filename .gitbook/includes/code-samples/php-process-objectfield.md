---
title: php-process-objectfield
---

```php
use Mindee\Parsing\V2\InferenceResponse;

public function handleResponse(InferenceResponse $response)
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
