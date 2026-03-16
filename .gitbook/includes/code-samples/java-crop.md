---
title: code-sample-java-crop
---

Requires Java ≥ 8. Java ≥ 11 recommended.\
Requires the [Mindee Java client library](https://central.sonatype.com/artifact/com.mindee.sdk/mindee-api-java) version **4.43.0** or greater.

```java
import com.mindee.MindeeClientV2;
import com.mindee.input.LocalInputSource;
import com.mindee.v2.product.crop.CropResponse;
import com.mindee.v2.product.crop.CropResult;
import com.mindee.v2.product.crop.params.CropParameters;
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
    CropParameters cropParams = CropParameters
        // ID of the model, required.
        .builder(modelId)
        .build();

    // Load a file from disk
    LocalInputSource inputSource = new LocalInputSource(filePath);

    // Send for processing using polling
    CropResponse response = mindeeClient.enqueueAndGetResult(
        CropResponse.class,
        inputSource,
        cropParams
    );

    // Print a summary of the response
    System.out.println(response.getInference().toString());

    // Access the crop results
    CropResult result = response.getInference().getResult();
  }
}
```

Also take a look at the [Processing Results](https://docs.mindee.com/integrations/client-libraries-sdk/quick-start#processing-the-results) documentation.
