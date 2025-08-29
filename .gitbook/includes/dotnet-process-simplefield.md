---
title: dotnet-process-simplefield
---

```csharp
using Mindee.Parsing.V2.Field;

public void HandleResponse(InferenceResponse response)
{
    // texts, dates, classifications ...
    string stringFieldValue = fields["string_field"].SimpleField.Value;

    // a JSON float will be a Double
    Double floatFieldValue = fields["float_field"].SimpleField.Value;

    // even if the API always returns an integer, the type will be Double
    Double intFieldValue = fields["int_field"].SimpleField.Value;

    // booleans
    Boolean boolFieldValue = fields["bool_field"].SimpleField.Value;
}
```
