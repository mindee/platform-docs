Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

```php
$my_simple_field = $response["inference"]["fields"]["my_simple_field"];
$field_value = $my_simple_field["value"];
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

```php
$my_list_field = $response["inference"]["fields"]["my_list_field"];

// access a value at a given position
$field_first_value = $my_list_field[0]["value"];

// loop over all values in the list
foreach ($my_list_field as $list_item) {
    $item_value = $list_item["value"];
}
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```php
$object_field = $response["inference"]["fields"]["my_object_field"];
$sub_field_value = $object_field["sub_field"]["value"];
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```php
$object_list_field = $response["inference"]["fields"]["my_object_list_field"];

// access an object at a given position
$object_item_0 = $object_list_field[0];
$sub_field_0_value = $object_item_0["sub_field"]["value"];

// loop over object lists
foreach ($object_list_field as $object_item) {
    $sub_field_value = $object_item["sub_field"]["value"];
}
```
