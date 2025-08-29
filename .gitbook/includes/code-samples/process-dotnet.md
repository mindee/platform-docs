---
title: process-dotnet
---

Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

We need to specify that the field is a `SimpleField` in order to access its value.

```csharp
using Mindee.Parsing.V2;
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    InferenceFields fields = response.inference.Result.Fields;

    var mySimpleField = fields["my_simple_field"].SimpleField;
    var fieldValue = mySimpleField.Value;
}
```

Accessing a list of simple values, where `my_list_field` is the name of the field in the Model.

We need to specify that the field is a `ListField` in order to access its `SimpleItems`.

```csharp
using Mindee.Parsing.V2;
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{    
    InferenceFields fields = response.inference.Result.Fields;

    var myListField = fields["my_list_field"].ListField;

    // access a value at a given position
    var fieldFirstValue = myListField.SimpleItems[0].Value;

    // loop over all values in the list
    foreach (var listItem in myListField.SimpleItems)
    {
        var itemValue = listItem.Value;
    }
}
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```csharp
using Mindee.Parsing.V2;
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    InferenceFields fields = response.inference.Result.Fields;

    var objectField = fields["my_object_field"].ObjectField;

    SimpleField subField = objectField.SimpleFields["sub_field"];
    var subFieldValue = subField.Value;
}
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```csharp
using Mindee.Parsing.V2;
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    InferenceFields fields = response.inference.Result.Fields;
    
    objectListField = fields["my_object_list_field"].ListField;

    // access an object at a given position
    var objectItem0 = objectListField.ObjectItems[0];
    var subField0Value = objectItem0.SimpleFields["sub_field"].Value;

    // loop over object lists
    foreach (var objectItem in objectListField.ObjectItems) {
        SimpleField subField = objectItem.SimpleFields["sub_field"];
        var subFieldValue = subField.SimpleField.Value;
    }
}
```
