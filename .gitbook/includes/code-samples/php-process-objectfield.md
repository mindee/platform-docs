---
title: php-process-objectfield
---

```php
$inferenceFields = $response->inference->result->fields;
$objectField = $inferenceFields["my_object_field"];
$subFieldValue = $objectField["sub_field"]->value;
```
