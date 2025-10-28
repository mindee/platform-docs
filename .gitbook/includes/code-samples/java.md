---
title: code-sample-java
---

Requires Java ≥ 8. Java ≥ 11 recommended.\
Requires the [Mindee Java client library](https://central.sonatype.com/artifact/com.mindee.sdk/mindee-api-java) version **4.37.0** or greater.

```java
import com.mindee.MindeeClientV2;
import com.mindee.InferenceParameters;
import com.mindee.input.LocalInputSource;
import com.mindee.parsing.v2.InferenceResponse;
import java.io.File;
import java.io.IOException;

public class SimpleMindeeClient {

  public static void main(String[] args)
      throws IOException, InterruptedException
  {
    String filePath = "/path/to/the/file.ext";
    String apiKey = "MY_API_KEY";
    String modelId = "MY_MODEL_ID";

    // Init a new client
    MindeeClientV2 mindeeClient = new MindeeClientV2(apiKey);

    // Set inference parameters
    // Note: modelId is mandatory.
    InferenceParameters options = InferenceParameters
        // ID of the model, required.
        .builder(modelId)
        
        // Options: set to `true` or `false` to override defaults

        // Enhance extraction accuracy with Retrieval-Augmented Generation.
        .rag(null)
        // Extract the full text content from the document as strings.
        .rawText(null)
        // Calculate bounding box polygons for all fields.
        .polygon(null)
        // Boost the precision and accuracy of all extractions.
        // Calculate confidence scores for all fields.
        .confidence(null)
        
        .build();

    // Load a file from disk
    LocalInputSource inputSource = new LocalInputSource(
        new File(filePath)
    );

    // Send for processing using polling
    InferenceResponse response = mindeeClient.enqueueAndGetInference(
        inputSource,
        options
    );

    // Print a summary of the response
    System.out.println(response.getInference().toString());
  }
}
```
