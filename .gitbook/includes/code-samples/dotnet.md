---
title: code-sample-dotnet
---

Requires .NET ≥ 6.\
Requires the [Mindee .NET client library](https://www.nuget.org/packages/Mindee) version **3.34** or greater.

{% code lineNumbers="true" %}
```csharp
using Mindee;
using Mindee.Input;
using Mindee.Parsing.V2.Field;

string filePath = "/path/to/the/file.ext";
string apiKey = "MY_API_KEY";
string modelId = "MY_MODEL_ID";

// Construct a new client
MindeeClientV2 mindeeClient = new MindeeClientV2(apiKey);

// Set inference parameters
var inferenceParams = new InferenceParameters(
    // ID of the model, required.
    modelId: modelId

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

// Send for processing using polling
var response = await mindeeClient.EnqueueAndGetInferenceAsync(
    inputSource, inferenceParams);

// Print a summary of the response
System.Console.WriteLine(response.Inference.ToString());

// Access the result fields
InferenceFields fields = response.Inference.Result.Fields;
```
{% endcode %}

Also take a look at the [Processing Results](https://docs.mindee.com/integrations/client-libraries-sdk/quick-start#processing-the-results) documentation.
