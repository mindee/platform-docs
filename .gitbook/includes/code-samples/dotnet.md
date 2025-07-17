---
title: code-sample-dotnet
---

Requires .NET ≥ 6.\
Requires the [Mindee .NET client library](https://www.nuget.org/packages/Mindee/3.29.0-rc3) version **3.29-rc3** or greater.

{% code lineNumbers="true" %}
```csharp
using Mindee;
using Mindee.Input;

string filePath = "/path/to/the/file.ext";
string apiKey = "MY_API_KEY";
string modelId = "MY_MODEL_ID";

// Construct a new client
MindeeClientV2 mindeeClient = new MindeeClientV2(apiKey);

// Load an input source as a path string
var inputSource = new LocalInputSource(filePath);

// Call the product asynchronously with auto-polling
var response = await mindeeClient
    .EnqueueAndParseAsync(inputSource, new InferencePredictOptions(modelId));

// Print a summary of all the predictions
System.Console.WriteLine(response.Inference.ToString());
```
{% endcode %}
