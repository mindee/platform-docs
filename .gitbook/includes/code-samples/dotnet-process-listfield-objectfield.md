---
title: dotnet-process-listfield-objectfield
---

```csharp
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    InferenceFields fields = response.Inference.Result.Fields;

    ListField fieldObjectList = fields["my_simple_list_field"].ListField;

    List<ObjectField> objectItems = fieldObjectList.ObjectItems;

    // Loop over the list of Object fields
    foreach (ObjectField itemField in objectItems)
    {
        Dictionary<string, SimpleField> subFields = objectField.SimpleFields;
    
        // grab a single sub-field
        SimpleField subField1 = subFields["subfield_1"];
        
        // Choose the appropriate value type:
        // string, Double, Boolean
        string subFieldValue = subField1.Value;
    
        // loop over sub-fields
        // Note: in C#14, 'field' is a reserved keyword, hence use of 'entry'.
        foreach (KeyValuePair<string, SimpleField> entry in subFields)
        {
            string fieldName = entry.Key;
            SimpleField subField = entry.Value;
        }
    }
}
```
