---
title: code-sample-java-crop
---

Requires Java ≥ 11. Java ≥ 17 is recommended.\
Requires the [Mindee Java SDK](https://central.sonatype.com/artifact/com.mindee.sdk/mindee-api-java) version **5.0.0** or greater.

{% code lineNumbers="true" %}
```java
import com.mindee.input.LocalInputSource;
import com.mindee.v2.MindeeClient;
import com.mindee.v2.product.crop.CropResponse;
import com.mindee.v2.product.crop.params.CropParameters;
import java.io.IOException;

public class SimpleMindeeClientV2 {

  public static void main(String[] args)
      throws IOException, InterruptedException
  {
    String apiKey = "MY_API_KEY";
    String modelId = "MY_MODEL_ID";
    String filePath = "/path/to/the/file.ext";

    // Init a new client
    var mindeeClient = new MindeeClient(apiKey);

    // Set inference parameters
    var modelParams = CropParameters
        // ID of the model, required.
        .builder(modelId)
        .build();

    // Load a file from disk
    var inputSource = new LocalInputSource(filePath);

    // Send for processing using polling
    CropResponse response = mindeeClient.enqueueAndGetResult(
        CropResponse.class,
        inputSource,
        modelParams
    );

    // Print a summary of the response
    System.out.println(response.getInference().toString());

    // Access the crop results
    var crops = response.getInference().getResult().getCrops();
  }
}
```
{% endcode %}

Also take a look at the [Crop Result](https://docs.mindee.com/crop-models/sdk-integration/crop-result) documentation.
