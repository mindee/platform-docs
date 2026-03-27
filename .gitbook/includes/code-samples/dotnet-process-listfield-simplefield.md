---
title: dotnet-process-listfield-simplefield
---

```csharp
using Mindee.V2.Parsing.Inference.Field;

public void HandleResponse(ExtractionResponse response)
{
    InferenceFields fields = response.Inference.Result.Fields;

    ListField simpleListField = fields["my_simple_list_field"].ListField;

    List<SimpleField> simpleItems = simpleListField.SimpleItems;

    // Loop over the list of Simple fields
    foreach (SimpleField itemField in simpleItems)
    {
        // Choose the appropriate value type:
        // string, Double, Boolean
        string fieldValue = itemField.Value;
    }
}
```
