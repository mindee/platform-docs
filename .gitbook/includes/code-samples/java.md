---
title: code-sample-java
---

Requires Java ≥ 8. Java ≥ 11 recommended.\
Requires the [Mindee Java client library](https://central.sonatype.com/artifact/com.mindee.sdk/mindee-api-java) version **4.33.0-rc2** or greater.

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
    InferenceParameters options = InferenceParameters.builder(modelId)
        // If set to `true`, will enable Retrieval-Augmented Generation.
        .rag(false)
        .build();

    // Load a file from disk
    LocalInputSource inputSource = new LocalInputSource(
        new File(filePath)
    );

    // Upload the file
    InferenceResponse response = mindeeClient.enqueueAndGetInference(
        inputSource,
        options
    );

    // Print a summary of the response
    System.out.println(response.getInference().toString());
  }
}
```
