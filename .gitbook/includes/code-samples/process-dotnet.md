Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

We need to specify that the field is a `SimpleField` in order to access its `Value`.

```csharp
var mySimpleField = response.Inference.Result.Fields["my_simple_field"];
var fieldValue = mySimpleField.SimpleField.Value;
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

We need to specify that the field is a `ListField` in order to access its `Items`.

```csharp
var myListField = response.Inference.Result.Fields["my_list_field"];

// access a value at a given position
var fieldFirstValue = myListField.ListField.Items[0].SimpleField.Value;

// loop over all values in the list
foreach (var listItem in myListField.ListField.Items)
{
    var itemValue = listItem.SimpleField.Value;
}
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```csharp
var objectField = response.Inference.Fields["my_object_field"];
var subField = objectField.ObjectField.Fields["sub_field"].Value;
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```csharp
objectListField = response.Inference.Fields["my_object_list_field"];

// access an object at a given position
$object_item_0 = $object_list_field.ListField.Items[0];
$sub_field_0_value = $object_item_0.ObjectField.Items["sub_field"].Value;

// loop over object lists
foreach ($object_list_field.ListField.Items as $object_item) {
    $sub_field_value = $object_item.ObjectField.Fields["sub_field"].Value;
}
```
