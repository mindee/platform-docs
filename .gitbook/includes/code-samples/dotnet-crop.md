---
title: code-sample-dotnet-crop
---

.NET ≥ 8.0 is recommended.\
Requires the [Mindee .NET SDK](https://www.nuget.org/packages/Mindee) version **4.3.0** or greater.

{% code lineNumbers="true" %}
```csharp
using Mindee;
using Mindee.Input;
using Mindee.V2;
using Mindee.V2.Product.Crop;
using Mindee.V2.Product.Crop.Params;

string filePath = "/path/to/the/file.ext";
string apiKey = "MY_API_KEY";
string modelId = "MY_MODEL_ID";

// Construct a new client
Client mindeeClient = new Client(apiKey);

// Set Crop parameters
var modelParams = new CropParameters(
    modelId: modelId
);

// Load a file from disk
var inputSource = new LocalInputSource(filePath);

// Upload the file
var response = await mindeeClient.EnqueueAndGetResultAsync<CropResponse>(
    inputSource, modelParams);

// Print a summary of the response
System.Console.WriteLine(response.Inference.ToString());

// Access the crop results
var crops = response.Inference.Result.Crops;
```
{% endcode %}

Also take a look at the [Crop Result](https://docs.mindee.com/crop-models/sdk-integration/crop-result) documentation.
