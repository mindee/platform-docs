---
title: code-sample-dotnet-webhook
---

Requires .NET ≥ 6.\
Requires the [Mindee .NET client library](https://www.nuget.org/packages/Mindee) version **3.34** or greater.

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

    // Add any number of webhook IDs here.
    , webhookIds: new List<string>{ "MY_WEBHOOK_ID" }

    // Options: set to `true` or `false` to override defaults

    // Enhance extraction accuracy with Retrieval-Augmented Generation.
    , rag: null
    // Extract the full text content from the document as strings.
    , rawText: null
    // Calculate bounding box polygons for all fields.
    , polygon: null
    // Boost the precision and accuracy of all extractions.
    // Calculate confidence scores for all fields.
    , confidence: null
);

// Load a file from disk
var inputSource = new LocalInputSource(filePath);

// Send for processing
var response = await mindeeClient.EnqueueInferenceAsync(
    inputSource, inferenceParams);

string jobId = response.Job.Id;

// Print the job ID
System.Console.WriteLine(jobId);

// IMPORTANT: save a record of which job ID corresponds to which file.
```
{% endcode %}
