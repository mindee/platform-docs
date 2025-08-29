---
title: dotnet-process-listfield-simplefield
---

```csharp
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    InferenceFields fields = response.Inference.Result.Fields;

    ListField fieldSimpleList = fields["my_simple_list_field"].ListField;

    List<SimpleField> simpleItems = fieldSimpleList.SimpleItems;

    // Loop over the list of Simple fields
    foreach (SimpleField itemField in simpleItems)
    {
        // Choose the appropriate value type:
        // string, Double, Boolean
        string fieldValue = itemField.Value;
    }
}
```
