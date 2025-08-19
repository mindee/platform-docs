---
title: code-sample-dotnet
---

Requires .NET ≥ 6.\
Requires the [Mindee .NET client library](https://www.nuget.org/packages/Mindee) version **3.30** or greater.

{% code lineNumbers="true" %}
```csharp
using Mindee;
using Mindee.Input;

string filePath = "/path/to/the/file.ext";
string apiKey = "MY_API_KEY";
string modelId = "MY_MODEL_ID";

// Construct a new client
MindeeClientV2 mindeeClient = new MindeeClientV2(apiKey);

// Set inference parameters
var inferenceParams = new InferenceParameters(
    modelId: modelId
    // If set to `true`, will enable Retrieval-Augmented Generation.
    , rag: false
);

// Load a file from disk
var inputSource = new LocalInputSource(filePath);

// Send for processing using polling
var response = await mindeeClient.EnqueueAndGetInferenceAsync(
    inputSource, inferenceParams);

// Print a summary of the response
System.Console.WriteLine(response.Inference.ToString());
```
{% endcode %}
