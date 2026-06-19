---
title: code-sample-java-ocr
---

Requires Java ≥ 11. Java ≥ 17 is recommended.\
Requires the [Mindee Java SDK](https://central.sonatype.com/artifact/com.mindee.sdk/mindee-api-java) version **5.1.0** or greater.

{% code lineNumbers="true" %}
```java
import com.mindee.input.LocalInputSource;
import com.mindee.v2.MindeeClient;
import com.mindee.v2.product.ocr.OcrResponse;
import com.mindee.v2.product.ocr.params.OcrParameters;
import java.io.IOException;

public class SimpleMindeeClientV2 {

  public static void main(String[] args)
      throws IOException, InterruptedException
  {
    String apiKey = "MY_API_KEY";
    String filePath = "/path/to/the/file.ext";
    String modelId = "MY_MODEL_ID";

    // Init a new client
    var mindeeClient = new MindeeClient(apiKey);

    // Set Raw OCR parameters
    var modelParams = OcrParameters
        // ID of the model, required.
        .builder(modelId)
        .build();

    // Load a file from disk
    var inputSource = new LocalInputSource(filePath);

    // Send for processing using polling
    OcrResponse response = mindeeClient.enqueueAndGetResult(
        OcrResponse.class,
        inputSource,
        modelParams
    );

    // Print a summary of the response
    System.out.println(response.getInference().toString());

    // Access the result OCR pages
    var pages = response.getInference().getResult().getPages();
  }
}
```
{% endcode %}

Also take a look at the [OCR Result](https://docs.mindee.com/ocr-models/sdk-integration/ocr-result) documentation.
