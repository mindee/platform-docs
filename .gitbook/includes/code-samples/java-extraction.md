---
title: code-sample-java-extraction
---

Requires Java ≥ 8. Java ≥ 11 recommended.\
Requires the [Mindee Java client library](https://central.sonatype.com/artifact/com.mindee.sdk/mindee-api-java) version **4.43.0** or greater.

```java
import com.mindee.MindeeClientV2;
import com.mindee.InferenceParameters;
import com.mindee.input.LocalInputSource;
import com.mindee.parsing.v2.InferenceResponse;
import com.mindee.parsing.v2.field.InferenceFields;
import java.io.IOException;

public class SimpleMindeeClientV2 {

  public static void main(String[] args)
      throws IOException, InterruptedException
  {
    String apiKey = "MY_API_KEY";
    String filePath = "/path/to/the/file.ext";
    String modelId = "MY_MODEL_ID";

    // Init a new client
    MindeeClientV2 mindeeClient = new MindeeClientV2(apiKey);

    // Set inference parameters
    InferenceParameters extractionParams = InferenceParameters
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
    LocalInputSource inputSource = new LocalInputSource(filePath);

    // Send for processing using polling
    InferenceResponse response = mindeeClient.enqueueAndGetResult(
        InferenceResponse.class,
        inputSource,
        extractionParams
    );

    // Print a summary of the response
    System.out.println(response.getInference().toString());

    // Access the result fields
    InferenceFields fields = response.getInference().getResult().getFields();
  }
}
```

Also take a look at the [Processing Results](https://docs.mindee.com/integrations/client-libraries-sdk/quick-start#processing-the-results) documentation.
