---
title: php-process-simplefield
---

```php
use Mindee\Parsing\V2\InferenceResponse;

public function handleResponse(InferenceResponse $response)
{
    $fields = $response->inference->result->fields;

    // texts, dates, classifications ...
    $stringFieldValue = $fields->getSimpleField('string_field')->value;

    // a JSON float will be a float
    $floatFieldValue = $fields->getSimpleField('float_field')->value;

    // even if the API always returns an integer, the type will be float
    $intFieldValue = $fields->getSimpleField('int_field')->value;

    // booleans
    $boolFieldValue = $fields->getSimpleField('bool_field')->value;
}
```
