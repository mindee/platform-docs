---
title: dotnet-process-objectfield
---

```csharp
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    InferenceFields fields = response.Inference.Result.Fields;

    ObjectField objectField = fields["my_object_field"].ObjectField;

    Dictionary<string, SimpleField> subFields = objectField.SimpleFields;

    // grab a single sub-field
    SimpleField subField1 = subFields["subfield_1"];

    // loop over sub-fields
    foreach (KeyValuePair<string, SimpleField> entry in subFields)
    {
        string fieldName = entry.Key;
        SimpleField subField = entry.Value;
        
        // process the SimpleField ...
    }
}
```
