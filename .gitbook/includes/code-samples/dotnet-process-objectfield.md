---
title: dotnet-process-objectfield
---

```csharp
using Mindee.V2.Parsing.Inference.Field;

public void HandleResponse(ExtractionResponse response)
{
    InferenceFields fields = response.Inference.Result.Fields;

    ObjectField objectField = fields["my_object_field"].ObjectField;

    Dictionary<string, SimpleField> subFields = objectField.SimpleFields;

    // grab a single sub-field
    SimpleField subField1 = subFields["subfield_1"];

    // loop over sub-fields
    // Note: in C#14, 'field' is a reserved keyword, hence use of 'entry'.
    foreach (KeyValuePair<string, SimpleField> entry in subFields)
    {
        string fieldName = entry.Key;
        SimpleField subField = entry.Value;
        
        // process the SimpleField ...
    }
}
```
